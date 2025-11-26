# 🧱 Tech Stack Documentation

**Team:** UTOPIA
**Product:** UTOPIA – Anonymous Peer Support for Students
**Date:** 2025-11-07
**Version:** 1.0

---

# 🌐 Technology Stack Overview

### **Stack Summary**

| Layer               | Technology                      | Version                    | Why Chosen                                                |
| ------------------- | ------------------------------- | -------------------------- | --------------------------------------------------------- |
| **Frontend**        | React + Vite                    | React 18.2.0 / Vite 5      | Team expertise, fast dev environment, flexible components |
| **Backend**         | Node.js + Express               | Node 20 LTS / Express 4.19 | Simple, fast, perfect for MVP APIs                        |
| **Database**        | PostgreSQL                      | 15.x                       | Strong relational structure, free tier, fits app well     |
| **Hosting (FE)**    | Vercel                          | N/A                        | Instant deploys, perfect for React SPA                    |
| **Hosting (BE)**    | Render                          | N/A                        | Free server instances, auto deploy                        |
| **Analytics**       | Segment → PostgreSQL + Metabase | N/A                        | Best for event tracking + WAPSI metric                    |
| **Error Tracking**  | Sentry (Optional)               | Latest                     | Free tier + helpful for debugging                         |
| **Version Control** | Git + GitHub                    | N/A                        | Team collaboration                                        |

---

# 🎨 Detailed Technology Decisions

---

# 1. Frontend

**Framework:** **React 18.2.0**
**Tooling:** Vite 5
**Language:** TypeScript 5.x

### ⭐ Why We Chose React

1. **Team experience** — 3/4 team members already know React.
2. **Component-based structure** — perfect for Posts, Feed, Reactions, Replies.
3. **Fast iteration** — Vite dev server is instant, ideal for MVP.
4. **Large ecosystem** — libraries for UI, state, forms, UX enhancements.

### ❌ Alternatives Considered

- **Vue** — nice but no team experience.
- **Next.js** — too heavy for MVP, SSR unnecessary.

### 📚 Key Libraries

| Library                | Purpose          | Why                           |
| ---------------------- | ---------------- | ----------------------------- |
| Zustand                | State management | Lightweight and simple        |
| React Query (optional) | Server state     | Best for caching feed & posts |
| React Router           | Navigation       | Reliable SPA routing          |
| Tailwind CSS           | Styling          | Fast UI building              |
| Axios                  | HTTP requests    | Clean API calls               |

### ⚠️ Risks

- Medium: Overcomplicating state.
  **Mitigation:** Use Zustand + React Query clean separation.

---

# 2. Backend

**Framework:** **Express 4.19**
**Language:** TypeScript (Node 20 LTS)

### ⭐ Why We Chose Express

1. **Simple, fast, minimal** — perfect for MVP APIs.
2. **Easy integration** with PostgreSQL.
3. **Team familiarity** — Node is most known language in team.
4. Works seamlessly with Segment server-side events.

### ❌ Alternatives

- **Django** — too heavy.
- **FastAPI** — great but team would need new learning curve.

### 📚 Key Libraries

| Library                 | Purpose               | Version |
| ----------------------- | --------------------- | ------- |
| express                 | Core HTTP layer       | 4.19    |
| prisma or pg            | DB ORM / driver       | Latest  |
| cors                    | CORS config           | Latest  |
| zod                     | Input validation      | Latest  |
| dotenv                  | Environment variables | Latest  |
| @segment/analytics-node | Analytics             | Latest  |

### API Design:

- **Style:** REST
- **Auth:** Anonymous local ID sent to backend
- **Data Format:** JSON

### ⚠️ Risks

- None major — Express is stable for this scale.

---

# 3. Database

**Database:** **PostgreSQL 15**
**Hosting:** Supabase (optional) or Render PostgreSQL

### ⭐ Why PostgreSQL?

1. **Relational model fits data** (posts, reactions, replies).
2. **Free tier** available.
3. Team already used Postgres in Databases II.
4. Strong querying for feed + analytics.

### Schema Approach

- Highly relational, normalized.
- Index on `created_at` for feed.
- Separate tables:

```
users (anonymous_id)
posts
replies
reactions
analytics_events
```

### Estimated Data

- < 2000 posts total
- < 10k reactions
- Very small DB → extremely low risk

### Risks

- None significant.
- Backups provided by hosting platform.

---

# 4. Infrastructure & DevOps

### Hosting Choices

