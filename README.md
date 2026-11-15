# ProofOfWork

> **"Don't Just Claim Your Skills. Prove Them."**

**Product Owner:** HiTech Technologies ([hitech.pk](https://hitech.pk))  
**Version:** 1.0 (MVP Foundation)

---

## 📌 Project Overview

**ProofOfWork** is a skill verification and talent assessment platform. Candidates prove their abilities through practical assessments (coding challenges, written technical questions, SQL tasks, and real-world project submissions). Companies can create assessments, invite candidates, evaluate performance using structured rubrics, and shortlist proven talent with confidence.

### The Problem We Solve
Candidates often list skills on their CVs without verifiable evidence. Companies spend enormous time conducting repetitive, low-yield technical interviews. ProofOfWork replaces unsubstantiated claims with transparent, checkable evidence records.

---

## 🛠️ Technology Stack

| Layer | Technologies | Purpose |
| :--- | :--- | :--- |
| **Frontend (`apps/web`)** | Next.js 14+ (App Router), React, TypeScript, Tailwind CSS, shadcn/ui, Zod | Modern, accessible candidate & company user portals |
| **Backend (`apps/api`)** | NestJS, TypeScript, Node.js, REST API | Modular monolith: auth, permissions, assessments, rubrics |
| **Database (`packages/database`)** | PostgreSQL, Prisma ORM | Relational data persistence with strict schema migrations |
| **AI Microservice (`apps/ai-service`)** | Python 3.11+, FastAPI, Pydantic, LLM API | AI question drafting (Week 10 - requires human approval) |
| **Background Jobs** | Redis, BullMQ | Asynchronous tasks & decoupled processing |
| **Testing** | Jest, Supertest, Playwright | Unit, integration, and end-to-end browser testing |

---

## 📂 Repository Structure

```
ProofOfWork/
├── apps/
│   ├── web/               # Next.js frontend application (Developer A)
│   ├── api/               # NestJS backend REST API (Developer B)
│   └── ai-service/        # Python FastAPI service (Week 10)
├── packages/
│   ├── database/          # Prisma schema, migrations, seeders
│   └── api-client/        # Generated API client and types
├── docs/                  # Architecture diagrams, ERD, and master maps
├── infra/                 # Local services configuration
├── .editorconfig          # Code style rules
├── .env.example           # Safe environment variables template
├── .gitignore             # Git ignore patterns
├── CONTRIBUTING.md        # Two-developer Git workflow guide
├── SECURITY.md            # Security & vulnerability reporting policy
└── README.md              # Project documentation
```

---

## 👥 Two-Developer Team Division

This project is built collaboratively by a team of two developers:

- **Developer A (Huzaifa / Frontend Lead):** Owns `apps/web`, candidate experience, company UI/UX, forms, and browser testing.
- **Developer B (Friend / Backend Lead):** Owns `apps/api`, `packages/database`, PostgreSQL schema, authentication, permissions, and API tests.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for full branch naming, code review, and pull request rules.

---

## 🚀 Getting Started (Overview)

1. Clone the repository:
   ```bash
   git clone https://github.com/Huzaifa12-jutt/ProofOfWork.git
   cd ProofOfWork
   ```
2. Switch to the `develop` branch:
   ```bash
   git checkout develop
   ```
3. Copy environment configuration:
   ```bash
   cp .env.example .env
   ```
4. Follow the setup instructions in each app/package directory as modules are built.

---

## 📜 License & Governance

Internal proprietary project developed for **HiTech Technologies**. All rights reserved.
