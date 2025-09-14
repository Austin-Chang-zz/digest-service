****
---

### **Product Requirements Document (PRD) – Family Expense Tracker**

**Version:** 0.94.0

### **🎯 Vision**

The Family Expense Tracker is a family-first financial management platform that enables households to:

*   Securely onboard and manage family groups.
*   Track expenses, allowances, savings goals, and individual balances.
*   Encourage financial literacy through gamification and education.
*   Provide multi-language and responsive support for a global audience.
*   Offer flexible subscription plans to sustain long-term growth.
*   Collect user feedback seamlessly to drive continuous improvement.

### **🗂 Epics & Stories**

#### **🚀 Epic 0: Account Creation & Onboarding (High Priority)**

**Goal:** Provide a smooth and multilingual onboarding experience.

*   **Story 0.1 – Account Creation Page:** Create a form for new users to enter their name, select a persona, and set a group name.
*   **Story 0.2 – Host/Owner Definition:** Designate the group creator as the manager/owner of the family group with administrative permissions.
*   **Story 0.3 – Add Members Placeholder:** Implement a visual "+ Add Member" button or option on the onboarding screen to indicate where members will be added later.
*   **Story 0.4 – Current Member Display:** Create a list to display members who have joined and include an "all joined" checkbox for the host to confirm completion.
*   **Story 0.5 – Multi-language onboarding labels:** Ensure all text, placeholders, and buttons on the onboarding pages support the defined languages (EN, ZH-TW, ZH-CN, JA, ES).
*   **Story 0.6 – RWD onboarding page:** Implement a responsive web design so the onboarding process works seamlessly on mobile, tablet, and desktop devices.

#### **🔐 Epic 1: Authentication & Security (High Priority)**

**Goal:** Enable secure access with localized messages.

*   **Story 1.1 – Secure Login:** Build a login form that accepts email and password.
*   **Story 1.2 – Social Login:** Integrate OAuth authentication with Google, Facebook, and X (Twitter).
*   **Story 1.3 – Two-Factor Authentication:** Implement a 6-digit verification code system sent via email or SMS.
*   **Story 1.4 – Role-Based Permissions Middleware:** Develop server-side logic to enforce access controls based on user roles (Parent, Partner, Teen, Child).
*   **Story 1.5 – Localized login/registration messages:** Translate all authentication-related messages, errors, and success notifications.
*   **Story 1.6 – RWD login and authentication pages:** Ensure all auth pages (login, register, forgot password) are fully responsive.

#### **👥 Epic 2: Group Management & Dashboard (High Priority)**

**Goal:** Provide role-based group management and dashboard access.

*   **Story 2.1 – Family Dashboard:** Create a main dashboard view that summarizes family financial activity, localized for each user.
*   **Story 2.2 – Role-Based Permissions:** Define and implement the specific capabilities and data visibility for each role (Parent, Partner, Teen, Child).
*   **Story 2.3 – Group Creation & Setup:** Build the workflow for a host to create a group and generate localized invitation text.
*   **Story 2.4 – QR Invite Auto-Fill:** Generate a QR code for the group invite; scanning it should auto-populate the invite code for a new user.
*   **Story 2.5 – Invite Preview Modal:** Create a modal dialog that displays a preview of the invite, optimized for screenshotting or printing.
*   **Story 2.6 – Multi-Channel Invite Sharing:** Implement functionality to share the group invite via Email, Copy Link, WhatsApp, Telegram, and QR Code download.
*   **Story 2.7 – RWD dashboard and group UI:** Ensure the dashboard and all group management interfaces are responsive.

#### **🏦 Epic 3: Core Expense Management (Hybrid Bank Sync Included)**

**Goal:** Enable universal yet localized expense and budget management.

