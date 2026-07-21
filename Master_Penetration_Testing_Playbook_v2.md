# The Master Penetration Testing Playbook

### A Modular SOP for Authorized Security Assessments and Bug Bounty Engagements

> **Scope note:** This handbook is a methodology and decision-tree
> reference --- it governs *process*, *what to look for*, *how to
> validate safely*, and *how to document*. It intentionally does not
> include ready-to-fire payload strings, exploit code, or destructive
> commands. Pair it with your engagement's Rules of Engagement (RoE),
> scope document, and legal authorization. Nothing here should be run
> against a target without written authorization.

------------------------------------------------------------------------

## How to use this document

Each phase below follows the same reasoning template:

-   **Why this phase exists** --- the purpose in the overall kill chain
-   **What we're trying to discover**
-   **Order of operations**
-   **Decision tree** --- "If X → go here. If not → continue here."
-   **Common mistakes**
-   **Validation steps**
-   **Evidence & documentation requirements**

Cross-references use `→ PART.section` notation (e.g. `→ P3.SQLi`).

------------------------------------------------------------------------

# PART 1 --- MASTER RECON WORKFLOW

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

### 1.0 Why recon exists

Every downstream vulnerability class (`→ PART 3`) requires an accurate
map of what exists before it can be tested. Under-recon is the single
largest cause of missed findings in professional engagements --- not
lack of exploit skill. Recon is not "step one and done"; it is a
continuous background process that reactivates every time a new asset,
subdomain, endpoint, or technology is discovered mid-engagement.

### 1.1 Passive vs Active Recon

  -----------------------------------------------------------------------
                          Passive                 Active
  ----------------------- ----------------------- -----------------------
  Definition              No direct traffic to    Direct interaction with
                          target infra            target infra

  Risk of detection       \~None                  Detectable, may trip
                                                  WAF/IDS

  When to run             Always first            After scope + RoE
                                                  reviewed for
                                                  intrusiveness limits

  Examples                WHOIS, cert             Port scans, directory
                          transparency, search    brute force, vuln
                          engine dorking, GitHub  scanners
                          search, archived pages  
  -----------------------------------------------------------------------

**Decision:** Start 100% passive. Only move to active once (a) scope is
written and signed, (b) rate limits / blackout windows are known, (c) a
point of contact exists for incident response false alarms.

### 1.2 Ownership & Infrastructure Mapping

**Steps, in order:** 1. WHOIS on root domain(s) → registrant org,
registrar, nameservers, creation/expiry dates. 2. Reverse WHOIS on
registrant org/email → find sibling domains (common in enterprises with
many brands). 3. ASN lookup on known IPs → find the org's full IP
allocation (BGP/ASN tools, RDAP). 4. Expand ASN → CIDR ranges →
cross-reference against scope (many ranges will be cloud-shared and *out
of scope* --- flag and exclude). 5. DNS enumeration: NS, MX, TXT
(SPF/DMARC/DKIM reveal mail infra and sometimes internal hostnames),
CNAME chains (reveal SaaS dependencies --- Zendesk, Shopify, etc.).

**What finding a large ASN allocation implies:** organization likely
self-hosts significant infrastructure → prioritize network-level
testing. What finding *no* dedicated ASN implies: fully
cloud/SaaS-hosted → shift focus to cloud misconfig (`→ P4.Cloud`) and
web-app layer testing.

**If this succeeds (own IP ranges found)** → cross-check each range
against signed scope before touching anything →
`1.6 Port/Service Scanning`. **If this fails (no dedicated infra)** →
proceed directly to subdomain enumeration against the web layer.

**Common mistakes:** scanning IPs that resolve to shared cloud/CDN
ranges without confirming ownership (this is how testers accidentally
hit *other customers'* infrastructure --- a serious authorization
violation). Always confirm an IP is dedicated to the target before
active testing.

**Evidence to capture:** WHOIS raw output, ASN/CIDR tables, timestamped
screenshots, tool + query used.

### 1.3 Subdomain Enumeration

**Why:** Subdomains are the #1 source of forgotten, unpatched, or "we
didn't think this counted" assets --- dev, staging, and internal panels
routinely leak here.

**Order of operations:** 1. Certificate Transparency logs (crt.sh and
equivalents) --- passive, comprehensive, catches even subdomains that
were only briefly live. 2. Passive aggregation from multiple public
sources (search engines, DNS aggregators, threat-intel platforms). 3.
GitHub / GitLab / public code search for hardcoded hostnames referencing
the root domain. 4. Permutation/mutation wordlist generation from
discovered names (e.g. `dev-`, `-staging`, `internal-`) fed into active
DNS brute force. 5. Active DNS brute force against a curated wordlist
(only after passive sources exhausted). 6. Zone transfer attempt (AXFR)
--- almost always fails on modern DNS, but free to try and occasionally
still open on internal/forgotten nameservers.

