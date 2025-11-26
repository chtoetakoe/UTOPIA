# User Story Mapping

**Team:** UTOPIA  
**Date:** 2025-11-07  
**Product:** UTOPIA – Peer Support Platform for KIU Students  
**Version:** 1.0

---

## 🎯 Purpose

This document visualizes the **end-to-end user journey** of KIU students using UTOPIA, mapping how user stories connect to the product’s **core goals** and **MVP features**.  
It bridges insights from our 10 discovery interviews into actionable development flow.

---

## 🧠 Overview

- **Primary Persona:**  
  First–third-year KIU student feeling academic or emotional stress, seeking connection and validation but afraid of judgment.

- **Core User Need:**  
  “I want to feel understood and supported without fear of being judged.”

- **North Star Metric (NSM):**  
  **WAPSI** — Weekly Active Peer-Support Interactions (measures engagement in posts, replies, or reactions).

---

## 🗺️ Journey Map Structure

| Phase                   | User Goal                       | Key Actions                       | Emotional State       | Supporting MVP Features             |
| ----------------------- | ------------------------------- | --------------------------------- | --------------------- | ----------------------------------- |
| 1. Onboarding           | Understand & trust the platform | Learn about anonymity and purpose | Curious but hesitant  | F6: Anonymous Onboarding            |
| 2. Posting              | Share thoughts safely           | Write & submit an anonymous post  | Relieved, hopeful     | F1: Anonymous Posting               |
| 3. Browsing             | Read others’ stories            | Scroll peer feed, filter by topic | Connected, understood | F2: Peer Feed, F7: Category Tagging |
| 4. Reacting             | Validate and empathize          | Tap emoji reaction                | Supportive, caring    | F3: Quick Reactions                 |
| 5. Replying             | Offer deeper support            | Write short supportive comment    | Empowered, kind       | F4: Supportive Replies              |
| 6. Feeling Seen         | Know their post mattered        | See “Seen by peers” counter       | Validated, calmer     | F5: Seen Indicator                  |
| 7. Safety               | Maintain respectful environment | Report inappropriate content      | Safe, respected       | F8: Report/Flag Content             |
| 8. Reflection (Stretch) | Track emotions over time        | Use mood check-in (optional)      | Self-aware            | F9: Mood Check-In                   |

---

## 🧩 Epics and User Stories

### **Epic 1 – Trust & Onboarding**

> “I want to feel safe enough to open up.”

**User Stories:**

- **US#1:** As a new user, I want to understand how anonymity works so I feel safe sharing (F6).
- **US#2:** As a new user, I want to sign up without revealing my real identity (F6).

**Outcome:** Students trust the platform enough to post authentically.

---

### **Epic 2 – Expression & Sharing**

> “I want to share my thoughts without being judged.”

**User Stories:**

- **US#3:** As a stressed student, I want to post anonymously about how I feel (F1).
- **US#4:** As a student, I want to categorize my post (academic/social/etc.) for visibility (F7).

**Outcome:** Students can safely express emotions and feel immediate relief through sharing.

---

### **Epic 3 – Discovery & Connection**

> “I want to see that I’m not alone.”

**User Stories:**

- **US#5:** As a user, I want to browse others’ anonymous posts so I can relate to their experiences (F2).
- **US#6:** As a user, I want to filter posts by category to find relevant stories (F7).

**Outcome:** Students gain emotional validation and a sense of belonging through reading others’ experiences.

---

### **Epic 4 – Validation & Empathy**

> “I want to show and receive support easily.”

**User Stories:**

- **US#7:** As a user, I want to react quickly with emojis to show empathy (F3).
- **US#8:** As a user, I want to write short supportive replies under posts (F4).
- **US#9:** As a poster, I want to know when someone viewed my post (F5).

**Outcome:** Emotional loop completed — posts generate acknowledgment, reducing isolation.

---

### **Epic 5 – Safety & Well-Being**

> “I want this space to stay safe and kind.”

**User Stories:**

- **US#10:** As a user, I want to report harmful or inappropriate posts (F8).
- **US#11:** As a poster, I want to remove my own post if I regret sharing it (future).
- **US#12 (Stretch):** As a user, I want to check in with my mood to track progress (F9).

**Outcome:** Trust and community maintained through safety and emotional reflection.

---

## 🧭 Hierarchical Map (Text Format)

UTOPIA Journey Map
│
├── Epic 1: Trust & Onboarding
│ ├── US#1 – Learn about anonymity
│ └── US#2 – Anonymous registration
│
├── Epic 2: Expression & Sharing
│ ├── US#3 – Post anonymously
│ └── US#4 – Add category to post
│
├── Epic 3: Discovery & Connection
│ ├── US#5 – Browse peer posts
│ └── US#6 – Filter by category
│
├── Epic 4: Validation & Empathy
│ ├── US#7 – React to posts
│ ├── US#8 – Write supportive replies
│ └── US#9 – See post views ("Seen by peers")
│
└── Epic 5: Safety & Well-Being
├── US#10 – Report content
├── US#11 – Delete my post (post-MVP)
└── US#12 – Mood check-in (stretch)

---

## 🪜 MVP Focus

**Included in MVP (Weeks 7–12):**

- F1: Anonymous Posting
- F2: Peer Feed
- F3: Quick Reactions
- F4: Supportive Replies
- F5: Seen Indicator
- F6: Anonymous Onboarding
- F7: Category Tagging
- F8: Report Content

**Stretch (if capacity):**

- F9: Mood Check-In

**Excluded (Future):**

- F10: AI-generated supportive prompts

---

## 🧩 Validation Links

| Epic           | Related Metric                  | Success Target   | Validation Method                 |
| -------------- | ------------------------------- | ---------------- | --------------------------------- |
| 1 – Trust      | New users completing onboarding | ≥ 80%            | Track onboarding completion event |
| 2 – Sharing    | # of posts created              | ≥ 100 in 2 weeks | Event tracking in database        |
| 3 – Connection | Avg. session time               | ≥ 2 minutes      | Analytics dashboard               |
| 4 – Empathy    | % of posts with reaction/reply  | ≥ 60%            | Segment events                    |
| 5 – Safety     | # of reports resolved           | 100% within 48h  | Admin moderation log              |

---

## 🔗 Traceability

| Epic | MVP Feature(s) | User Story IDs | Sprint     |
| ---- | -------------- | -------------- | ---------- |
| 1    | F6             | US#1–2         | Sprint 1   |
| 2    | F1, F7         | US#3–4         | Sprint 1   |
| 3    | F2, F7         | US#5–6         | Sprint 2   |
| 4    | F3, F4, F5     | US#7–9         | Sprint 2–3 |
| 5    | F8, F9         | US#10–12       | Sprint 3   |

---

## 🧩 Insights to Implementation Flow

1. **Students first need psychological safety (Onboarding, Anonymity).**
2. **Then they express themselves (Anonymous Posts).**
3. **Then they connect and empathize (Feed, Reactions, Replies).**
4. **Finally, the system nurtures trust and sustainability (Safety, Moderation).**

---

## 🧱 Definition of Done (for all Epics)

- [ ] Feature meets acceptance criteria from user stories
- [ ] No personal data exposed
- [ ] Logged analytics events verified (Segment → Postgres)
- [ ] Feature tested across browsers
- [ ] User flow validated via peer test

---

## 📄 Document Metadata

**File:** `/03-build/user-stories/story-mapping.md`  
**Created by:** Team UTOPIA  
**Course:** Product Development for Software Engineers (Fall 2025)  
**Instructor:** Zeshan Ahmad  
**Last Updated:** 2025-11-07