*   **Story 3.1 – Expense CRUD:** Build the core functionality to Create, Read, Update, and Delete expense entries.
*   **Story 3.2 – Recurring Expense Scheduling:** Implement a system to define and automatically create repeating expenses.
*   **Story 3.3 – Budget Alerts:** Create a system to define budget limits and trigger notifications when they are approached or exceeded.
*   **Story 3.4 – Hybrid Bank Account Sync Strategy:** Develop a global bank synchronization feature.
    *   Single global landing page (`/bank-sync`).
    *   Dynamic filtering of supported banks by user region.
    *   Localized error codes and messages (EN, ZH-TW, ZH-CN, JA, ES).
    *   Display compliance disclaimers (e.g., PSD2, Open Banking, RBI).
    *   Integrate with scalable API providers (e.g., Plaid, Tink, Truelayer, SaltEdge).
    *   Provide a fallback to manual expense entry for unsupported banks.
*   **Story 3.5 – RWD expenses & bank sync UI:** Ensure all expense tracking and bank syncing interfaces are responsive.
*   **Story 3.6 – Monthly Personal Balance View:**
    *   As a family member, I want to see my personal running balance for the current month, so I can understand my net income vs. spending.
    *   **Acceptance Criteria:**
        *   Balance is calculated as: (Allowances received + Contributions from others) - (Personal expenses + Contributions to others/goals).
        *   Balance is displayed prominently on the user's dashboard and expense views.
        *   Balance updates instantly when any related transaction is logged.
        *   Supports multi-currency formatting based on user's locale.

#### **💰 Epic 4: Goals & Savings**

**Goal:** Help families define and track savings goals.

*   **Story 4.1 – Create Family Goal:** Build a form to define a new savings goal with a target amount and deadline.
*   **Story 4.2 – Track Goal Progress:** Implement a visual progress bar to show how much has been saved towards each goal.
*   **Story 4.3 – Shared Contributions:** Enable multiple family members to contribute funds towards a shared goal.
*   **Story 4.4 – Localized goal setup & progress messages:** Translate all goal-related text and notifications.
*   **Story 4.5 – RWD goal dashboard:** Ensure the goals and savings interface is responsive.

#### **🧹 Epic 5: Allowances & Chores**

**Goal:** Automate allowances and link chores to financial rewards.

*   **Story 5.1 – Chore Assignment:** Create a system for parents to assign chores to children with due dates and values.
*   **Story 5.2 – Allowance Automation:** Implement a feature to automatically distribute allowances on a scheduled basis.
*   **Story 5.3 – Chore Completion → Rewards:** Build a workflow where marking a chore as complete triggers the automatic payment of the allowance to the child.
*   **Story 5.4 – Localized tasks & reminders:** Translate all chore and allowance-related text and notifications.
*   **Story 5.5 – RWD chores & allowance lists:** Ensure the chores and allowances interface is responsive.

#### **🎮 Epic 6: Gamification & Education**

**Goal:** Engage younger users with fun and educational tools.

*   **Story 6.1 – Gamified Savings Tracker:** Create a visually engaging and game-like interface for children to track their savings progress.
*   **Story 6.2 – Badges & Achievements:** Implement a system of rewards and badges for completing financial tasks or reaching milestones.
*   **Story 6.3 – Financial Literacy Hub:** Build a section with articles, quizzes, and tips about money management, tailored for different age groups.
*   **Story 6.4 – Multi-language content support:** Ensure all educational content is available in the supported languages.
*   **Story 6.5 – RWD gamification UI:** Ensure the gamification and education hub is responsive.

#### **🔔 Epic 7: Advanced Notifications & Controls**

**Goal:** Provide parental controls and cross-device notifications.

*   **Story 7.1 – Push Notifications:** Implement system for push notifications for budget alerts, chore reminders, and goal updates.
*   **Story 7.2 – Unusual Spending Alerts:** Create algorithms to detect and alert parents of spending that falls outside a user's typical pattern.
*   **Story 7.3 – Parental Controls:** Build a feature for parents to approve or reject expenses made by children.
*   **Story 7.4 – Data Security & Compliance:** Ensure the application meets data protection standards like GDPR and CCPA.
*   **Story 7.5 – Localized notifications:** Translate all notification content.
*   **Story 7.6 – RWD notification banners:** Ensure notification displays are responsive.

#### **🌍 Epic 8: Multi-Language & RWD (System-Wide)**

**Goal:** Ensure global usability with localization and responsive design.

