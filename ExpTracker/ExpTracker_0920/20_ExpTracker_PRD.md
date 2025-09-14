📖 Product Requirements Document (PRD) – Family Expense Tracker

Version: 0.92.0

🎯 Vision

A family-first financial app with secure onboarding, localized dashboards, and adaptive international support, enabling families to manage expenses, goals, allowances, and savings across multiple regions, languages, and banking systems.

🗂 Epics & Stories (Updated v0.92.0)
🚀 Epic 0: Account Creation & Onboarding (High Priority)

Account Creation Page (Name, Persona, Group Name).

Host / Owner Definition.

Placeholder UX (transparent hints + “+” add member).

Current Member Display.

Multi-language UI labels.

RWD support for onboarding page.

🔐 Epic 1: Authentication & Security (High Priority)

Secure Login (JWT, role claims).

Social Login (Google, Facebook, X).

Email/SMS 6-Digit Verification Code (2FA).

Role-Based Permissions Middleware.

Localized login/registration messages.

RWD support for login forms.

👥 Epic 2: Group Management & Dashboard (High Priority)

Family Dashboard (multi-language).

Role-Based Permissions.

Group Creation & Setup.

QR Invite Auto-Fill.

Invite Preview Modal.

Multi-Channel Invite Sharing.

RWD dashboard layouts.

🏦 Epic 3: Core Expense Management (Updated with Hybrid Bank Sync)

Goal: Provide universal yet localized expense management and banking connectivity.

Stories

Expense CRUD.

Recurring Expense Scheduling.

Budget Alerts.

Hybrid Bank Account Sync Strategy (NEW):

Single global landing page (/bank-sync).

Dynamic filtering of supported banks by region.

Localized error codes/messages (English, Traditional Chinese, Simplified Chinese, Japanese, Spanish).

Regional compliance disclaimers (e.g., PSD2, Open Banking, RBI).

Scalable bank integration APIs (Plaid, Tink, Truelayer, SaltEdge).

Fallback: manual expense entry if bank not supported.

RWD forms & tables for expenses and sync UI.

💰 Epic 4: Goals & Savings

Create Family Goal.

Track Goal Progress.

Shared Contributions.

Localized goal setup.

RWD goal progress dashboard.

🧹 Epic 5: Allowances & Chores

Chore Assignment.

Allowance Automation.

Chore Completion → Rewards.

Localized chore/allowance text.

RWD lists for allowances & chores.

🎮 Epic 6: Gamification & Education

Gamified Savings Tracker.

Badges & Achievements.

Financial Literacy Hub.

Localized gamification & content modules.

RWD gamification UI.

🔔 Epic 7: Advanced Notifications & Controls

Push Notifications.

Unusual Spending Alerts.

Parental Controls.

Data Security & Compliance.

Localized notifications & warnings.

RWD alert banners.

🌍 Epic 8: Multi-Language & RWD (System-wide)

Support for English, Traditional Chinese, Simplified Chinese, Japanese, Spanish.

Language Switcher.

Auto-detect device/browser language.

Responsive Web Design across all screens.

Centralized i18n library.

🆕 Changes in Version 0.92.0

Epic 3 expanded with Hybrid Bank Sync Strategy.

One global landing page.

Dynamic region filtering.

Localized messages.

Compliance-ready by region.

Strengthened dependency between Epic 3 and Epic 8 (multi-language + RWD).

📊 Updated Release Roadmap (0.92.0)

Sprint 1 → Epic 0, Epic 1, Epic 2 (Onboarding + QR Invites).

Sprint 2 → Epic 8 (i18n + RWD foundation).

Sprint 3 → Epic 3 (Core Expenses + Hybrid Bank Sync).

Sprint 4 → Epic 4 (Goals & Savings).

Sprint 5 → Epic 5 (Allowances & Chores).

Sprint 6 → Epic 6 (Gamification & Education).

Sprint 7 → Epic 7 (Notifications & Controls).