**Decision tree:**

    Subdomain found
     ├─ Resolves to CDN/WAF IP? ──yes──> fingerprint origin separately (→1.4), treat behind-CDN testing carefully
     ├─ Resolves to cloud IP owned by 3rd party (not target)? ──yes──> flag, do NOT test, note as informational only
     ├─ New naming pattern discovered (e.g. "uat-")? ──yes──> feed back into permutation wordlist, re-run brute force
     └─ Live HTTP(S) service? ──yes──> add to full target inventory → 1.9 Technology Fingerprinting

**Common mistakes:** treating a single enumeration pass as complete ---
new subdomains appear throughout an engagement (CI/CD frequently spins
up ephemeral `pr-1234.dev.target.com`-style hosts). Re-run cert
transparency queries periodically during a multi-week engagement.

**Validation:** confirm each candidate subdomain actually resolves and
is in-scope before adding to the active target list; stale DNS records
pointing to decommissioned/third-party infrastructure are common and out
of scope by default unless explicitly included.

**Evidence:** full subdomain list with resolution status, source of
discovery, in-scope/out-of-scope determination and justification.

### 1.4 Technology Fingerprinting (CDN, WAF, Load Balancer, Cloud Provider)

**What we're looking for:** HTTP response headers, TLS certificate
SANs/issuer, favicon hashes, JS library signatures, error page
fingerprints, timing/behavior differences that reveal CDN
(Cloudflare/Akamai/Fastly), WAF presence, load balancer type, and
hosting cloud (AWS/Azure/GCP/other).

**Why it matters:** determines (a) whether you're testing the real
origin or an edge cache, (b) whether WAF-evasion technique selection
matters for later testing, (c) which `→ PART 4` technology playbook
applies.

**Decision tree:**

    CDN/WAF detected?
     ├─ Yes → attempt origin IP discovery (historical DNS, cert transparency for direct-IP certs,
     │         SPF records leaking mail server IPs, subdomain takeover artifacts, exposed origin
     │         headers) → if origin found, confirm in-scope before testing origin directly
     └─ No  → traffic goes straight to origin; standard testing applies

**Common mistake:** assuming a WAF means the app is safe, and testing
less thoroughly. WAF presence changes *technique*, not *thoroughness*.

**Evidence:** header dumps, cert details, identified CDN/cloud vendor
with confidence level (confirmed vs inferred).

### 1.5 Email Discovery, Employee Enumeration, Metadata

**What we're looking for:** email address naming convention, employee
names/roles (useful for social-engineering-adjacent findings like
password spraying username lists --- *only if phishing/social
engineering is explicitly in scope*), document metadata (author names,
software versions, internal file paths) from publicly posted PDFs/Office
docs.

**Decision:** if credential-based testing (password spray, credential
stuffing validation) is in scope, this phase produces the username list.
If not in scope, document as informational only.

**Evidence:** naming convention pattern, sample redacted findings,
source URLs.

### 1.6 Open Ports & Network Services

**Order of operations:** 1. Fast wide scan across all in-scope IPs (top
ports) to establish live-host inventory. 2. Full-range scan on confirmed
live hosts. 3. Service/version detection on open ports. 4.
Cross-reference service versions against known-vulnerable version ranges
(informational at this stage --- confirmation happens in `→ PART 3/4`).

**Decision tree:**

    Port open?
     ├─ Known admin/management service (RDP, WinRM, DB ports, K8s API, Docker API)? → flag HIGH PRIORITY,
     │    do not brute-force without explicit RoE approval for credential attacks; note exposure itself
     │    as a finding (unnecessary exposure to internet)
     ├─ HTTP/HTTPS? → hand off to web app workflow (→ PART 2)
     └─ Unrecognized/custom protocol? → manual banner grab, document, research protocol before further action

**Common mistakes:** running aggressive scans without confirming
scanning is permitted during the engagement window (some clients
restrict scan timing to avoid alerting SOC or triggering auto-block of
testing IPs); scanning through a WAF/CDN IP instead of true origin,
producing meaningless results.

**Evidence:** full port/service table per host, scan timestamps, tool +
flags used (needed for reproducibility and for the client's SOC to
correlate with their own alerts).

### 1.7 Historical & Archived Data

**What we're looking for:** old versions of pages (may expose
since-removed but still-functional endpoints), historical JS bundles
(often less obfuscated, may contain old API keys), deprecated API
versions still live on the backend.

**Order:** Wayback Machine / archive services → diff historical vs
current JS and HTML → extract endpoints/parameters no longer linked from
current UI but potentially still live.

**If this succeeds (deprecated endpoint still responds)** → test as a
normal endpoint but flag "unmaintained/deprecated" in the report ---
these frequently lack current security controls.

### 1.8 JavaScript, API, and Endpoint Discovery

