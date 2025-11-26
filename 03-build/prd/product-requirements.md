# Product Requirements Document (PRD)

**Product Name:** UTOPIA – Student Well-Being Platform
**Team:** UTOPIA
**Version:** 1.0
**Date:** 2025-11-07
**Status:** Draft
**Owner:** Teona Berozashvili (Product Lead / Discovery Lead)

---

## Document Control

| Version | Date       | Author             | Changes                 |
| ------- | ---------- | ------------------ | ----------------------- |
| 1.0     | 2025-11-07 | Teona Berozashvili | Initial draft for Lab 6 |

**Approval:**

- [ ] All team members reviewed
- [ ] Technical Lead approved
- [ ] Instructor feedback incorporated

---

## Executive Summary

UTOPIA is a web-based, anonymous peer-support space for KIU students who are struggling with the emotional toll of academic pressure. It creates a low-friction way to share “stress moments,” receive validating responses from peers, and see that others are going through similar experiences—especially late at night during peak exam periods when students feel most alone.

The product is designed specifically for first to third-year KIU students with heavy course loads who feel isolated and afraid of being judged if they show vulnerability. Instead of pretending everything is fine or silently burning out, they can post short, anonymous reflections, browse others’ experiences, and respond with simple, supportive gestures (reactions, short replies) that make people feel seen.

The expected impact is a measurable reduction in emotional isolation and an increase in supportive peer interactions during high-stress weeks. Our core belief: **connection and validation are the antidotes to burnout**, and even lightweight peer support can change how students experience pressure.

**One-Line Pitch:**
_A safe, anonymous peer-support space where KIU students can share stress moments and feel understood by others like them._

**Problem We're Solving:**
First to third-year KIU students with heavy course loads struggle to manage the emotional toll of academic pressure, especially during midterms and finals. A culture of perceived competence and fear of judgment makes it unsafe to admit vulnerability, leaving students feeling intensely isolated and pushing them into unhealthy coping mechanisms such as sacrificing sleep or avoidance, which leads to recurring burnout cycles.

**Solution Overview:**
UTOPIA provides an anonymous, low-effort space for students to share how they feel, see others’ experiences, and receive validating peer responses. The product focuses on emotional validation, not therapy: short posts (“stress moments”), themed feeds (e.g., academics, social, housing), supportive reactions and replies, and gentle check-ins at peak stress times. The experience is intentionally simple, mobile-friendly, and emotionally safe.

**Success Metric (North Star):**
**WAPSI – Weekly Active Peer-Support Interactions**
= count of meaningful interactions per week (e.g., an original post that receives at least one reply or supportive reaction from a peer, seen by the original poster).

---

## Table of Contents

