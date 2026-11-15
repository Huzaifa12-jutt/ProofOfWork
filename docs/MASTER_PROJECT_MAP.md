# ProofOfWork — Master Project Map

**Product Owner:** HiTech Technologies  
**Version:** 1.0 (Final) | 15 November 2026  
**Tagline:** Don't Just Claim Your Skills. Prove Them.

---

## 1. Project Overview

ProofOfWork is a skill verification platform where candidates demonstrate their abilities through practical assessments (MCQs, coding challenges, written questions, SQL tasks, and project submissions). Companies can create assessments, invite candidates, evaluate submissions using structured rubrics, and shortlist proven talent.

- **Primary Goal:** Replace unsupported CV claims with verifiable evidence.
- **First Customers:** Small and medium software houses in Islamabad/Rawalpindi hiring juniors, QA, data, and interns.
- **MVP Success Test:** A company creates a test, a candidate completes it, a reviewer scores it with a rubric, and the recruiter reviews the evidence and shortlists.

---

## 2. Core System Architecture

```
ProofOfWork/
|-- apps/
|   |-- web/           Next.js website (Developer A)
|   |-- api/           NestJS server (Developer B)
|   `-- ai-service/    FastAPI AI service (added in Week 10)
|-- packages/
|   |-- database/      Prisma schema, migrations
|   `-- shared-types/  Shared TypeScript types & DTOs
|-- docs/              Documentation, ERD, architecture diagrams
|-- infra/             Local services configuration
```

- **Architecture:** Modular monolith. One main NestJS REST API server (`/api/v1`), one Next.js web application, and a separate Python FastAPI service added later for AI question generation.
- **Browser Security:** The web app talks only to the API; the browser never communicates directly with the database.

---

## 3. User Roles & Permission Matrix

1. **Candidate:** Creates profile, adds skills, takes timed assessments, submits answers/code/repos, views released results and evidence portfolio.
2. **Company / Recruiter:** Manages company profile, invites team members, creates/publishes assessments, invites candidates, reviews evidence, adds private notes, and shortlists.
3. **Reviewer:** Scores assigned submissions using evaluation rubrics, adds feedback comments, and releases results when authorized.
4. **Platform Admin:** Manages users, organizations, skills taxonomy, and audit logs.

*Golden Rule:* The server must check user identity and organization membership on every protected request. Never trust client-supplied IDs or roles.

---

## 4. Assessment Engine & Question Types

- **Supported Question Types:**
  - Single-choice MCQ (Auto-graded)
  - Multiple-select MCQ (Auto-graded with partial credit)
  - Short written answer (Rubric-graded)
  - Long written answer (Rubric-graded)
  - Coding / SQL task (Reviewer evaluated in MVP)
  - Debugging / Scenario (Rubric-graded)
  - Project / File / Repo submission (Rubric-graded)
- **Builder Options:**
  - **Option 1 (Manual Builder):** Direct question authoring with question bank reuse.
  - **Option 2 (AI-Assisted Drafts - Week 10):** Generates draft questions from job roles/skills. Must be reviewed, edited, and approved by a human before publishing.

---

## 5. Team Division & Ownership

| Developer | Ownership | Responsibilities |
| :--- | :--- | :--- |
| **Developer A (Frontend Lead)** | `apps/web` | UI/UX, forms, public site, candidate test runner, recruiter dashboards, Playwright tests |
| **Developer B (Backend Lead)** | `apps/api`, `packages/database` | NestJS modules, Prisma migrations, PostgreSQL, auth, permissions, API tests |

---

## 6. Development Roadmap (12 Weeks)

- **Week 1 (M0):** Repository baseline, ERD, API contract, wireframes.
- **Week 2 (M1):** Next.js & NestJS skeletons, Prisma setup, CI checks.
- **Week 3-4 (M2):** Authentication (Argon2id + JWT cookies), user profiles, organizations.
- **Week 5 (M3):** Assessment builder, question management, publish workflows.
- **Week 6 (M4):** Candidate assessment runner, timer, autosave, submission flows.
- **Week 7-8 (M5):** Submissions, rubric evaluations, evidence records, results release.
- **Week 9 (M6):** Recruiter search, talent filtering, comparison, shortlisting.
- **Week 10 (M7):** Python FastAPI service for AI-assisted question drafts.
- **Week 11-12 (M8):** Automated testing, security hardening, backups, pilot launch.