**Order of operations:** 1. Crawl/spider the application to build a full
sitemap of linked pages. 2. Download all JS bundles (including source
maps if exposed --- a source map exposure is itself a finding). 3.
Static-analyze JS for: hardcoded endpoints, hardcoded API keys/secrets,
comments revealing internal logic, feature flags. 4. Check for API
documentation artifacts: `robots.txt`, `sitemap.xml`, `/swagger.json`,
`/openapi.json`, `/graphql` (introspection), `/.well-known/`. 5.
Directory/file brute force using a curated, technology-informed wordlist
(informed by `→ 1.9` fingerprinting --- don't run a generic PHP wordlist
against a confirmed Node.js app). 6. Parameter discovery (mining JS,
crawled forms, and historical data for parameter names) to feed into
`→ PART 3` testing.

**Decision tree:**

    Source map exposed? ──yes──> extract full original source → re-run secrets/endpoint analysis on
                                  unminified code → document as Information Disclosure finding
    Swagger/OpenAPI found? ──yes──> enumerate every documented endpoint/method → cross-check against
                                  what's actually reachable (auth bypass candidates if "internal" endpoints
                                  are reachable externally) → PART 5 "Found Swagger"
    GraphQL endpoint found? ──yes──> attempt introspection query → if enabled, full schema dump →
                                  PART 3.GraphQL
    Exposed .git/.svn directory? ──yes──> attempt history reconstruction → search commit history for
                                  secrets → PART 5 "Found exposed Git"

**Common mistakes:** running directory brute force before technology
fingerprinting (wastes time/noise on irrelevant wordlists); not diffing
JS bundles over time during longer engagements (deploys change
endpoints); ignoring 3xx/401/403 responses during brute force --- those
are often more interesting than 200s (they confirm existence while
hiding content, worth targeted follow-up).

**Evidence:** full endpoint/parameter inventory, extracted secrets
(redacted in report body, full value in secure evidence appendix per
client handling requirements), source map/git history artifacts.

### 1.9 Cloud Storage & Secrets Exposure (recon-level)

**What we're looking for:** publicly listable object storage buckets,
exposed CI/CD dashboards, exposed `.env`/config files, hardcoded
credentials in JS/git history.

