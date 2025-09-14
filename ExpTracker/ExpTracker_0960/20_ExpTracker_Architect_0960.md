# Family Expense Tracker – System Architecture Document (v0.96.0)

## Introduction

This document defines the full-stack system architecture for the Family Expense Tracker (aligned with PRD v0.96.0), updating the previous version (v0.94.0) to include major enhancements in calendar scheduling, multi-currency/exchange management, and refinements throughout the technical stack and workflow. It serves as the fundamental reference for AI-driven and manual implementation in all environments.

---

## Change Log

| Date       | Version | Description                            | Author          |
| ---------- | ------- | -------------------------------------- | --------------- |
| 2024-01-15 | 0.94.0  | Initial architecture foundation        | Architect Agent |
| 2025-09-14 | 0.96.0  | Major update: PRD v0.96.0 enhancements | Architect Agent |

---

## Vision Alignment

**Platform vision:** Empower global families to manage group expenses, savings, and allowances with secure onboarding, robust roles, real-time insights, gamified education, subscription options, and extensibility for calendar and multi-currency travel use cases.

Key drivers:
- Deep localization (multi-language, multi-currency)
- Modular extensibility (bank APIs, calendars)
- Real-time and scheduled financial views
- Family-friendly RWD/mobile-first UX
---

## High-Level Architecture

### Overview Diagram

*See updated system and processing flow diagrams in attached files v0.94.1 and v0.94.2. These are extended in this revision for calendar- and currency-related modules.*

- Modular monolith (Next.js + Node.js/NestJS; monorepo)
- API-first (REST+OpenAPI); interfaces for every data and external service
- PostgreSQL (primary relational data), MongoDB (gamification/events), Redis (caching/notifications)
- AWS cloud-native, Dockerized micro-deployments, Terraform IaC


---

### Component Map

- **Web client:** Next.js (SSR+SPA; RWD; i18n; App Router)
- **Mobile client:** React Native (future)
- **API Gateway:** Routing, auth filters, API versioning
- **Core backend services (NestJS modular):**
  - **Auth & Role Service:** SSO, JWT, 2FA, RBAC
  - **Expense Service:** CRUD, scheduling, recurring rules
  - **Family/Group Service:** Invite, roles, dashboard, QR
  - **Bank Integration Service:** Plaid/Tink/TrueLayer adapters
  - **Goals & Savings Service:** Goal CRUD, shared funds
  - **Allowances & Chores Service:** Schedules, rewards
  - **Gamification Service:** Badges, streaks (MongoDB)
  - **Notification Service:** Push/email/SMS, cross-device
  - **Calendar & Scheduling Service** (**NEW**): Calendar UI, expense/income booking, recurring event logic, custom periods, notifications, i18n calendar formats
  - **Multi-Currency & Exchange Service** (**NEW**): Currency management, FX rates, travel mode, conversion, multi-currency CRUD, budget allocation
- **Data storage:** PostgreSQL (main), MongoDB (gamification), Redis (cache, sessions)
- **External APIs:**
  - Banking: Plaid, Tink, TrueLayer, SaltEdge, others
  - Currency rates: OpenExchangeRates/ECB
  - Payments: Stripe, PayPal
- **Infrastructure:** AWS EC2, RDS, S3, CloudFront, Lambda


---

## Technology Stack

| Category             | Tech          | Version    | Purpose                    | Rationale                      |
| -------------------- | ------------- | ---------- | -------------------------- | ------------------------------ |
| Frontend Framework   | Next.js       | 14.0.0     | React+SSR+App Router       | Speed, SEO, i18n               |
| UI Library           | React         | 18.2.0     | Component/UI               | Ecosystem, RWD                 |
| State Mgmt (FE)      | Context, SWR  | n/a        | Data caching/consistency   | SSR+SPA sync, simplicity       |
| Styling              | Tailwind CSS  | 3.3.0      | RWD, design system         | Atomic, mobile-first           |
| i18n (FE/BE)         | next-i18next  | 13.0.0     | Multi-language             | SSR compatible                 |
| Backend Framework    | NestJS        | 10.0.0     | Modular APIs               | TypeScript, scalability        |
| Auth                 | JWT, bcrypt   | JWT9, bc12 | Secure sessions, RBAC, 2FA | Scalable, secure               |
| ORM                  | Prisma        | 5.0.0      | DB management, migrations  | Type-safe, performant          |
| Database             | PostgreSQL    | 15.0       | Main data                  | ACID, JSON support             |
| Gamification Storage | MongoDB       | 7.0.0      | NoSQL (badges, events)     | Event streams, flexible schema |
| Caching              | Redis         | 7.0.0      | Sessions, notifications    | Low-latency, pub/sub           |
| Bank APIs            | Plaid, Tink   | Vary       | FI connectivity            | Global/EU, secure, compliant   |
| FX Rates             | OXR/ECB       | Vary       | FX rate API                | Real-time/cached rates         |
| Payment Gateway      | Stripe,PayPal | Current    | Subscriptions              | Multi-channel                  |
| IaC                  | Terraform     | 1.5.0      | Cloud deployment           | Modular, IaC best practice     |
| CI/CD                | GitHub CI     | -          | Test+deploy automation     | Workflow flexibility           |

---

## Domain Data Models (Incremental: see previous for base, below are new/changed in v0.96.0)

