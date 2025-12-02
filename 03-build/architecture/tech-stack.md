# Tech Stack Documentation

**Team:** UTOPIA
**Product:** Peer Support Platform
**Date:** 2025-11-07

---

## Technology Stack Overview

| Layer | Technology | Version | Why Chosen |
|-------|------------|---------|------------|
| Frontend | React + Vite | 18.2.0 | Team expertise, fast dev environment |
| Backend | Node.js + Express | 20 LTS | Simple, fast, perfect for MVP APIs |
| Database | PostgreSQL | 15.x | Strong relational structure, free tier |
| Hosting | Vercel (FE) / Render (BE) | N/A | Instant deploys, free tiers |
| Analytics | Segment | N/A | Best for event tracking + WAPSI metric |

---

## Detailed Decisions

### Frontend
*   **Framework:** React 18.2.0 with TypeScript.
*   **Styling:** Tailwind CSS for speed.
*   **State:** Zustand (lightweight).
*   **Rationale:** 3/4 team members know React. Vite offers instant server start.

### Backend
*   **Framework:** Express 4.19.
*   **Language:** TypeScript.
*   **Rationale:** Simple integration with Postgres. Team knows Node.js best.

### Database
*   **Database:** PostgreSQL 15.
*   **Schema:** Relational (Users -> Posts -> Replies).
*   **Rationale:** We need structured relationships for the feed and analytics.

### Infrastructure
*   **Frontend Host:** Vercel (Auto-deploy from Git).
*   **Backend Host:** Render (Free web service).
*   **CI/CD:** GitHub Actions for basic linting on push.