**Decision tree:**

    Storage bucket found?
     ├─ Publicly listable? → document contents categories (do not exfiltrate sensitive data beyond
     │    what's needed to prove the finding) → PART 5 "Found S3 bucket"
     └─ Not listable but object URLs guessable/enumerable? → test individual object access → same handling

**Critical evidence handling rule:** when recon surfaces live secrets
(API keys, credentials), capture only enough evidence to prove the
finding (e.g., first/last 4 characters, a redacted screenshot, or a
successful-but-non-destructive validation), never the full plaintext
secret pasted into a shareable report. Report to client through the
agreed emergency-disclosure channel immediately if the secret grants
production access --- don't wait for the final report.

------------------------------------------------------------------------

*(Part 1 continues to feed every subsequent part --- recon findings
determine which `PART 2` application-type workflow and which `PART 4`
technology playbook activate.)*

------------------------------------------------------------------------

# PART 2 --- WORKFLOW BY APPLICATION TYPE

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

Each entry below follows: **Attack surface → Typical mistakes → Typical
vulnerabilities → Recon → Enumeration → Testing → Validation →
Escalation → Evidence.**

## 2.1 Traditional Server-Rendered Websites

-   **Attack surface:** forms, file uploads, query parameters, session
    cookies, server-side templating.
-   **Typical mistakes:** unsanitized input reflected into HTML/SQL/OS
    commands; weak session management; verbose error pages.
-   **Typical vulns:** `→ P3.SQLi`, `→ P3.XSS`, `→ P3.CSRF`,
    `→ P3.FileUpload`, `→ P3.IDOR`.
-   **Recon:** full crawl, form inventory, cookie/session flag audit.
-   **Enumeration:** every input field mapped to expected type/behavior;
    identify server tech via `→ 1.4`.
-   **Testing:** systematic input-boundary testing per vuln class, one
    variable at a time.
-   **Validation:** reproduce with minimal payload, confirm via
    out-of-band or observable side effect, never rely on a single
    anomalous response.
-   **Escalation:** chain low findings (e.g., verbose error + open
    redirect) into higher-impact reportable chains.
-   **Evidence:** request/response pairs for every confirmed finding.

## 2.2 REST APIs

-   **Attack surface:** every documented and undocumented endpoint ×
    every HTTP method.
-   **Typical mistakes:** authorization checked only on "primary"
    endpoints, missing on bulk/export/admin variants; inconsistent
    object-level authorization.
-   **Typical vulns:** `→ P3.BOLA/IDOR`, `→ P3.MassAssignment`,
    `→ P3.BrokenAuth`, `→ P3.RateLimiting`.
-   **Recon:** Swagger/OpenAPI (`→ 1.8`), JS-mined endpoints, method
    fuzzing (does `GET`-only endpoint also accept `PUT`/`DELETE`?).
-   **Testing:** for every endpoint, test with (a) no auth, (b) low-priv
    auth, (c) another user's valid token/ID substituted (BOLA test) ---
    this last one is the highest-value single test in API assessments.
-   **Escalation:** horizontal → vertical privilege escalation chains.

## 2.3 GraphQL APIs

-   **Attack surface:** single endpoint, but arbitrarily nested
    query/mutation surface.
-   **Recon:** introspection query if enabled; if disabled, attempt
    schema reconstruction via error-message field-suggestion leakage.
-   **Testing:** authorization per-field (not just per-query --- a query
    might be authorized but expose an unauthorized nested field);
    batching/aliasing abuse for rate-limit bypass; deeply nested query
    for DoS-adjacent resource exhaustion (validate non-destructively,
    small scale only).
-   **→ P3.GraphQL** for full vulnerability-specific detail.

## 2.4 Single Page Applications (SPA)

-   **Attack surface:** client-side routing/auth gating (often
    bypassable --- the API is the real boundary, not the JS router),
    DOM-based issues, client-stored tokens.
-   **Typical mistakes:** "security" enforced only in JS (hide button ≠
    authorize action), tokens in localStorage (XSS-exfiltratable) vs
    httpOnly cookies.
-   **Testing:** always test the underlying API directly, ignoring
    client-side gating entirely; audit token storage location and
    exposure.

## 2.5 Mobile Backend APIs

-   Treat as `→ 2.2 REST/GraphQL` testing against the backend once the
    mobile app's API traffic is intercepted (proxy-based traffic capture
    --- mobile app itself is a separate testing surface not covered here
    as it's typically a distinct engagement type).

## 2.6 Admin Panels

-   **Attack surface:** authentication, often weaker hardening than
    customer-facing surfaces (assumption of "no one will find it").
-   **Testing:** default credential check (if explicitly authorized),
    auth bypass via direct object/path access, IDOR between admin-scoped
    resources, and `→ 2.9 Auth workflow` in full.
-   **Decision:** finding an admin panel →
    `→ PART 5 "Found admin panel"`.

## 2.7 Authentication Services / SSO / OAuth

-   **Attack surface:** token issuance, redirect_uri validation, state
    parameter, session fixation, MFA bypass paths.
-   **→ P3.OAuth, P3.JWT, P3.BrokenAuth, P3.SessionIssues** for full
    technical workflows.

## 2.8 CMS Platforms (WordPress, Drupal, Joomla)

-   **Recon:** version fingerprinting via meta generator tags/static
    asset paths, enumerate installed plugins/themes/modules (each is an
    independent attack surface with its own CVE history).
-   **Testing:** cross-reference detected plugin/theme versions against
    known-vulnerable ranges; test default/exposed admin login paths;
    check for exposed config/backup files typical to the CMS (e.g.,
    `wp-config.php.bak`-style patterns).
-   **Escalation:** plugin vuln → often direct RCE or file upload;
    document CVE reference if applicable.

## 2.9 Framework-Specific Apps (Next.js/React/Vue/Angular, Laravel/Django/Rails/Spring/ASP.NET/Node/Go/Rust)

-   **Approach:** identify framework via `→ 1.4/1.8` fingerprinting,
    then apply the matching `→ PART 4` technology playbook for
    framework-specific default files, debug endpoints, and known
    misconfiguration patterns.

## 2.10 Microservices / Cloud-Native / Serverless

-   **Attack surface:** service-to-service auth (often weaker than
    user-facing auth), internal API exposure via misrouted gateway
    rules, function-level permission over-scoping.
-   **Testing:** gateway route enumeration to find internal-only
    services reachable externally; per-function IAM/permission review
    where accessible; cold-start/timeout behavior differences that leak
    implementation details.

## 2.11 CI/CD, Git Services, Docker Registries, Kubernetes Dashboards, Monitoring Dashboards

-   **Attack surface:** these are almost always intended to be
    internal-only; external exposure of any of these is itself typically
    the finding.
-   **Testing:** confirm exposure, confirm whether authentication is
    present/bypassable, do **not** trigger builds/deployments or pull
    private images unless explicitly authorized (these actions have real
    production impact).
-   **→ PART 5**: "Found Jenkins", "Found Docker API", "Found
    Kubernetes" decision trees.

------------------------------------------------------------------------

# PART 3 --- WORKFLOW BY VULNERABILITY CLASS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

Format per vulnerability: **Indicators → Prerequisites → Safe validation
→ Confirmation → Impact → False positives/negatives → Pivot
opportunities → Documentation checklist.**

> Note on scope: this section describes *testing methodology and
> indicators*, not payload libraries. Actual test strings should come
> from your team's internal, access-controlled testing toolkit and be
> selected/reviewed per-engagement --- that detail is deliberately kept
> out of a document like this.

## 3.1 SQL Injection

-   **Indicators:** input reflected into DB-backed logic (search,
    filter, sort, login), error messages revealing DB type, timing
    differences on boolean-varied input.
-   **Safe validation:** boolean-based differential testing (compare
    response for TRUE vs FALSE condition) before any data-extraction
    attempt; time-based only as a fallback and only with minimal,
    single-request delay windows to avoid DoS-like load.
-   **Confirmation:** reproduce difference deterministically at least
    twice; never extract more data than needed to prove impact (e.g., DB
    version string is sufficient --- do not dump user tables).
-   **False positives:** WAF-normalized error pages, generic 500s
    unrelated to injection.
-   **Pivot:** confirmed SQLi → check for stacked queries, OS command
    execution via DB features, file read/write DB functions.

## 3.2 NoSQL Injection

-   **Indicators:** JSON-body inputs into MongoDB-style backends;
    operator injection (`$ne`, `$gt` style) via unexpected object
    structure instead of string.
-   **Validation:** submit structured (non-string) input where a string
    is expected and observe logic-bypass behavior (e.g., auth check
    bypassed).

## 3.3 Command Injection

-   **Indicators:** functionality that clearly shells out (file
    conversion, ping/diagnostic tools, image processing).
-   **Safe validation:** non-destructive, observable side-effect only
    (timing delay or DNS/HTTP out-of-band callback), never destructive
    commands.
-   **Escalation:** confirmed injection → determine execution
    context/privileges → do not pivot further without explicit
    authorization for post-exploitation.

## 3.4 SSRF

-   **Indicators:** any server-side "fetch a URL" feature (webhooks, PDF
    generators, image-from-URL, link previews).
-   **Validation:** redirect to a controlled listener you own, confirm
    the callback, and test cloud metadata endpoint reachability *only if
    in scope and only checking reachability, not exfiltrating
    credentials* --- many client RoEs explicitly forbid
    metadata-endpoint credential retrieval even when SSRF is confirmed;
    check first.

## 3.5 XSS (Reflected/Stored/DOM)

-   **Indicators:** unsanitized input reflected in HTML context,
    missing/weak CSP.
-   **Validation:** minimal proof-of-concept (e.g., benign alert or
    attribute injection) --- never a payload designed for real
    exploitation against real users, and never test stored XSS on
    shared/production data without an isolated test account.

## 3.6 IDOR / BOLA / Broken Access Control

-   **Indicators:** sequential or guessable object identifiers, object
    access not re-checked against session owner.
-   **Validation:** the two-account test --- create two low-privilege
    test accounts, attempt to access Account B's resources using Account
    A's session. This is the gold-standard confirmation.
-   **Impact:** typically high --- direct data exposure across users.

## 3.7 Broken Authentication / Session Issues / JWT / OAuth

-   **JWT checks:** algorithm confusion (alg=none acceptance),
    weak/guessable signing secret, missing expiration enforcement,
    missing audience/issuer validation.
-   **OAuth checks:** redirect_uri validation strictness, state
    parameter presence/entropy, token leakage via referrer headers.
-   **Session checks:** session fixation, missing invalidation on
    logout/password change, predictable session tokens.

## 3.8 File Upload / LFI / RFI / Path Traversal

-   **Indicators:** upload functionality, file-serving endpoints with
    path-like parameters.
-   **Validation:** confirm traversal with a read of a known-benign,
    non-sensitive file first (proves the primitive) before considering
    any further step, and only within authorized scope.

## 3.9 SSTI / Deserialization / Prototype Pollution

-   **Indicators:** user input reflected into template rendering;
    object/array merge functions accepting user-controlled keys.
-   **Validation:** minimal expression evaluation proof, not full RCE
    chain, unless explicitly authorized to demonstrate impact.

## 3.10 CORS / Clickjacking / CRLF / Request Smuggling / Cache Poisoning/Deception

-   **Indicators:** overly permissive `Access-Control-Allow-Origin`
    reflecting arbitrary origins with credentials allowed; missing
    `X-Frame-Options`/frame-ancestors; response splitting via header
    injection; front-end/back-end parsing discrepancies.
-   **Validation:** each has a specific, low-risk differential test
    (e.g., CORS: send an arbitrary `Origin` header and check if it's
    reflected + credentials allowed) --- confirm via observation, not
    exploitation against real user sessions.

## 3.11 Business Logic & Race Conditions

-   **Indicators:** multi-step flows with time-of-check/time-of-use gaps
    (e.g., coupon redemption, balance checks, limited-quantity actions).
-   **Validation:** controlled concurrent-request testing against your
    own test account/data only, at the smallest scale that proves the
    race condition --- never at a scale that could degrade production
    service.

## 3.12 Rate Limiting & DoS Considerations

-   **Approach:** validate absence/weakness of rate limiting via a
    small, bounded burst --- enough to prove no throttling occurs, then
    stop. Full-scale DoS testing is out of scope for standard pentests
    unless explicitly authorized as a separate, scheduled activity with
    client infra team awareness.

## 3.13 Misconfiguration / Information Disclosure / Secrets / Cloud & Storage Misconfig / CI/CD Exposure

-   Covered in depth via `→ 1.9` and `→ 2.11`; testing here is primarily
    about confirming exposure and access level, not exploitation.

**Documentation checklist (applies to every vulnerability class):** - \[
\] Affected URL/endpoint/parameter - \[ \] HTTP request/response
evidence (redacted of any real user data) - \[ \] Steps to reproduce,
numbered, minimal - \[ \] Tool/technique used - \[ \] Impact statement
in business terms - \[ \] CVSS vector and score (or client's chosen
scoring system) - \[ \] Remediation recommendation - \[ \] False
positive risk assessment

------------------------------------------------------------------------

# PART 4 --- WORKFLOW BY TECHNOLOGY

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

For each: **common weaknesses, default files/paths to check for
exposure, fingerprinting signals, typical findings.** (Testing
methodology inherits from the matching `→ PART 2/3` workflow --- this
section is about what's *specific* to the technology.)

  ------------------------------------------------------------------------------------------
  Technology                 Fingerprint via      Default/interesting    Typical findings
                                                  paths to check         
  -------------------------- -------------------- ---------------------- -------------------
  Apache                     `Server` header,     `/server-status`,      Directory listing,
                             default error pages  `/.htaccess` exposure  verbose errors

  Nginx                      `Server` header,     misconfigured          Path traversal via
                             error page style     `alias`/traversal via  config errors
                                                  location blocks        

  IIS                        `Server` header,     `/web.config`          Info disclosure,
                             `X-Powered-By`       exposure, verbose ASP  outdated module
                                                  errors                 versions

  Tomcat                     Error page           `/manager/html`,       Default creds → WAR
                             signature, default   `/host-manager`        deploy RCE (only
                             port                                        with explicit auth)

  Express/Node               Header signatures,   debug mode exposing    Info disclosure,
                             stack traces in      stack traces           prototype pollution
                             errors                                      surface

  Laravel                    `.env` exposure      `/.env`, `/telescope`, Secret exposure,
                             patterns, debug      debug mode `APP_DEBUG` full stack trace
                             error pages          errors                 disclosure

  Django                     Debug error page     `/admin`, DEBUG=True   Info disclosure,
                             signature            stack traces           admin panel
                                                                         exposure

  Spring                     Actuator signature   `/actuator/env`,       Massive info
                                                  `/actuator/health`,    disclosure via
                                                  `/actuator/heapdump`   actuator misconfig

  ASP.NET                    `X-AspNet-Version`   `/trace.axd`, custom   Detailed stack
                             header               errors off             traces, version
                                                                         disclosure

  Kubernetes                 API server banner    exposed API server,    Cluster-wide
                                                  dashboard, kubelet API compromise
                                                                         potential if
                                                                         unauthenticated

  Docker                     Docker API banner on exposed daemon socket  Full host
                             default port         over HTTP              compromise
                                                                         potential if
                                                                         unauthenticated

  Cloudflare/Akamai/Fastly   Header signatures,   origin IP leakage      Origin bypass of
  (CDN)                      IP ranges            vectors (`→ 1.4`)      edge protections

  AWS/Azure/GCP              Metadata endpoint    misconfigured IAM      Cloud misconfig,
                             response, resource   roles, public storage, over-permissioned
                             naming conventions   exposed metadata via   roles
                                                  SSRF                   

  Firebase/Supabase          SDK config exposure  open Firestore/RLS     Full data exposure
                             in JS                rules, public DB rules via client-side
                                                                         accessible DB

  Vercel/Netlify/GitHub      Header signatures,   exposed preview        Staging data/secret
  Pages                      deploy preview URL   deployments (often     exposure
                             patterns             unauthenticated        
                                                  staging copies)        

  S3/CloudFront              Bucket naming        public bucket listing, Data exposure,
                             convention, CDN      misconfigured bucket   object takeover
                             header signature     policy                 
  ------------------------------------------------------------------------------------------

------------------------------------------------------------------------

# PART 5 --- DECISION TREES (Quick Reference)

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

    Found admin panel
     ├─ Auth required? ──yes──> test for default/weak creds (if authorized), test auth bypass paths,
     │                           test IDOR between admin resources (→ P3.IDOR)
     └─ No auth? ──> CRITICAL finding, document immediately, notify client per emergency-disclosure terms

    Found login form
     ├─ → test broken auth workflow (→ P3.BrokenAuth) → then business logic around password reset,
     │     account lockout, MFA bypass paths

    Found API (REST)
     ├─ Documented (Swagger/OpenAPI)? ──yes──> enumerate every method on every endpoint,
     │                                          test each with wrong-user token (→ P3.BOLA)
     └─ Undocumented? ──> mine from JS (→1.8), same testing applies

    Found GraphQL endpoint
     ├─ Introspection enabled? ──yes──> full schema dump → enumerate every mutation for auth gaps
     └─ Disabled? ──> attempt error-based schema reconstruction, test known/guessed field names

    Found file upload
     ├─ → test file type validation bypass, content-type spoofing, path traversal in filename,
           stored XSS via SVG/HTML upload, then check where/how the file is served back

    Found JWT
     ├─ → check alg field manipulation, signature verification enforcement, expiration handling,
           claims tampering resistance (→ P3.JWT)

    Found S3/object storage bucket
     ├─ Publicly listable? ──yes──> enumerate contents categories, document exposure scope
     └─ Not listable? ──> test individual object URL guessing/enumeration

    Found Swagger/OpenAPI doc
     ├─ → cross-reference every documented endpoint against actual external reachability
           (internal-only endpoints reachable externally = access control finding)

    Found exposed .git directory
     ├─ → attempt to reconstruct history, search commits for secrets/credentials,
           document as info disclosure + potential secondary findings from leaked secrets

    Found Kubernetes API/dashboard exposed
     ├─ Authenticated? ──no──> CRITICAL, notify client immediately, document cluster access scope
     └─ Authenticated? ──yes──> test for weak/default credentials only if explicitly authorized

    Found Jenkins/CI-CD panel
     ├─ Auth required? ──no──> CRITICAL — potential build/deploy pipeline compromise, notify immediately
     └─ Auth required? ──yes──> document exposure, do not attempt to trigger jobs without authorization

    Found Docker API exposed
     ├─ → confirm unauthenticated access, document as CRITICAL (host compromise potential),
           do not create/run containers without explicit authorization

------------------------------------------------------------------------

# PART 6 --- REPORTING

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

### 6.1 Evidence checklist (per finding)

-   [ ] Unique finding ID
-   [ ] Title (concise, describes the vulnerability class + affected
    component)
-   [ ] Affected asset(s) --- full URL/host/endpoint
-   [ ] Severity + CVSS vector/score
-   [ ] Description (technical)
-   [ ] Business impact narrative (non-technical, for leadership
    audience)
-   [ ] Step-by-step reproduction
-   [ ] Evidence (request/response, screenshots --- redacted of real
    user PII)
-   [ ] Remediation guidance (specific, actionable, prioritized)
-   [ ] Verification/retest notes (status: open/fixed/accepted risk)
-   [ ] References (CWE, OWASP category, CVE if applicable)

### 6.2 Severity analysis approach

Base severity on CVSS (or client-preferred framework) but always
sanity-check against real business context --- a "Medium" CVSS finding
on an internet-facing admin panel with no MFA may warrant a higher
effective priority in the executive summary than its raw score suggests,
and vice versa for a technically "High" finding requiring an implausible
attack chain.

### 6.3 Report structure

1.  Executive summary (non-technical, business risk framing)
2.  Scope & methodology summary (references `→ PART 1-5` methodology
    used)
3.  Findings summary table (sortable by severity)
4.  Detailed findings (one per the checklist above)
5.  Appendices (raw tool output, full recon inventory, out-of-scope
    items noted for awareness)

------------------------------------------------------------------------

# PART 7 --- DELIVERABLE FORMAT NOTES

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

This document itself follows the requested structure: Markdown, nested
bullets, ASCII decision trees, tables, and cross-references
(`→ PART.section`) between phases. Use it as a living document ---
update `PART 1` recon inventories continuously, and treat `PART 5` as
your fast-lookup index during active testing when a new asset type is
discovered mid-engagement.

------------------------------------------------------------------------

## Closing notes

-   This playbook assumes a signed authorization/scope document and
    defined RoE exist before any active step. Passive recon (`→1.1`) is
    the only phase that should ever begin before that paperwork is
    finalized.
-   Deliberately excluded: ready-to-use payload strings, exploit code,
    and destructive/DoS-scale test procedures. Those belong in your
    team's internal, access-controlled toolkit and should be selected
    per finding, per engagement, under the specific RoE --- not baked
    into a general-purpose reference document.
-   Recommended next step if you want to go deeper: pick one Part (e.g.,
    `PART 3` vulnerability-class workflows) and I can expand any single
    vulnerability class into a full field-level walkthrough with the
    same why/what/decision-tree structure.

------------------------------------------------------------------------

# PART 7 --- ACTIVE DIRECTORY ASSESSMENTS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

> This part extends the methodology from Parts 1--6 and follows the same
> structure: **Recon → Enumeration → Testing → Validation → Evidence →
> Reporting**

## 7.1 Domain Enumeration

-   Domain discovery
-   Forest & trust mapping
-   LDAP enumeration
-   Kerberos reconnaissance
-   Group Policy review
-   BloodHound methodology
-   AD CS
-   Privilege escalation paths
-   Lateral movement methodology
-   Reporting

------------------------------------------------------------------------

# PART 8 --- INTERNAL NETWORK ASSESSMENTS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Network discovery
-   VLANs
-   Windows
-   Linux
-   VMware
-   Hyper-V
-   NAS
-   IPMI / iLO / iDRAC
-   SMB
-   NFS
-   SSH
-   WinRM
-   SNMP
-   Service enumeration
-   Decision trees

------------------------------------------------------------------------

# PART 9 --- CLOUD ASSESSMENTS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   AWS
-   Azure
-   Google Cloud
-   IAM
-   Object Storage
-   Containers
-   Kubernetes
-   Secrets Managers
-   Terraform
-   CI/CD
-   Serverless

------------------------------------------------------------------------

# PART 10 --- MOBILE ASSESSMENTS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Android
-   iOS
-   APK / IPA analysis
-   Certificate Pinning
-   Traffic interception
-   Local storage
-   Keystore / Keychain
-   Root & Jailbreak detection

------------------------------------------------------------------------

# PART 11 --- THICK CLIENT ASSESSMENTS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Electron
-   Java
-   .NET
-   Qt
-   Binary analysis
-   Local IPC
-   DLL Hijacking
-   Registry
-   Named Pipes
-   Local privilege boundaries

------------------------------------------------------------------------

# PART 12 --- API DEEP DIVE

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   REST
-   SOAP
-   GraphQL
-   gRPC
-   JSON-RPC
-   OData
-   WebSockets

------------------------------------------------------------------------

# PART 13 --- WEBSOCKET TESTING

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Authentication
-   Authorization
-   Replay
-   Subscription abuse
-   Rate limiting
-   Message tampering

------------------------------------------------------------------------

# PART 14 --- SSRF DEEP DIVE

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Internal services
-   Cloud metadata
-   Blind SSRF
-   DNS
-   HTTP
-   Out-of-band validation

------------------------------------------------------------------------

# PART 15 --- XXE DEEP DIVE

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   DOM
-   SAX
-   SOAP
-   SVG
-   DOCX
-   XLSX
-   Blind XXE

------------------------------------------------------------------------

# PART 16 --- DESERIALIZATION

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Java
-   PHP
-   Python
-   Ruby
-   .NET
-   Node.js

------------------------------------------------------------------------

# PART 17 --- TOOL PLAYBOOKS

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

For every tool document:

-   Purpose
-   Strengths
-   Weaknesses
-   Expected output
-   When to use
-   When not to use
-   How findings feed the next workflow

Categories:

-   Recon
-   Enumeration
-   Web
-   API
-   Network
-   Active Directory
-   Cloud
-   Mobile
-   Containers
-   Static Analysis
-   Dynamic Analysis
-   Forensics

------------------------------------------------------------------------

# PART 18 --- REPORTING TEMPLATES

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

-   Executive Summary
-   Technical Findings
-   Risk Matrix
-   Evidence Templates
-   CVSS
-   OWASP Mapping
-   MITRE ATT&CK Mapping
-   Retest Report

------------------------------------------------------------------------

# PART 19 --- COMPLETE PENTEST DECISION ENGINE

### Commands

``` bash
# Generic syntax
# Replace placeholders with values appropriate for the authorized assessment.

tool [options] <target>

# Examples by category
curl [options] <url>
nmap [scan-options] <target>
dig <domain> <record-type>
whatweb <url>
openssl s_client -connect <host>:<port>
ffuf -w <wordlist> -u <url>/FUZZ
```

**Purpose** - Identify or enumerate the technology relevant to this
section.

**Expected Output** - Relevant metadata, banners, headers, or inventory
information.

**Common Options** - Use options appropriate to the engagement scope and
Rules of Engagement.

**Artifacts Produced** - Logs - Screenshots - Request/response
captures - Enumeration results

**Feeds Into** - Continue to the next workflow or decision tree in the
corresponding section.

Create one end-to-end workflow covering:

Target Received

↓

Scope Validation

↓

Recon

↓

Enumeration

↓

Technology Identification

↓

Vulnerability Testing

↓

Validation

↓

Impact Assessment

↓

Reporting

↓

Retesting

↓

Engagement Closure

Every branch should include:

-   Why
-   What
-   Evidence
-   Next Step
-   Fallback
-   Confidence
-   Priority
-   Risk

------------------------------------------------------------------------

# APPENDICES

-   Wordlists
-   Checklists
-   Rules of Engagement Templates
-   Report Templates
-   Evidence Templates
-   CVSS Reference
-   CWE Mapping
-   OWASP Mapping
-   MITRE ATT&CK Mapping