*   **Story 8.1 – Language Support:** Implement full language support for English (EN), Traditional Chinese (ZH-TW), Simplified Chinese (ZH-CN), Japanese (JA), and Spanish (ES).
*   **Story 8.2 – Language Switcher:** Build a user interface element to easily switch between languages.
*   **Story 8.3 – Auto-detect language:** Implement logic to automatically set the app's language based on the user's browser or device settings.
*   **Story 8.4 – Responsive Web Design:** Apply responsive design principles across all application screens and components.
*   **Story 8.5 – Centralized i18n library:** Structure all translatable strings in a centralized internationalization library for easy management.
*   **Story 8.6 – RTL/LTR support:** Build the application with a structure that supports both Left-To-Right and Right-To-Left languages for future expansion.

#### **💳 Epic 9: Pricing & Subscription**

**Goal:** Monetize with flexible, family-friendly pricing options.

*   **Story 9.1 – Free Tier:** Implement a free forever plan for users aged 18 and under.
*   **Story 9.2 – Free Trial:** Offer a 3-month free trial for all new adult users.
*   **Story 9.3 – Monthly Subscription Plan:** Create a monthly paid subscription option.
*   **Story 9.4 – Yearly Subscription Plan:** Create a discounted yearly paid subscription option.
*   **Story 9.5 – Group/Family Subscription Pricing:** Implement pricing logic that applies to entire family groups.
*   **Story 9.6 – Discount Framework:** Build the backend infrastructure to support promotional discounts and offers (specific offers TBD).
*   **Story 9.7 – Payment Methods:** Integrate payment providers to support credit/debit cards, PayPal, Apple Pay, and Google Pay.
*   **Story 9.8 – Localized pricing page:** Ensure the pricing page is translated and displays local currencies.
*   **Story 9.9 – RWD pricing page:** Ensure the pricing page is responsive.

#### **📝 Epic 10: Feedback & Customer Support**

**Goal:** Provide users with a seamless, low-friction way to give feedback and get help.

*   **Story 10.1 – Instant Feedback Floating Button:**
    *   As a user, I want a small, always-accessible button on my screen to provide feedback or get help, so I don't have to navigate to a separate help section.
    *   **Acceptance Criteria:**
        *   A subtle, floating button (e.g., chat icon) is present on all authenticated pages.
        *   The button is responsive and does not obstruct critical UI elements.
        *   Clicking the button opens a modal pop-up with a feedback form.
        *   The form includes fields for: Feedback type (Bug, Suggestion, Question), Message, and optional contact email.
        *   The form and its labels are localized to the user's current language.
*   **Story 10.2 – Feedback Integration & Management:**
    *   As a product manager, I want all user feedback to be logged in a central system, so I can prioritize issues and improvements.
    *   **Acceptance Criteria:**
        *   Submitted feedback is sent to a dedicated channel (e.g., Slack, Email, Jira, a dedicated database table).
        *   Feedback tickets are tagged with user metadata (e.g., user ID, group ID, browser, locale) for context.
        *   The user receives an on-screen confirmation that their feedback was sent successfully.

### **🆕 Changes in Version 0.94.0**

*   Added **Story 3.6 – Monthly Personal Balance View** to Epic 3.
*   Added **Epic 10: Feedback & Customer Support** with Stories 10.1 and 10.2.
*   Updated the Vision statement to reflect new capabilities.
*   Version increment from 0.93.1 to 0.94.0.

### **📊 Release Roadmap (v0.94.0)**

*   **Sprint 1** → Epic 0, Epic 1, Epic 2 (MVP Onboarding + QR Invites).
*   **Sprint 2** → Epic 8 (Multi-language + RWD foundation).
*   **Sprint 3** → Epic 3 (Core Expenses + Hybrid Bank Sync + Story 3.6).
*   **Sprint 4** → Epic 9 (Pricing & Subscription MVP: Free Tier + Trials + Monthly/Yearly).
*   **Sprint 5** → Epic 4 (Goals & Savings).
*   **Sprint 6** → Epic 5 (Allowances & Chores).
*   **Sprint 7** → Epic 6 (Gamification & Education).
*   **Sprint 8** → Epic 7 (Notifications & Controls).
*   **Sprint 9** → Epic 10 (Feedback & Customer Support).

---