### CalendarEvent Model
- **id:** UUID
- **family_id:** UUID (rel: family)
- **title:** string
- **description:** string
- **type:** enum (expense/income/goal/allowance/other)
- **start_date:** datetime
- **end_date:** datetime
- **recurrence:** JSON (schedule details)
- **currency:** string
- **amount:** decimal (optional, for expense/income)
- **created_by:** user_id

### CurrencyAccount Model
- **id:** UUID
- **family_id:** UUID
- **currency:** string (3-letter code)
- **primary:** boolean
- **accounts:** JSON (list of accounts, balances)

### FXRateHistory Model
- **id:** UUID
- **base_currency:** string
- **target_currency:** string
- **rate:** decimal
- **date:** datetime

### Key Model/Schema Adaptations
- **Expense:** currency, amount; now supports multiple currencies, automatic FX conversion, travel tags
- **Family:** default_currency, multi-currency profile, travel flags
- **Goal:** currency; can be cross-currency

---

## Component Responsibilities & Key Interfaces (by Epic)

- **Account onboarding, Authentication, Group Management (Epics 0-2):**
  - Registration, login, social auth, 2FA, roles, group creation, invites (QR+, multi-channel)
- **Expense Management (Epic 3):**
  - CRUD, recurring, hybrid sync, manual fallback, multi-currency selection, real-time personal/family balance views
- **Goals & Savings (Epic 4):**
  - Family goals, progress, shared contributions, multi-currency compatibility
- **Allowances & Chores (Epic 5):**
  - Scheduled allowances, linked chores, reward flow, notifications
- **Gamification & Education (Epic 6):**
  - Savings gamification, badge engines, literacy hub, multi-language
- **Notifications & Parental Controls (Epic 7):**
  - Real-time, role-aware notifications, anomaly detection, approval flows
- **Multi-language & RWD (Epic 8):**
  - Centralized i18n, language switcher, RWD on all screens, RTL-ready
- **Pricing & Subscription (Epic 9):**
  - Free/paid tier logic, group-based billing, payment provider integration
- **Feedback & Support (Epic 10):**
  - Persistent floating feedback UI, centralized ticket creation/logging
- **Calendar & Scheduling (Epic 11, NEW):**
  - Multi-view calendar, expense/income/event booking, recurring scheduler, custom periods, i18n date formats, notification triggers
- **Multi-Currency & Exchange Management (Epic 12, NEW):**
  - Multi-currency account setup, FX rate feeds, travel mode, currency converter, budget allocation/reporting, currency-formatting/locale support

---

## Processing and Dependency Flows

- See updated attachment for sequence and block diagrams (v0.94.1, v0.94.2, v0.94.3)
- Calendars now subscribe to event/expense/goal/allowance schedules
- Currency layer transparently integrates with every expense/goal/allowance via hooks/service decorators
- Bank integration supports currency-detection, locale-sensitive category assignment
- All event-driven flows (notifications, recurring) centralize on calendar and currency triggers

---

## Infrastructure, DevOps & Security

**Infra:** AWS IaC (Terraform), blue-green deployment, rollback automation
**CI/CD:** GitHub Actions, full test matrix, staged promotion, security scanning (Snyk, Semgrep, ZAP)
**Env:** Dev/staging/prod, encrypted secrets (KMS, .env), global region coverage

**Security:**
- 2FA, RBAC, OAuth, JWT session rotation
- Rate limits, CORS, helmet, XSS/CSRF prevention
- PCI/GDPR/CCPA/PSD2 alignment for banking and payments
- FX rates/PII all encrypted at rest and in transit
- Language/currency/personal data pseudonymization where possible
- Monitoring: logging (Winston), distributed tracing, error reporting, alerting

---

## Error Handling & Test Strategy

- Layered (HTTP code, JSON error, custom exception hierarchies)
- Localized error dictionaries (all supported languages)
- Retry, circuit breaker, and fallback logic for all external APIs
- Transactional integrity; distributed Saga for cross-module, idempotency keys

**Testing:**
- TDD, >80% coverage, Playwright (E2E), Jest (unit/integration), Testcontainers (Postgres), OWASP ZAP+Lighthouse (sec, perf)
- All new calendar/currency features with scenario and edge case coverage

---

## Code & Implementation Standards

- TypeScript 5 everywhere, strict typing
- ESLint+Prettier; enforce style and import rules
- All new DB logic via Prisma, no raw SQL unless required
- All number/math involving currency via Decimal.js
- All UI/UX strings wrapped in i18n
- All errorable logic covered by automated tests
- All build/deploy via mono-repo scripts, Docker

---

## Source Tree, Modules, and API Spec

- See previous (v0.94.0) for monorepo structure; all new services/modules as above
- OpenAPI 3.0 spec extended in-place; all new endpoints for calendar, currency, etc. under /calendar, /currency

---

## Next Steps

1. Initiate updated Frontend Architecture (v0.96.0) with new modules and state mgmt for calendar/currency flows
2. Sync Jira/backlog structure to new Epic/Story/MVP sequence
3. Begin implementation stories for Epic 11, 12 after MVP core
4. Validate all test and infra setup for new modules
5. Continuous review and feedback per epic/sprint

---

This document supersedes v0.94.0 and provides the foundation for all architecture, design, and implementation work through release 0.96.0.