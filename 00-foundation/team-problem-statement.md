## Problem Title

Academic Stress & Mental Well-Being Imbalance

## Problem Description

### The Problem (1–2 sentences)

KIU undergraduates struggle to maintain a healthy balance between academic workload and mental well-being. Overlapping deadlines, late-night study habits, and social stigma around discussing stress lead to burnout, reduced motivation, sleep disruption, and lower academic performance.

### Who Experiences It

**Specific user segment:**  
First– to third-year KIU students taking **5+ courses** who experience recurring stress and motivation dips during midterms/finals and project weeks, and who prefer quick, private, peer-based support over formal counseling.

**NOT:** “All students” (too broad)  
**NOT:** Seniors focused mainly on thesis (different stress pattern)  
**NOT:** Students already in regular therapy (different needs, channels)

### When/Where Does It Occur

**Context — When:**

- Peaks during Weeks 5–8 (midterms) and Weeks 13–15 (finals)
- Intensifies 2–5 days before clustered deadlines
- Most acute late evenings (21:00–01:00) during solo study sessions

**Context — Where:**

- Dorm rooms, library quiet floors, labs, cafeteria corners
- Instagram/Messenger chats, LMS tabs, YouTube/Spotify in the background
- Often while working alone and comparing progress with peers

---

## Why It Matters

### Pain Level

**HIGH (8–9/10)**

**Signals we expect to hear in interviews:**

- “I’m exhausted but can’t switch off.”
- “I feel alone with this; everyone else looks fine.”
- “I’m just pushing through—no time to think about balance.”
- “Sleep is the first thing I sacrifice.”

### Frequency

**Very High** — recurring weekly, spikes during exams/projects.

**Back-of-the-envelope:**
If stress spikes **3–5 days/week** for **6–8 high-pressure weeks**, that’s **18–40 acute episodes/semester** per student, plus ongoing low-level stress the rest of the term.

### Consequences

**Academic Impact**

- Lower focus and retention; procrastination and last-minute work
- Decline in quality of submissions despite high effort
- Avoidance of challenging but growth-driving tasks

**Time Impact**

- Inefficient study sessions; time lost to doom-scrolling and rumination
- Recovery time after burnout episodes increases (sleep debt)

**Stress/Mental Impact**

- Anxiety, irritability, emotional exhaustion, feeling isolated
- Stigma; reluctance to seek help early

**Most Significant Consequence**
Students operate below their potential for long stretches of the semester; burnout cycles reduce learning, consistency, and confidence.

---

## Current Solutions

### What People Do Now

**Primary coping mix (informal)**

- Music, memes, short walks, naps, caffeine
- Light journaling/notes apps; sporadic habit trackers
- Vent to close friends/roommates; avoid public sharing

**Backup pattern**

- “Push through” near deadlines; post-deadline crash
- Promise to “do better next time,” but patterns repeat

**Occasional formal options**

- University services or hotlines (used infrequently due to stigma, time, or awareness)
- Generic wellness apps (abandoned due to setup friction or lack of relevance)

### Gaps in Current Solutions

- **Stigma & privacy:** Public sharing feels risky; formal help feels too heavy.
- **Friction:** Apps require long onboarding or daily essays; students drop off.
- **Relevance:** Generic content doesn’t reflect KIU context/semester rhythms.
- **Consistency:** No gentle, low-effort routine that actually sticks.
- **Peer energy:** Hard to feel “not alone” without safe, lightweight peer touchpoints.

**Fundamental gap:**  
There’s no **quick, private, stigma-aware** way to (1) check in emotionally, (2) feel seen by relatable peers, and (3) get a small nudge back to balance **in under 90 seconds**.

---

## Evidence

### What Makes You Think This Is Real?

**Personal & peer observations (to validate in interviews):**

- Late-night library/dorm study; visible stress in Weeks 6–8 & 13–15
- Friends admit stress privately but avoid public discussion
- Students cite “no time” for heavy wellness tools; want quick, discreet support

**Early social validation patterns to look for:**

- Instagram/Messenger chatter spikes near deadlines (“I’m dying this week”)
- Students share coping memes but not actionable habits
- Many “I’ll sleep after finals” jokes (normalized imbalance)

---

## Feasibility Assessment

### Technical Feasibility

**Can we build something in 8–10 weeks?** YES

**MVP concept:**

- **30–90s daily check-in:** mood + one-tap reflection
- **Anonymous peer snapshots:** “others felt X today—here’s what helped”
- **Tiny wins feed:** gratitude, study micro-goals, gentle focus prompts
- **Optional streaks/insights:** weekly trend + 1 actionable nudge
- **Privacy-first:** pseudonyms, opt-in small circles

**Tech stack (example):**

- Frontend: React/Vite (mobile-first PWA)
- Backend: Node/Express or FastAPI
- DB: Postgres (row-level security) or Supabase
- Auth: Email/OTP; no social graph required initially
- Hosting: Vercel/Render free tiers

**Feasibility:** HIGH — fits team skills/timebox.

### Access to Users

**Can we find 10+ people at KIU?** YES

**Where:**

- Large CS/Engineering lectures; labs (K-102, etc.)
- Library 19:00–23:00; dorm lounges 21:00–01:00
- Telegram/Discord cohort groups; peer mentors/RA networks

**Access feasibility:** VERY HIGH — rapid recruitment possible.

---

## Initial Ideas (Optional)

**Hypothesis for solution:**  
A **stigma-aware, micro-interaction app** that helps KIU students regain balance with **fast private check-ins**, **relatable peer perspectives**, and **one small nudge**—not therapy, not heavy wellness.

**Key design principles (to test):**

- **Micro, not macro:** value in under 90 seconds
- **Privacy by default:** no pressure to reveal identity
- **Student voice:** prompts/tips written by peers, for peers
- **Semester-aware:** midterm/finals rhythms reflected in prompts
- **Gentle, not spammy:** helpful nudges; user-controlled reminders

**NOT building:**

- A clinical mental-health tool or diagnosis system
- A social network with public posting or likes
- A habit tracker that requires long entries

**What we are building:**  
A **lightweight balance companion** for the KIU semester.