1. [Problem Statement](#1-problem-statement)
2. [Target Users](#2-target-users)
3. [Goals & Success Metrics](#3-goals--success-metrics)
4. [User Needs & Stories](#4-user-needs--stories)
5. [Product Overview](#5-product-overview)
6. [MVP Scope](#6-mvp-scope)
7. [Features & Requirements](#7-features--requirements)
8. [User Experience](#8-user-experience)
9. [Technical Architecture](#9-technical-architecture)
10. [Assumptions & Dependencies](#10-assumptions--dependencies)
11. [Risks & Mitigation](#11-risks--mitigation)
12. [Timeline & Milestones](#12-timeline--milestones)
13. [Out of Scope](#13-out-of-scope)
14. [Appendix](#14-appendix)

---

## 1. Problem Statement

### The Problem

First to third-year KIU students with heavy course loads struggle to manage the emotional toll of academic pressure during high-stakes periods like midterms and finals. The dominant culture of perceived competence (“everyone else is handling it”) creates a strong stigma around admitting vulnerability, leaving students feeling that they are the only ones struggling.

When stress peaks—often at night when they are alone in dorms or commuting home—students lack a safe, informal channel for emotional validation. As a result, they adopt unhealthy coping mechanisms (sacrificing sleep, procrastinating out of anxiety, emotional shutdown) that damage both mental health and learning outcomes.

**Problem Severity:**

- **Frequency:**

  - Emotional overwhelm is recurring, especially around **midterms and finals**; many described it as a **weekly** or **daily** feeling during peak periods.

- **Intensity:**

  - Students used words such as “alone in my room,” “only person in the world,” “crash,” and “burnout” (8/10 interviews).

- **Economic/Educational Impact:**

  - Lost effective study time (hours spent in anxiety loops or avoidance), surface-level learning (“I passed the exam but didn’t actually learn anything”), and long-term burnout that reduces motivation for future semesters.

**Evidence:**

- Interview #01: “I passed the exam, but I didn’t actually learn anything… I just crashed afterwards.”
- Interview #03: “At night in my room I feel like I’m the only one failing.”
- Interview #07: “Everyone acts like they’re fine. If I admit that I’m stressed, it feels like I’m weak.”
- Patterns from synthesis:

  - “Fear of Judgment (Stigma)” in **9/10** interviews
  - “Feeling Alone (Isolation)” in **8/10** interviews
  - “Unhealthy Coping Mechanisms / Post-Burnout Crash” in **7–8/10** interviews

### Current Solutions & Why They Fail

**What people do now:**

1. **Pretend everything is fine / suppress feelings**

   - Why it fails: Increases internal pressure; feelings explode later as burnout, anxiety, or shutdown.

2. **Overwork and sacrifice sleep**

   - Why it fails: Short-term grades at the cost of health; students feel empty after exams and don’t retain material.

3. **Vent to 1–2 close friends (if available)**

   - Why it fails: Not everyone has that safe friend; even when they do, they fear “being a burden.” This doesn’t scale during peak exam weeks.

4. **Use generic mental-health or journaling apps**

   - Why it fails: Not KIU-specific, no sense of “others like me here,” feels like a solo activity, not peer validation.

**Evidence:**

- Multiple interviews described “just pushing through” or “crying alone in my room” instead of seeking support.
- Several participants explicitly rejected “therapy apps” or “formal counseling” as too heavy, too official, or not trusted in this context.

### Opportunity

The opportunity is to build a **lightweight, peer-based support layer** that fits inside existing student routines and culture. Students **don’t want therapy**; they want to feel understood by peers who share the same environment (same courses, same campus, same deadlines).

This hasn’t been solved at KIU because:

- Stigma makes public conversations about stress rare.
- Existing tools focus on productivity or formal mental-health support, not **informal emotional validation**.
- There is no dedicated space where KIU students can safely and anonymously say “this is hard” and be met with “me too, you’re not alone.”

Remote learning periods, high academic expectations, and social media pressure all **increase isolation**, making now the right moment to provide a targeted, low-friction peer-support product.

---

## 2. Target Users

### Primary User Persona: Nino – Overwhelmed On-Campus CS Student

**Demographics:**

- Age range: 18–21
- Role: 1st–3rd year undergraduate, often Computer Science or other demanding program
- Location: Lives on KIU campus (dorms)
- Education: Bachelor’s in progress
- Tech savviness: High (comfortable with apps, Discord, university systems)

**Psychographics:**

- **Goals:**

  - Pass tough courses without destroying mental health
  - “Keep up” with classmates who seem more confident
  - Feel that she’s not the only one struggling

- **Frustrations:**

  - Feels stupid or weak if she admits stress
  - Friends are also stressed; doesn’t want to “dump” on them
  - Nights before exams feel especially lonely and anxiety-heavy

- **Motivations:**

  - Wants to succeed academically
  - Wants to feel emotionally stable and not constantly in survival mode

- **Behaviors:**

  - Studies late into the night
  - Scrolls social media or watches random videos to escape stress
  - Rarely reaches out proactively for help

**Quote from Interviews:**

> “At night in my room before an exam, I feel like I’m the only one failing while everyone else is just… fine.”

**Jobs To Be Done:**

1. **When** I feel overwhelmed at night before exams, **I want to** share what I’m going through in a safe way, **so that** I can release some pressure and feel less alone.
2. **When** I’m doubting myself, **I want to** see that other KIU students feel this too, **so that** I don’t think I’m uniquely broken or weak.

**Interview Evidence:**

- Represents majority of interviewees (on-campus residents with heavy course loads)
- Interviews: #01, #02, #04, #05, #08

---

### Secondary User Persona: Giorgi – Commuter Student with Fragmented Day

**Demographics:**

- Age range: 19–23
- Role: 2nd–3rd year undergrad, mixed programs
- Location: Commutes 30–60+ minutes to campus
- Education: Bachelor’s in progress
- Tech savviness: Medium–High

**Psychographics:**

- **Goals:**

  - Survive long days (classes + commute) without burning out
  - Use gaps between classes productively

- **Frustrations:**

  - Feels disconnected from campus community
  - Stress builds up on the way home; no one around to talk to

- **Motivations:**

  - Wants a sense of belonging despite not living on campus

**Quote from Interviews:**

> “When I commute back home after a long day, I replay everything in my head and feel like I’m the only one who can’t handle it.”

**Jobs To Be Done:**

1. **When** I’m commuting after a heavy day, **I want to** quickly see if others felt the same stress, **so that** I feel less alone in that moment.

**Interview Evidence:**

- Interviews: #03, #06, #09

---

### User Segmentation

| Segment                          | Size (Relative) | Priority | Why                                |
| -------------------------------- | --------------- | -------- | ---------------------------------- |
| On-campus CS & STEM students     | Medium–High     | High     | Strongest pain, easiest to reach   |
| On-campus non-STEM students      | Medium          | Medium   | Similar emotions, varying context  |
| Commuter students (all programs) | Medium          | Medium   | Strong pain, slightly harder reach |

**Initial Focus:**
On-campus first to third-year CS/STEM students with 5+ courses. They showed the most intense patterns of burnout + isolation and are easier to recruit for early testing.

---

## 3. Goals & Success Metrics

### Product Vision

In one year, UTOPIA will be the **default emotional support layer** for KIU students during stressful periods: a place they check when things feel heavy, to share how they feel and to support others. It will normalize talking about stress, reduce isolation, and provide early signals of burnout that the community can respond to.

### Goals

**Primary Goal (MVP period):**
Validate that **anonymous peer-support interactions** reduce perceived emotional isolation for first to third-year KIU students during midterms/finals.

**Secondary Goals:**

1. Demonstrate that students are willing to **share honest stress moments** in a semi-structured anonymous format.
2. Show that other students are willing to **respond supportively** (reactions/replies) at meaningful volume.
3. Establish basic analytics and feedback loops to inform future iterations (e.g., categories that matter most).

### Success Metrics (AARRR Framework)

**Acquisition:**

- Metric: Number of **new students who visit and sign in** at least once per week during the pilot.
- Target (course project): 30–50 unique KIU students over pilot period.
- Measurement: `user_signup_completed` + `user_logged_in` events.

**Activation:**

- Metric: % of new users who **either create a post or leave a supportive reply** within 48 hours of first login.
- Target: ≥ 40% of new users.
- Measurement:

  - Event: `post_created` or `reply_created` within 48h of first `user_logged_in`.

**Retention:**

- Metric: % of users who return and interact (post, reply, or add reaction) in Week 2 or later.
- Target: ≥ 30% 2-week retention.
- Measurement: weekly counts of `post_created`, `reply_created`, `reaction_added` per user.

**Revenue:**

- Not applicable for this course project (no monetization in MVP).

**Referral:**

- Metric: % of active users who say they **invited a friend** (via lightweight in-app prompt or survey).
- Target: ≥ 20% of active users.

**North Star Metric (NSM):**

- **WAPSI – Weekly Active Peer-Support Interactions**

  - Count of interactions where an original post receives at least one **supportive reply or reaction** from a peer that the original poster sees.
  - Short-term Target (pilot): 20–30 WAPSI/week during active exam periods.

---

## 4. User Needs & Stories

### Core User Needs (from Discovery)

**Need #1: Feel Less Alone in Academic Struggle**

- **Evidence:**

  - Mentioned in interviews #01, #02, #03, #05, #07, #08
  - Students explicitly described feeling like the “only one failing.”

- **Intensity:** 9/10 (high emotional charge, repeated stories about crying/stress alone).
- **Quotes:**

  - “Everyone acts fine; I think I’m the only one behind.”

**Need #2: Safe, Non-Judgmental Space to Be Honest**

- **Evidence:**

  - “Fear of Judgment (Stigma)” pattern: 9/10 interviews.
  - People said they avoid talking about stress because it feels like admitting weakness.

- **Intensity:** 9/10.
- **Quotes:**

  - “If I say I’m stressed, it feels like I’m the weak one.”

**Need #3: Short, Low-Effort Emotional Check-In**

- **Evidence:**

  - Many described being too tired to “do a lot” when stressed; they want minimal friction.

- **Intensity:** 7/10.
- **Quotes:**

  - “I don’t have energy for long conversations. I just want to know I’m not alone.”

### User Stories (Summary)

Full document: `/03-build/user-stories/user-stories-list.md`

**MVP Stories (likely):**

1. User Story #1: **Anonymous Stress Moment Posting**
2. User Story #2: **Browse Peer Stories by Theme (e.g., academics, social, housing)**
3. User Story #3: **Supportive Reactions & Short Replies**
4. User Story #4: **Night-time Check-ins / Contextual Prompts**
5. User Story #5: **Lightweight Boundaries & Content Controls (hide tags, mute topics)**

**Post-MVP Stories (examples):**

6. User Story #6: **Saved / Favorite Posts That Helped Me**
7. User Story #7: **Opt-in Mood Tracking Over Time**
8. User Story #8: **Escalation Pathway to Formal Support Resources**

(See full user-stories-list.md for detailed acceptance criteria and interview citations.)

---

## 5. Product Overview

### High-Level Description

UTOPIA is a web application where KIU students can anonymously post short “stress moments” tied to themes like academics, social life, housing, or family. Other students can then read these posts, react with supportive emojis, and leave short, encouraging replies.

The app focuses on **emotional validation**, not medical treatment or formal counseling. It is intentionally simple: one primary feed, lightweight filtering by theme, and minimal friction to share or respond. The experience is optimized for late-night usage on mobile browsers or laptops.

System-wise, students sign in with a KIU-specific authentication (or invite code for the pilot), but their **public identity remains anonymous** in the feed. This preserves safety and honesty while still allowing us to track usage patterns (for analytics) at a user level.

### Core Value Proposition

**For** first to third-year KIU students feeling overwhelmed by academic pressure
**Who** feel isolated and afraid of being judged if they admit stress
**The** UTOPIA platform
**Is a** peer-support and emotional validation space
**That** lets them anonymously share their struggles and receive validating, supportive responses from others in the same environment
**Unlike** generic mental-health apps, group chats, or formal counseling
**Our product** is **tailored to KIU’s culture**, focuses on **peer understanding**, and is **light, fast, and safe** to use during real stress moments.

### Key Differentiators

1. **Context-Specific to KIU:**
   Posts and experiences are shared by people living under the same academic structure, exams, and campus conditions—not generic strangers on the internet.

2. **Emotion-First, Low Friction:**
   Short, anonymous “stress moments” instead of long posts or forms. Designed for a brain that is tired and overwhelmed.

3. **Safe & Judgment-Free by Design:**
   No public profiles or follower counts. Reactions and replies are intentionally supportive; community norms and simple moderation discourage toxicity.

**Evidence:**
Students repeatedly said they **didn’t want therapy apps** and **didn’t want to be judged by classmates**. They expressed that simply seeing others struggle in similar ways would already help them feel better.

---

## 6. MVP Scope

### Definition of MVP

MVP = **The minimum set of features** needed to validate whether anonymous peer sharing plus supportive reactions can **reduce emotional isolation** for KIU students during high-pressure periods.

**MVP Thesis:**
If we provide a simple, anonymous space where KIU students can share stress moments and receive validating peer responses, then we will observe repeated weekly peer-support interactions (WAPSI) and self-reported decreases in feeling “alone in this” during midterms/finals.

### MVP Features (Summary)

(Full definition to be captured in `/03-build/roadmap/mvp-definition.md`.)

| Feature                                    | Why It's in MVP                                          | Value | Effort |
| ------------------------------------------ | -------------------------------------------------------- | ----- | ------ |
| Anonymous KIU-authenticated access         | Needed to ensure safety and restrict to KIU students     | 5/5   | 3/5    |
| Stress moment creation (with category tag) | Core way to express emotional state                      | 5/5   | 3/5    |
| Main feed with basic filters               | Core way to see others’ experiences                      | 5/5   | 3/5    |
| Supportive reactions & short replies       | Core mechanism for peer validation (interactions)        | 5/5   | 3/5    |
| Night-time friendly UI & prompts           | Aligns with most painful time context (late-night usage) | 4/5   | 2/5    |
| Basic moderation / report content          | Safety requirement, even in pilot                        | 4/5   | 3/5    |

### MVP User Journey

**Step 1:**
Student signs in via KIU email / invite link → System verifies eligibility and creates an anonymous internal user profile.

**Step 2:**
Student lands on the main feed and sees recent anonymous posts tagged with themes (e.g., “Midterms,” “CS Homeworks,” “Social Anxiety”).

**Step 3:**
Student writes their own short stress moment (e.g., “I feel like I’m the only one who doesn’t understand X lecture”) and chooses a theme.

**Step 4:**
Other students browse the feed, react with supportive emojis (e.g., “I feel this too,” heart, hug) and/or write short replies.

**Step 5:**
The original poster returns later, sees reactions and replies → feels less alone and more validated.

**Step 6:**
Student continues using the app during other high-stress moments, contributing to recurring WAPSI.

### What's NOT in MVP (and why)

| Feature                                      | Why Excluded                                   | When to Revisit                     |
| -------------------------------------------- | ---------------------------------------------- | ----------------------------------- |
| Native mobile apps (iOS/Android)             | Too much dev cost for course timeline          | Post-course / Phase 2               |
| Advanced personalization / recommendation    | Overkill; simple filters are enough for pilot  | After initial validation            |
| Deep mood-tracking analytics for individuals | Sensitive and complex; can feel too “clinical” | Only if students explicitly want it |
| Real-time chat / group rooms                 | Moderation and complexity too high             | Phase 2, if core concept works      |

---

## 7. Features & Requirements

### Feature #1: Anonymous Stress Moment Posting

**Description:**
Allow students to quickly create short, anonymous posts describing how they feel, with an optional category/tag (e.g., academics, social, housing).

**User Story (reference):**
“As an on-campus CS student, I want to anonymously share what I’m going through when I feel overwhelmed, so that I can release pressure without being judged (Interviews #1, #4, #8).”

**Functional Requirements:**

1. System shall allow a logged-in user to submit a text post (e.g., 20–300 characters) with at least one theme/tag.
2. System shall store posts with timestamps and internal user IDs (not exposed publicly).
3. System shall prevent empty or excessively long posts (e.g., >1000 chars).
4. System shall confirm successful posting and return the post to the feed in < 2 seconds under normal load.

**Non-Functional Requirements:**

- **Performance:** Post submission must complete within 500 ms backend time for 95% of requests.
- **Scalability:** Support at least 1,000 posts total for the pilot.
- **Security:**

  - No personally identifiable information displayed by default.
  - Basic content checks (e.g., profanity/abuse detection later).

- **Accessibility:** Simple, high-contrast text input; usable on mobile and desktop.

**Acceptance Criteria:**

1. Given a logged-in user, when they type a valid message and click “Post,” then the post appears in the feed with a timestamp and theme.
2. Given a message exceeding character limit, when they click “Post,” then they see a clear validation message and nothing is saved.
3. Given an unauthenticated user, when they try to access post creation, then they are redirected to login screen.

**Priority:** P0 (Must-Have)
**Dependencies:** Authentication, database connection.
**Open Questions:**

- [ ] Do we need a “draft” state or is instant posting fine for MVP?

---

### Feature #2: Main Feed & Filtering

**Description:**
A simple feed showing recent stress moments, with basic filters by theme (e.g., “Academics,” “Social,” “Housing,” “Other”).

**Functional Requirements:**

1. System shall display posts in reverse chronological order by default.
2. System shall allow filtering by theme/tag via simple UI controls.
3. System shall paginate or lazy-load posts to avoid huge payloads.

**Non-Functional Requirements:**

- **Performance:** Feed load time ≤ 1 second for 50 recent posts.
- **Accessibility:** Scrollable, keyboard-friendly navigation.

**Acceptance Criteria:**

1. Given 20 existing posts, when a user visits the home page, then they see at least the 10 most recent posts.
2. Given posts with different themes, when the user selects “Academics” filter, then only posts tagged “Academics” are shown.

**Priority:** P0
**Dependencies:** Posts storage, basic API endpoints.

---

### Feature #3: Supportive Reactions & Short Replies

**Description:**
Enable students to respond to posts with quick, supportive gestures: emoji reactions and short text replies.

**Functional Requirements:**

1. System shall allow users to add a reaction (from a limited set) to any post.
2. System shall display total counts of each reaction type per post.
3. System shall allow users to write short replies (e.g., 20–200 characters).
4. System shall display replies under the corresponding post.

**Non-Functional Requirements:**

- **Security:**

  - Basic filters/checks against abusive content in replies.

- **Performance:** Reaction and reply submission must feel instant (< 300 ms backend time target).

**Acceptance Criteria:**

1. Given a logged-in user, when they click a reaction on a post, then the count increases and remains persistent on refresh.
2. Given a logged-in user, when they write a reply and submit, then the reply appears under the post.
3. Given an unauthenticated user, when they try to react or reply, they are prompted to log in.

**Priority:** P0
**Dependencies:** Authentication, posts feature.

---

### Feature #4: Night-Time Friendly UI & Contextual Prompts

**Description:**
Make the experience comfortable and welcoming for late-night usage, with dark UI and gentle prompts that normalize stress.

**Functional Requirements:**

1. System shall provide a dark-theme UI with calming colors.
2. System shall show different micro-copy at night hours (e.g., “You’re not alone. Many students feel this way during exams.”).

**Non-Functional Requirements:**

- **Performance:** No additional heavy assets for dark mode beyond basic CSS.

**Acceptance Criteria:**

1. Given the client time between 21:00–01:00, the header subtitle shows a night-time supportive message.
2. Given daytime use, the header subtitle shows a neutral message.

**Priority:** P1 (Should-Have)
**Dependencies:** Base UI.

---

### Feature #5: Basic Moderation & Reporting

**Description:**
Give users a simple way to report harmful or inappropriate content and allow admins to review and act.

**Functional Requirements:**

1. System shall allow users to report a post or reply.
2. System shall store reports with timestamps and reasons.
3. Admin view (simple internal tool or DB inspection) shall allow marking content as removed.

**Non-Functional Requirements:**

- **Security:** Ensure only trusted admins can access moderation actions.

**Acceptance Criteria:**

1. Given a user, when they click “Report” and select a reason, then a report entry is stored.
2. Given a reported post, when an admin marks it as removed, then it no longer appears in the feed.

**Priority:** P0 (for safety)
**Dependencies:** Authentication + basic admin role.

---

## 8. User Experience

### Information Architecture

**Main Sections:**

1. **Home / Feed:** Main view with stress moments and filters.
2. **Create Post:** Embedded on home or via modal for quick posting.
3. **Info / Safety Page:** Explains purpose, guidelines, and crisis contacts.
4. **(Internal)** Admin/Moderation view (could be very simple or DB-only in MVP).

**Navigation Flow:**

- Default landing: Home/Feed.
- Primary actions: “Share a moment” (CTA button) and “Support others” (scroll + react/reply).

### Key User Flows

**Flow 1: Share a Stress Moment**

1. **Entry Point:** User logs in → Home feed.
2. Click “Share how you’re feeling” button.
3. Type short message, choose theme, click Post.
4. See confirmation and their post appearing in the feed.

**Success State:** Post is live and visible; user feels a small sense of relief.
**Error States:**

- Invalid input (too long/empty) → error message, no data loss.
- Network error → temporary message with retry.

---

**Flow 2: Support Another Student**

1. **Entry Point:** User on the Home feed.
2. Scroll and read stress moments.
3. Tap a reaction (“I feel this too,” heart, etc.) or open replies area.
4. Write a short supportive reply and submit.

**Success State:** Reaction count increments or reply appears; user feels they helped someone.
**Error States:** As above (network errors, validation).

---

### Wireframes / Mockups

(To be linked later from Figma or Miro.)

**Screen 1: Home / Feed**

- Purpose: Read and support others, entry point to posting.
- Key elements:

  - Header with product name + supportive subtitle
  - “Share a moment” input or button
  - Filter chips (Academics / Social / Housing / Other)
  - List of posts with reactions and reply counts

**Screen 2: Post Detail (optional, or inline)**

- Purpose: See full post and replies.
- Key elements:

  - Original post text + theme + timestamp
  - Reactions row
  - Replies list
  - Reply composer

---

## 9. Technical Architecture

Full design: `/03-build/architecture/system-design-v1.md`

### Tech Stack (Draft)

**Frontend:**

- Framework: React (or similar modern SPA)
- Styling: Simple CSS or Tailwind (TBD)
- Reasoning: Team familiarity and fast iteration for a web app.

**Backend:**

- Framework: Node.js + Express (or similar)
- Database: PostgreSQL (shared with analytics where possible)
- Reasoning:

  - Familiar to team
  - Good fit for simple CRUD + event logging

**Infrastructure:**

- Hosting:

  - Frontend: Vercel or Netlify (preview + prod)
  - Backend: Render / Railway / similar student-friendly hosting

- CI/CD: GitHub Actions for lint + basic tests on PR and deploy on merge.

**Analytics:**

- Platform: Segment → PostgreSQL + Metabase
- Reasoning:

  - Already defined in analytics plan
  - Keeps event data in a warehouse we control.

### High-Level Architecture

```text
User (Browser)
   ↓
React Frontend (UTOPIA Web)
   ↓ REST/JSON
Node/Express Backend API
   ↓
PostgreSQL (app DB: posts, users, reactions)
   ↓
Segment Events → Analytics DB → Metabase Dashboards
```

### Data Model (High-Level)

**User (internal):**

- id (UUID)
- created_at
- last_login_at

**Post:**

- id (UUID)
- user_id (FK, internal only)
- content (text)
- theme (enum: academics, social, housing, other)
- created_at

**Reaction:**

- id
- post_id (FK)
- user_id (FK)
- type (enum: feel_this, heart, hug, etc.)
- created_at

**Reply:**

- id
- post_id (FK)
- user_id (FK)
- content (short text)
- created_at

### API Endpoints (Key Endpoints)

| Method | Endpoint              | Purpose                   | Auth Required  |
| ------ | --------------------- | ------------------------- | -------------- |
| POST   | /api/login            | Basic login / onboarding  | Yes (internal) |
| GET    | /api/posts            | List posts (with filters) | Yes            |
| POST   | /api/posts            | Create post               | Yes            |
| POST   | /api/posts/:id/react  | Add reaction              | Yes            |
| POST   | /api/posts/:id/reply  | Add reply                 | Yes            |
| POST   | /api/posts/:id/report | Report content            | Yes            |

---

## 10. Assumptions & Dependencies

### Assumptions

**User Assumptions:**

1. Students are willing to post honestly if anonymity is guaranteed.

   - **Validation:** Usage metrics + feedback survey.

2. Students are willing to support others with reactions/replies.

   - **Validation:** WAPSI and reaction/reply rates.

**Technical Assumptions:**

1. Free-tier hosting and DB resources will be sufficient for pilot.

   - **Risk:** Performance issues if usage spikes.

2. Team can implement basic React + Node + Postgres stack within timeline.

   - **Risk:** Underestimation of integration complexity.

**Business/Context Assumptions:**

1. KIU culture will accept anonymous peer-support platform (no institutional blocks).

   - **Risk:** Concerns from administration or staff.

### External Dependencies

| Dependency              | Type    | Risk   | Mitigation                        |
| ----------------------- | ------- | ------ | --------------------------------- |
| Hosting (Vercel/Render) | Service | Medium | Have backup hosting options       |
| Segment / Metabase      | Service | Low    | If fails, fall back to DB queries |

### Internal Dependencies

| Dependency      | Owner  | Delivery Date | Impact if Delayed         |
| --------------- | ------ | ------------- | ------------------------- |
| Auth + DB setup | Aleksi | Sprint 1      | Blocks all other features |
| Basic UI        | Saba   | Sprint 1      | Blocks user testing       |

---

## 11. Risks & Mitigation

### High-Priority Risks

**Risk #1: Low Engagement (Students Don’t Post or Reply)**

- **Likelihood:** Medium
- **Impact:** High
- **Mitigation:**

  - Recruit core early adopters manually.
  - Seed a few example posts (clearly flagged) to lower barrier.

- **Contingency:**

  - Conduct quick follow-up interviews to adjust UX or messaging.

**Risk #2: Harmful or Triggering Content**

- **Likelihood:** Medium
- **Impact:** High
- **Mitigation:**

  - Clear community guidelines.
  - Reporting + admin removal.
  - Crisis resources on Info/Safety page.

- **Contingency:**

  - Temporary shutdown or stricter moderation if needed.

**Risk #3: Over-Scoping for 6 Weeks**

- **Likelihood:** High
- **Impact:** Medium–High
- **Mitigation:**

  - Ruthlessly prioritize MVP features.
  - Keep nice-to-haves clearly out of scope.

---

## 12. Timeline & Milestones

Full roadmap: `/03-build/roadmap/product-roadmap.md`

### 8-Week Development Plan (Course Sprints)

**Sprint 1: Foundation (Weeks 7–8)**

- **Goal:** Get a basic vertical slice working (auth → create post → see post).
- **Deliverables:**

  - [ ] Auth + user model
  - [ ] Post creation API + UI
  - [ ] Basic feed rendering

- **Success Criteria:**

  - At least 1 internal user can post and see their post on another device.

**Sprint 2: User Testing (Weeks 9–10)**

- **Goal:** Complete core MVP features + run limited pilot.
- **Deliverables:**

  - [ ] Reactions & replies feature
  - [ ] Simple filters by theme
  - [ ] Info/Safety page
  - [ ] First student pilot (5+ users)

- **Success Criteria:**

  - WAPSI > 5/week in small pilot group; qualitative feedback collected.

**Sprint 3: Polish & Launch (Weeks 11–12)**

- **Goal:** Improve UX, harden moderation, and integrate basic analytics.
- **Deliverables:**

  - [ ] Night-time UX polish
  - [ ] Reporting & moderation
  - [ ] Segment integration + Metabase NSM dashboard
  - [ ] Final demo preparation

- **Success Criteria:**

  - Working analytics dashboard showing WAPSI; product stable enough for demo.

### Key Milestones

| Milestone            | Date (Week) | Definition of Success                           |
| -------------------- | ----------- | ----------------------------------------------- |
| Sprint 1 Complete    | Week 8      | Vertical slice working, basic posting + feed    |
| MVP Pilot Start      | Week 9–10   | 5+ real users invited and using app             |
| MVP Feature Complete | Week 12     | All P0 features implemented and stable          |
| Final Demo           | End of term | Clear story: problem → solution → impact → data |

---

## 13. Out of Scope

### Explicitly NOT Included in MVP

1. **Clinical Mental Health Features (diagnosis, treatment, etc.):**

   - Out of scope due to ethical, legal, and complexity reasons.

2. **Fully-fledged Chat or Group Rooms:**

   - Too complex to moderate and build within course time; revisit later.

3. **Complex Gamification (levels, streaks, badges):**

   - Nice-to-have for engagement but not required to validate core thesis.

### Future Considerations (Post-Course)

**Phase 2 Ideas:**

- Peer “circles” or small, themed groups.
- Optional mood tracking over time + reflective insights.

**Deferred Based on Technical Complexity:**

- Real-time updates (websockets) instead of simple polling.

**Deferred Based on Market Validation:**

- Integration with university services (counseling center links, etc.) at deeper level.

---

## 14. Appendix

### A. Interview Summary

**Total Interviews Conducted:** 10
**Date Range:** Weeks 3–4 (Fall 2025)
**Interview Documentation:** `/01-discovery/interview-logs/`
**Synthesis Results:** `/01-discovery/synthesis/`

**Key Insights:**

1. Fear of judgment is the biggest barrier to talking honestly about stress.
2. Students feel most alone at night during peak exam periods.
3. Connection + validation (not productivity tips) are what they crave most.

### B. Research & Competitive Analysis

(TBD – if completed, link here.)

### C. Technical Spikes

(TBD – to be stored under `/03-build/architecture/spike-*.md`.)

### D. References

- Course materials: Product Development for Software Engineers, KIU 2025.
- Internal docs: `final-problem-statement.md`, `user-stories-list.md`, analytics docs.

### E. Glossary

| Term  | Definition                                                               |
| ----- | ------------------------------------------------------------------------ |
| WAPSI | Weekly Active Peer-Support Interactions (NSM).                           |
| MVP   | Minimum Viable Product – smallest version that can test core hypothesis. |

---

## Sign-Off

**Team Agreement:**

- [ ] Teona Berozashvili – Reviewed and approved
- [ ] Ani Kelenjeridze – Reviewed and approved
- [ ] Saba Morchilashvili – Reviewed and approved
- [ ] Aleksi Tkebuchava – Reviewed and approved

**Instructor Feedback:**
_(To be filled after review.)_

**Approval Date:** ********\_\_********

---

## Document Maintenance

**Update Frequency:** Review and update after each sprint.

**Change Log:**

| Date       | Section | Change        | Reason            |
| ---------- | ------- | ------------- | ----------------- |
| 2025-11-07 | All     | Initial draft | Lab 6 deliverable |

**Next Review Date:** End of Sprint 1 (Week 8)

---

**Document Location:** `/03-build/prd/product-requirements.md`

**Related Documents:**

- User Stories: `/03-build/user-stories/user-stories-list.md`
- Product Roadmap: `/03-build/roadmap/product-roadmap.md`
- Technical Architecture: `/03-build/architecture/system-design-v1.md`
- Interview Synthesis: `/01-discovery/synthesis/final-problem-statement.md`
