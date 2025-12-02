# Sprint 1 Plan: Foundation & Core Experience

**Team:** UTOPIA
**Sprint:** 1
**Duration:** 2 weeks
**Dates:** Nov 10 - Nov 23, 2025
**Sprint Goal:** Establish technical infrastructure and enable anonymous post creation.

---

## Sprint Goal
By the end of this sprint, a user should be able to land on the site, be assigned an anonymous ID automatically, write a stress moment, and see it appear in the feed.

## Team Capacity
* **Aleksi (Tech Lead):** 15 hrs (Backend/DB Focus)
* **Saba (Dev):** 15 hrs (Frontend/UI Focus)
* **Teona (Product):** 10 hrs (QA/Requirements)
* **Ani (Research):** 10 hrs (User Testing Prep)

---

## User Stories Selected
1.  **US#6: Anonymous Onboarding** (High Priority)
2.  **US#1: Anonymous Sharing of Stress** (High Priority)
3.  **US#2: Reading Similar Peer Posts** (High Priority - Basic Read Only)

---

## Task Breakdown

### 1. Infrastructure & Database (Owner: Aleksi)
- [ ] Set up PostgreSQL database on Render/Supabase (Est: 2h)
- [ ] Initialize Express.js project with TypeScript (Est: 2h)
- [ ] Create database schema (Users, Posts tables) (Est: 3h)
- [ ] Set up API endpoints: `POST /api/posts`, `GET /api/posts` (Est: 4h)

### 2. Frontend Foundation (Owner: Saba)
- [ ] Initialize Vite + React + Tailwind project (Est: 2h)
- [ ] Implement "Anonymous ID" logic (Local Storage generation) (Est: 3h)
- [ ] Build "Create Post" UI Component (Est: 4h)
- [ ] Build "Feed" UI Component (Read-only list) (Est: 4h)

### 3. Integration & Logic (Shared: Aleksi & Saba)
- [ ] Connect Frontend "Post" button to Backend API (Est: 3h)
- [ ] Connect Frontend "Feed" to Backend API (Est: 3h)

### 4. Quality Assurance & Testing (Owner: Teona)
- [ ] Verify anonymous IDs persist on page refresh (Est: 1h)
- [ ] Test post creation (character limits, empty states) (Est: 2h)
- [ ] Verify data appears correctly in database (Est: 1h)

### 5. Prep for Next Sprint (Owner: Ani)
- [ ] Draft usability test script for Sprint 2 (Est: 2h)
- [ ] Create list of 5 students to test MVP in Week 9 (Est: 2h)

---

## Schedule

**Week 1:**
*   **Mon-Wed:** Project Init, DB Setup, UI Skeletons.
*   **Thu-Fri:** API Construction, Frontend Logic.

**Week 2:**
*   **Mon-Wed:** API Integration (Connecting Front to Back).
*   **Thu:** Testing & Bug Fixes.
*   **Fri:** Sprint Review (Internal Demo).

---

## Risks
*   **Database Connection:** If Render free tier is slow, we might need to switch to Supabase.
*   **State Management:** Ensuring the anonymous ID stays with the user without login.