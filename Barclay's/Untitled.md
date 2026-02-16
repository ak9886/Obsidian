---
updated_at: 2026-02-16T11:03:15.773+05:30
edited_seconds: 90
---

Current Solutions & Why They Don’t Work at Barclays

SIEM Platforms

Centralize logs and trigger alerts

- High alert volume, low prioritization

- Alerts treated as isolated events, not incidents
→ Detection exists, decision-making is manual

EDR / XDR Tools

Strong endpoint and identity telemetry

- Limited cross-system and vendor correlation

- High false positives during outages or maintenance
→ Good signals, poor context

# SOAR Platforms

## Automate predefined responses

- Assume alerts are already high confidence

- Over-automation risk in ambiguous scenarios
→ Automation without trust increases risk

# Threat Intelligence Feeds

## External threat context

- Generic and often irrelevant internally
→ Enrichment, not incident clarity



---

# Human Analysts

## Correct decisions when experienced

- Tribal knowledge, fatigue, inconsistency
→ Does not scale under pressure



---

# Core Gap

- Existing tools detect events.
- Barclays lacks a system that correlates behavior, ranks trust, and guides response decisions safely.