| Component               | Platform                     | Why                       |
| ----------------------- | ---------------------------- | ------------------------- |
| **Frontend**            | Vercel                       | Best for React apps, free |
| **Backend**             | Render free web service      | Easy deploy, free tier    |
| **Database**            | Render PostgreSQL / Supabase | Free, reliable            |
| **Analytics Dashboard** | Metabase                     | Beautiful dashboards      |

### Deployment Strategy

- FE: Auto-deploy on push to main (Vercel).
- BE: Auto-deploy on push to main (Render).
- DB: Manual migrations via Prisma CLI or SQL.

### Environment Setup

- `.env.example` with:

```
DATABASE_URL=
SEGMENT_WRITE_KEY=
```

- Local dev:

  - `npm run dev` for FE
  - `npm run dev` for BE

### CI/CD:

- GitHub Actions (optional)
- Run: `npm test` + typechecking before deploy

---

# 5. Analytics & Monitoring

### Analytics Platform: **Segment**

**Destination:** PostgreSQL + Metabase

### ⭐ Why Segment?

1. Easy SDK (frontend + backend).
2. Can forward to multiple tools if needed.
3. Perfect for custom events like **WAPSI**.

### Events Tracked

- `post_created`
- `feed_viewed`
- `reply_created`
- `reaction_added`
- `interaction_recorded` (**server-side NSM** event)

### Monitoring

- Optional Sentry (free tier)
- Backend logs
- Health endpoint (`/api/health`)

### Risks

- Privacy: must avoid PII
  **Mitigation:** use anonymous IDs only

---

# 6. Development Tools

### Git Workflow

- Branches:

  - `main`
  - `feature/*`

### Editor

- **VS Code**
  Extensions:
- ESLint
- Prettier
- Prisma (if used)
- Tailwind CSS IntelliSense

### Testing

- **Unit tests:** Jest
- **E2E:** Cypress (optional)
- **Coverage target:** 60% (good for MVP)

### Code Quality

- ESLint + Prettier
- Pre-commit hooks (optional)

---

# 7. Third-Party Services

| Service            | Purpose             | Risk                            |
| ------------------ | ------------------- | ------------------------------- |
| Segment            | Analytics           | Medium (API key leak potential) |
| Render             | Backend hosting     | Low                             |
| Vercel             | Frontend hosting    | Low                             |
| Metabase           | Analytics dashboard | Low                             |
| Supabase (if used) | DB hosting          | Low                             |

**Rate Limits:**

- Segment: 1000 events/day free tier
- Render: sleeps after inactivity (fine for MVP)

---

# 8. Security Considerations

- No personal data stored
- Anonymous ID only
- HTTPS enforced by Vercel & Render
- Backend input validation with Zod
- DB access restricted via environment variables
- CORS strict origins
- Content moderation (keyword filter)

---

# 9. Architecture Diagram

```
┌─────────────────────┐
│      Browser        │
└─────────┬───────────┘
          │  HTTPS
          ▼
┌─────────────────────┐
│   Frontend (React)  │
└─────────┬───────────┘
          │  REST API
          ▼
┌─────────────────────┐
│ Backend (Express)   │
└─────────┬───────────┘
          │
   ┌──────┴────────┐
   ▼               ▼
┌──────────┐   ┌─────────────┐
│PostgreSQL│   │ Segment API │
└──────────┘   └──────┬──────┘
                      ▼
                 Metabase Dashboard
```

---

# 10. Setup Instructions

### 🔧 1. Clone Repo

```bash
git clone https://github.com/kiu-utopia/utopia.git
cd utopia
```

### 🔧 2. Install Dependencies

```bash
# Frontend
cd frontend
npm install

# Backend
cd backend
npm install
```

### 🔧 3. Environment Variables

```bash
cp .env.example .env
```

Fill in:

```
DATABASE_URL=
SEGMENT_WRITE_KEY=
```

### 🔧 4. Run Development

```bash
# Frontend
npm run dev

# Backend
npm run dev
```

### 🔧 5. Verify

- FE: `http://localhost:3000`
- BE: `http://localhost:5000/api/health`

---

# 11. Open Technical Questions

| Question                           | Priority | Owner  | Target Date |
| ---------------------------------- | -------- | ------ | ----------- |
| Should we use Prisma or plain SQL? | Medium   | Aleksi | Week 7      |
| Do we need React Query?            | Low      | Teona  | Week 7      |
| Should replies support images?     | Low      | Team   | After MVP   |
