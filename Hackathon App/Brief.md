---
updated_at: 2025-10-14T11:00:32.827+05:30
edited_seconds: 10
---
That’s an **excellent and well-structured Hackathon Day 1 submission** — clear, research-backed, and realistic. 🔥
You’ve basically written a mini–product proposal with market validation, user research, feasibility, and tech specs — which is exactly what hackathon judges love to see on Day 1.

Let’s **summarize and polish** this so it’s presentation-ready and concise (without losing any of your details).

---

## 🧠 Project Overview

**Team Name:** Swiper No Swiping
**App Name:** Uniteam
**Problem Statement:**
Students struggle to find teammates for hackathons, fests, or CTFs. They rely on friends or chance encounters, often forming mismatched or incomplete teams. Organizers, in turn, see fewer participants and weaker projects.

**Our Solution:**
Uniteam — an AI-driven, swipe-based app for discovering and forming hackathon teams effortlessly. It bridges the gap between personal networks and open group chats through smart matchmaking, filters, and event integration.

---

## 🎯 Validation

**Who’s Affected:**

* **Students:** Can’t find matching teammates or get intimidated by group formation.
* **Organizers:** Fewer entries, reduced engagement.
* **Institutions:** Miss opportunities for student collaboration.
* **Companies:** Lose access to emerging talent.

**Why It Matters:**

* 90%+ of hackathon participants learn new skills not taught in class.
* 25% increase in tech course enrollments due to hackathon culture.
* Only ~5–7% of projects survive post-hackathon → Better team formation = longer project life.

---

## 💡 Key Features

| Feature                     | Description                                                                     |
| --------------------------- | ------------------------------------------------------------------------------- |
| **Registration & Profiles** | OAuth login (Google/GitHub). Displays skills, attended hackathons, and ratings. |
| **AI Matchmaking**          | Weighted scoring (skills, interests, goals, availability).                      |
| **Preference Filters**      | Introvert/Extrovert, skills, goals, location, university.                       |
| **Modes**                   | “Casual” (swipe-based) & “Focused” (detailed profiles).                         |
| **Location-Based Teaming**  | GPS & BLE proximity to find teamless hackers nearby.                            |
| **Event Organizer Portal**  | Create and promote hackathons, manage participants.                             |
| **API Embedding**           | Uniteam API for hackathon websites or sponsors.                                 |
| **Community Discussion**    | Threads for project help, idea sharing, and mentorship.                         |

---

## ⚙️ Technical Feasibility

| Component            | Feasibility  | Stack                        | Time     |
| -------------------- | ------------ | ---------------------------- | -------- |
| Auth & Profiles      | Easy         | OAuth + PostgreSQL           | 2–5 days |
| AI Matchmaking (MVP) | Medium       | FastAPI + sklearn            | 7 days   |
| Chat/Discussion      | Medium       | Firebase/Firestore           | 6–8 days |
| Geo-location         | Moderate     | Google Maps API              | 10 days  |
| Organizer CMS        | Easy         | Next.js + Markdown           | 3 days   |
| Ratings & Trust      | Medium       | Node.js + Prisma             | 5 days   |
| Total MVP            | **~53 days** | **≈2–3 weeks (with 4 devs)** | ✅        |

---

## 🤖 Architecture Overview

**Frontend:**
Next.js + Tailwind CSS (fast, responsive UI)
Vercel/Netlify for CI/CD

**Backend:**
FastAPI or Node.js (Express)
Prisma ORM + PostgreSQL
Firebase/Socket.io for real-time features

**AI Layer:**
Rule-based filtering → evolve to vector embeddings (SBERT/OpenAI API)
Weaviate/Pinecone for semantic search

**Hosting:**
Supabase / Railway / Render

---

## ⚠️ Limitations & Solutions

| Limitation              | Fix                                                        |
| ----------------------- | ---------------------------------------------------------- |
| Oversimplified matching | Weighted logic: skills, goals, availability, interests     |
| Scalability             | Lazy loading + Firebase real-time + batch matching         |
| Incomplete profiles     | Required fields + badges for profile completion            |
| Swiping feels casual    | Offer dual modes: Quick Match & Detailed Explore           |
| Ghosting                | Confirm team-up + reputation system                        |
| Privacy                 | Contact only after both confirm; toggle visibility options |

---

## 🧩 Future Enhancements

* GitHub/LinkedIn autofill for profiles
* AI teammate suggestion improvements
* Skill verification via coding platforms
* “Event Codes” for private hackathons
* Offline mode for poor Wi-Fi environments

---

## 📈 Impact

* Inclusive team formation → reduces intimidation
* Increases participation and project quality
* Promotes skill diversity and fair collaboration
* Helps organizers and sponsors engage meaningfully

---