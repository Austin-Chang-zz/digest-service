📖 Product Requirements Document (PRD) – Family Expense Tracker

Version: 0.90.1 (Upgraded with Onboarding Priority)

🎯 Vision

Deliver a family-first financial app where secure onboarding, role-based dashboards, and group invites form the foundation. Families can then progressively unlock features like goals, allowances, gamification, and savings education.

🗂 Reprioritized Epics & Stories
🚀 Epic 0: Account Creation & Onboarding (NEW – High Priority)

Goal: Provide a smooth and secure entry point for users.

Stories

Account Creation Page (First Name, Last Name, Persona, Group Name).

Host / Owner Definition (assign manager of group).

Placeholder UX (transparent text, “+” to add members).

Current Member Display (list & checkbox: “all joined”).

🔐 Epic 1: Authentication & Security (Subset of Epic 6 – High Priority)

Goal: Ensure secure access and identity management from day one.

Stories

Secure Login (JWT, role claims).

Social Login Integration (Google, Facebook, X).

Email/SMS 6-Digit Verification Code (2FA).

Role-Based Permissions Middleware.

👥 Epic 2: Group Management & Dashboard (Reprioritized from old Epic 2 – High Priority)

Goal: Enable family group setup, joining, and dashboard overview.

Stories

Family Dashboard (overview of expenses, goals, allowances).

Role-Based Permissions (Parent, Partner, Teen, Child).

Group Creation & Setup (host, group scope, roles).

QR Invite Auto-Fill (scan → auto-fill group name & owner, add members).

Invite Preview Modal (invite message + QR, screenshot/print-ready).

Multi-Channel Invite Sharing (Email, Copy, WhatsApp, Telegram, Download QR).

🏦 Epic 3: Core Expense Management (Moved lower)

Goal: Enable families to track expenses and budgets.

Stories

Expense CRUD (create, read, update, delete).

Recurring Expense Scheduling.

Budget Alerts.

Bank Account Sync.

💰 Epic 4: Goals & Savings

Goal: Allow families to create, track, and contribute toward shared goals.

Stories

Create Family Goal.

Track Goal Progress.

Shared Contributions by family members.

🧹 Epic 5: Allowances & Chores

Goal: Automate allowances and assign chores linked to rewards.

Stories

Chore Assignment.

Allowance Automation.

Chore Completion → Allowance Rewards.

🎮 Epic 6: Gamification & Education

Goal: Drive engagement with gamified savings and financial literacy.

Stories

Gamified Savings Tracker.

Badges & Achievements.

Financial Literacy Hub.

🔔 Epic 7: Advanced Notifications & Controls (Remaining part of Epic 6)

Goal: Ensure family-wide visibility, alerts, and parental oversight.

Stories

Push Notifications (budgets, goals, chores).

Unusual Spending Alerts.

Parental Controls (approve/reject expenses).

Data Security & Compliance (GDPR/CCPA).

🆕 Changes in Version 0.90.1

Added Epic 0 (Account Creation & Onboarding) → covers host setup, persona, member management.

Split Epic 6 into two parts:

Epic 1: Authentication & Security → prioritized (login, 2FA, roles).

Epic 7: Advanced Notifications & Controls → lower priority.

Moved Epic 2 (Group Management & Dashboard) higher → critical for initial onboarding.

Delayed Core Expense Management (old Epic 1) until after onboarding is stable.

📊 Updated Release Roadmap (0.90.1)

Sprint 1 (MVP Onboarding) → Epic 0 (Account Creation), Epic 1 (Auth & Security), Epic 2 (Group Management basics: QR invites, Preview Modal).

Sprint 2 → Core Expense Management (Epic 3).

Sprint 3 → Goals & Savings (Epic 4).

Sprint 4 → Allowances & Chores (Epic 5).

Sprint 5 → Gamification & Education (Epic 6).

Sprint 6 → Advanced Notifications & Parental Controls (Epic 7).