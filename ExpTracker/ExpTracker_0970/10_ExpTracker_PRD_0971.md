### **Product Requirements Document (PRD) – Family Expense Tracker**

**Version:** 0.97.1

### **🎯 Vision**

The Family Expense Tracker is a family-first financial management platform that enables households to:

- Navigate through intuitive primary sections: Home, Overview, Payment, Chat, and My Center
- Manage both shared Funds (group expenses) and individual Wallets (personal tracking)
- Communicate seamlessly through integrated chat functionality similar to Line messenger
- Categorize all income and expenditures with comprehensive classification systems
- Personalize experience with dark mode, themes, and visual customization
- Securely onboard and manage family groups with multi-language support
- Track expenses, allowances, savings goals, and individual balances
- Schedule and manage financial activities through comprehensive calendar functionality
- Support multi-currency transactions and exchange management for traveling families
- Encourage financial literacy through gamification and education
- Provide multi-language and responsive support for a global audience
- Offer flexible subscription plans to sustain long-term growth
- Collect user feedback seamlessly to drive continuous improvement

### **📱 Navigation Structure**

**Primary Navigation Buttons:**
1. **Home** - Personalized dashboard with customizable Fund/Wallet blocks
2. **Overview** - Complete view of all Funds and Wallets with management capabilities
3. **Payment** - Expense/income tracking, bank sync, and transaction management
4. **Chat** - Group communication system with text and voice messaging
5. **My Center** - User profile, settings, preferences, and account management

### **🗂 Epics & Stories by Navigation Category**

---

## **🏠 HOME NAVIGATION EPICS**

### **🚀 Epic 0: Account Creation & Onboarding (High Priority)**

**Goal:** Provide a smooth and multilingual onboarding experience.

- **Story 0.1 – Account Creation Page:** Create a form for new users to enter their name, select a persona, and set a group name.
    - **UX Criteria:** Complete setup in <3 minutes; 95% success rate on mobile (Sprint 1 alignment).
- **Story 0.2 – Host/Owner Definition:** Designate the group creator as the manager/owner of the family group with administrative permissions.
- **Story 0.3 – Add Members Placeholder:** Implement a visual "+ Add Member" button or option on the onboarding screen to indicate where members will be added later.
- **Story 0.4 – Current Member Display:** Create a list to display members who have joined and include an "all joined" checkbox for the host to confirm completion.
- **Story 0.5 – Multi-language onboarding labels:** Ensure all text, placeholders, and buttons on the onboarding pages support the defined languages (EN, ZH-TW, ZH-CN, JA, ES).
    - **UX Criteria:** Localized errors with <2-click recovery (error resilience priority).
- **Story 0.6 – RWD onboarding page:** Implement a responsive web design so the onboarding process works seamlessly on mobile, tablet, and desktop devices.

### **🎨 Epic 13: Personalization & Theme System**

**Goal:** Enhance visual appeal and engagement through customization options.

- **Story 13.1 – Dark Mode Implementation:** Build system-wide dark theme with automatic/manual switching.
- **Story 13.2 – Theme Selection:** Create multiple color themes with preview and application functionality.
- **Story 13.3 – Style Customization:** Allow customization of UI elements (colors, fonts, spacing) for child engagement.
- **Story 13.4 – Home Screen Layout Memory:** Save user's home screen Fund/Wallet arrangement preferences.
- **Story 13.5 – RWD Theme Compatibility:** Ensure all themes work seamlessly across mobile, tablet, and desktop.

### **🧩 Epic 14: Home Screen Fund/Wallet Management**

**Goal:** Enable personalized home screen with customizable financial blocks.

- **Story 14.1 – Fund/Wallet Block System:** Create draggable, customizable blocks for Home screen organization.
- **Story 14.2 – Copy/Paste Between Overview-Home:** Implement functionality to move blocks between Overview and Home screens.
- **Story 14.3 – Drag & Drop Rearrangement:** Enable long-press and move functionality for block positioning.
- **Story 14.4 – Block Deletion Management:** Allow removal of blocks from Home screen without deleting from system.
- **Story 14.5 – Default Home Layouts:** Provide curated default layouts for different user roles and preferences.

---

## **📊 OVERVIEW NAVIGATION EPICS**

### **💼 Epic 15: Fund Management System**

**Goal:** Manage shared family funds for specific purposes.

- **Story 15.1 – Fund Creation:** Build interface to create shared Funds (Dinner Fund, Trip Fund, Party Fund, etc.).
- **Story 15.2 – Fund Contribution Tracking:** Implement system to track contributions to shared Funds.
- **Story 15.3 – Fund Usage Monitoring:** Create visibility into Fund expenditures and remaining balances.
- **Story 15.4 – Fund Transfer System:** Enable moving money between Funds and individual Wallets.
- **Story 15.5 – Fund History & Reporting:** Generate historical reports on Fund activity and performance.

### **👛 Epic 16: Wallet Management System**

**Goal:** Manage individual financial tracking envelopes.

- **Story 16.1 – Wallet Creation:** Build interface to create personal Wallets (Travel Wallet, Food Wallet, Education Envelope, etc.).
- **Story 16.2 – Wallet Allocation System:** Implement personal budget allocation to different Wallets.
- **Story 16.3 – Wallet Transfer Facility:** Enable moving funds between different personal Wallets.
- **Story 16.4 – Wallet Spending Tracking:** Track expenditures against specific Wallet allocations.
- **Story 16.5 – Wallet Balance Alerts:** Create notifications for low Wallet balances or overspending.

### **📈 Epic 2: Group Management & Dashboard (High Priority)**

**Goal:** Provide role-based group management and dashboard access.

- **Story 2.1 – Family Dashboard:** Create a main dashboard view that summarizes family financial activity, localized for each user.
    - **UX Criteria:** <2 clicks to core tasks per role (e.g., parents: expense overview; kids: chores) (role efficiency).
- **Story 2.2 – Role-Based Permissions:** Define and implement the specific capabilities and data visibility for each role (Parent, Partner, Teen, Child).
- **Story 2.3 – Group Creation & Setup:** Build the workflow for a host to create a group and generate localized invitation text.
- **Story 2.4 – QR Invite Auto-Fill:** Generate a QR code for the group invite; scanning it should auto-populate the invite code for a new user.
- **Story 2.5 – Invite Preview Modal:** Create a modal dialog that displays a preview of the invite, optimized for screenshotting or printing.
- **Story 2.6 – Multi-Channel Invite Sharing:** Implement functionality to share the group invite via Email, Copy Link, WhatsApp, Telegram, and QR Code download.
- **Story 2.7 – RWD dashboard and group UI:** Ensure the dashboard and all group management interfaces are responsive.

---

## **💳 PAYMENT NAVIGATION EPICS**

### **🏦 Epic 3: Core Expense Management (Hybrid Bank Sync Included)**

**Goal:** Enable universal yet localized expense and budget management.

- **Story 3.1 – Expense CRUD:** Build the core functionality to Create, Read, Update, and Delete expense entries.
- **Story 3.2 – Recurring Expense Scheduling:** Implement a system to define and automatically create repeating expenses.
- **Story 3.3 – Budget Alerts:** Create a system to define budget limits and trigger notifications when they are approached or exceeded.
    - **UX Criteria:** Non-technical, localized alerts with 95% mobile viewability (error resilience & global accessibility).
- **Story 3.4 – Hybrid Bank Account Sync Strategy:** Develop a global bank synchronization feature.
    - Single global landing page (`/bank-sync`).
    - Dynamic filtering of supported banks by user region.
    - Localized error codes and messages (EN, ZH-TW, ZH-CN, JA, ES).
    - Display compliance disclaimers (e.g., PSD2, Open Banking, RBI).
    - Integrate with scalable API providers (e.g., Plaid, Tink, Truelayer, SaltEdge).
    - Provide a fallback to manual expense entry for unsupported banks.
    - **UX Criteria:** <2-click error recovery; fallback flow in <1 min (error resilience priority, Sprint 3).
- **Story 3.5 – RWD expenses & bank sync UI:** Ensure all expense tracking and bank syncing interfaces are responsive.
- **Story 3.6 – Monthly Personal Balance View:**
    - As a family member, I want to see my personal running balance for the current month, so I can understand my net income vs. spending.
    - **Acceptance Criteria:**
        - Balance is calculated as: (Allowances received + Contributions from others) - (Personal expenses + Contributions to others/goals).
        - Balance is displayed prominently on the user's dashboard and expense views.
        - Balance updates instantly when any related transaction is logged.
        - Supports multi-currency formatting based on user's locale.
    - **UX Criteria:** Instant on-screen confirmation toast; <2s refresh (feedback loop & role efficiency).

### **📋 Epic 17: Comprehensive Categorization System**

**Goal:** Implement detailed income and expenditure categorization.

- **Story 17.1 – Income Categories Setup:** Create system for income classification (Salary/Wages, Business Income, Investment Returns, Government Benefits, Gifts, etc.).
- **Story 17.2 – Expenditure Categories Setup:** Build expenditure classification (Housing, Food & Groceries, Transportation, Healthcare, Personal & Family Care, etc.).
- **Story 17.3 – Custom Category Creation:** Allow users to create custom categories beyond predefined options.
- **Story 17.4 – Category-Based Reporting:** Generate reports filtered by specific categories.
- **Story 17.5 – Multi-language Category Support:** Ensure all category names are properly localized.

### **💰 Epic 4: Goals & Savings**

**Goal:** Help families define and track savings goals.

- **Story 4.1 – Create Family Goal:** Build a form to define a new savings goal with a target amount and deadline.
- **Story 4.2 – Track Goal Progress:** Implement a visual progress bar to show how much has been saved towards each goal.
- **Story 4.3 – Shared Contributions:** Enable multiple family members to contribute funds towards a shared goal.
- **Story 4.4 – Localized goal setup & progress messages:** Translate all goal-related text and notifications.
- **Story 4.5 – RWD goal dashboard:** Ensure the goals and savings interface is responsive.

### **🧹 Epic 5: Allowances & Chores**

**Goal:** Automate allowances and link chores to financial rewards.

- **Story 5.1 – Chore Assignment:** Create a system for parents to assign chores to children with due dates and values.
- **Story 5.2 – Allowance Automation:** Implement a feature to automatically distribute allowances on a scheduled basis.
- **Story 5.3 – Chore Completion → Rewards:** Build a workflow where marking a chore as complete triggers the automatic payment of the allowance to the child.
- **Story 5.4 – Localized tasks & reminders:** Translate all chore and allowance-related text and notifications.
- **Story 5.5 – RWD chores & allowance lists:** Ensure the chores and allowances interface is responsive.

### **📅 Epic 11: Calendar & Scheduling**

**Goal:** Provide comprehensive calendar functionality for booking and tracking financial activities across different time periods.

- **Story 11.1 – Calendar Integration:** Build a calendar interface that supports daily, weekly, monthly, and yearly views for expense and income planning.
    - **UX Criteria:** Calendar loads in <1.5s; intuitive navigation between views with <2 clicks (role efficiency).
- **Story 11.2 – Custom Period Selection:** Implement a date range picker that allows users to select any chosen period of days for booking expenditures or incomes.
    - **Acceptance Criteria:** 
        - Users can select start and end dates using a date picker.
        - Calendar displays all financial activities within the selected period.
        - Period selection supports up to 365 days range.
- **Story 11.3 – Expense/Income Booking:** Enable users to schedule future expenses and incomes directly from the calendar interface.
    - **UX Criteria:** Booking process completes in <2 minutes; instant visual confirmation on calendar (feedback loop).
- **Story 11.4 – Recurring Event Management:** Implement functionality to create, edit, and manage recurring financial events (weekly allowances, monthly bills, etc.).
- **Story 11.5 – Calendar Notifications:** Build notification system for upcoming scheduled expenses, due dates, and financial milestones.
- **Story 11.6 – Multi-language Calendar:** Ensure all calendar labels, date formats, and notifications support the defined languages (EN, ZH-TW, ZH-CN, JA, ES).
    - **Acceptance Criteria:**
        - Date formats adapt to locale conventions (MM/DD/YYYY vs DD/MM/YYYY vs YYYY/MM/DD).
        - Month and day names display in user's selected language.
- **Story 11.7 – RWD Calendar Interface:** Ensure the calendar interface is fully responsive across mobile, tablet, and desktop devices.
    - **UX Criteria:** Touch-friendly controls on mobile; no horizontal scrolling required (mobile optimization).

### **💱 Epic 12: Multi-Currency & Exchange Management**

**Goal:** Support multi-currency transactions and real-time exchange rate management for traveling families.

- **Story 12.1 – Multi-Currency Account Setup:** Enable families to add and manage multiple currencies within their account.
    - **Acceptance Criteria:**
        - Support for 50+ major world currencies.
        - Primary currency selection with secondary currency support.
        - Currency symbols and formatting based on locale.
- **Story 12.2 – Real-Time Exchange Rates:** Integrate with currency exchange APIs to provide real-time conversion rates.
    - **UX Criteria:** Exchange rates update every 15 minutes; rates display with <1s load time (real-time data efficiency).
- **Story 12.3 – Travel Mode:** Create a specialized travel interface for families planning multi-country trips.
    - **Acceptance Criteria:**
        - Pre-trip currency planning tools.
        - Country-specific expense categories.
        - Travel itinerary integration with currency needs.
- **Story 12.4 – Multi-Currency Expense Entry:** Allow users to log expenses in any supported currency with automatic conversion to primary currency.
    - **UX Criteria:** Currency selection in <3 taps; automatic conversion display within 1s (role efficiency).
- **Story 12.5 – Exchange Rate History:** Maintain historical exchange rate data for accurate financial reporting and analysis.
- **Story 12.6 – Currency Conversion Calculator:** Build an integrated calculator for quick currency conversions within the app.
- **Story 12.7 – Travel Budget Allocation:** Enable families to allocate budgets by country/currency for trip planning.
    - **Acceptance Criteria:**
        - Budget allocation by destination currency.
        - Real-time spending tracking against allocated budgets.
        - Alerts when approaching currency-specific budget limits.
- **Story 12.8 – Multi-Currency Reporting:** Generate financial reports that support multi-currency analysis and consolidated views.
- **Story 12.9 – Localized Currency Support:** Ensure currency names, symbols, and formatting follow international standards and user locale preferences.
- **Story 12.10 – RWD Currency Interface:** Ensure all currency management interfaces are responsive and optimized for mobile use during travel.

### **💳 Epic 9: Pricing & Subscription**

**Goal:** Monetize with flexible, family-friendly pricing options.

- **Story 9.1 – Free Tier:** Implement a free forever plan for users aged 18 and under.
- **Story 9.2 – Free Trial:** Offer a 3-month free trial for all new adult users.
- **Story 9.3 – Monthly Subscription Plan:** Create a monthly paid subscription option.
- **Story 9.4 – Yearly Subscription Plan:** Create a discounted yearly paid subscription option.
- **Story 9.5 – Group/Family Subscription Pricing:** Implement pricing logic that applies to entire family groups.
- **Story 9.6 – Discount Framework:** Build the backend infrastructure to support promotional discounts and offers (specific offers TBD).
- **Story 9.7 – Payment Methods:** Integrate payment providers to support credit/debit cards, PayPal, Apple Pay, and Google Pay.
- **Story 9.8 – Localized pricing page:** Ensure the pricing page is translated and displays local currencies.
- **Story 9.9 – RWD pricing page:** Ensure the pricing page is responsive.

---

## **💬 CHAT NAVIGATION EPICS**

### **📞 Epic 18: Line-like Messaging System**

**Goal:** Provide comprehensive chat functionality similar to Line messenger.

- **Story 18.1 – Text Messaging Core:** Build real-time text chat with read receipts and typing indicators.
- **Story 18.2 – Voice Message System:** Implement voice recording and playback functionality.
- **Story 18.3 – Group Chat Management:** Create system for family group conversations and sub-groups.
- **Story 18.4 – Media Sharing:** Enable photo, video, and document sharing within chats.
- **Story 18.5 – Chat History & Search:** Maintain chat history with search functionality.
- **Story 18.6 – Sticker & Emoji Integration:** Implement sticker packs and emoji reactions.
- **Story 18.7 – Notification Management:** Build customizable chat notifications.
- **Story 18.8 – Multi-language Chat Interface:** Ensure chat UI supports all defined languages.
- **Story 18.9 – RWD Chat Interface:** Ensure responsive chat across all devices.

### **📝 Epic 10: Feedback & Customer Support**

**Goal:** Provide users with a seamless, low-friction way to give feedback and get help.

- **Story 10.1 – Instant Feedback Floating Button:**
    - As a user, I want a small, always-accessible button on my screen to provide feedback or get help, so I don't have to navigate to a separate help section.
    - **Acceptance Criteria:**
        - A subtle, floating button (e.g., chat icon) is present on all authenticated pages.
        - The button is responsive and does not obstruct critical UI elements.
        - Clicking the button opens a modal pop-up with a feedback form.
        - The form includes fields for: Feedback type (Bug, Suggestion, Question), Message, and optional contact email.
        - The form and its labels are localized to the user's current language.
- **Story 10.2 – Feedback Integration & Management:**
    - As a product manager, I want all user feedback to be logged in a central system, so I can prioritize issues and improvements.
    - **Acceptance Criteria:**
        - Submitted feedback is sent to a dedicated channel (e.g., Slack, Email, Jira, a dedicated database table).
        - Feedback tickets are tagged with user metadata (e.g., user ID, group ID, browser, locale) for context.
        - The user receives an on-screen confirmation that their feedback was sent successfully.

---

## **👤 MY CENTER NAVIGATION EPICS**

### **🔐 Epic 1: Authentication & Security (High Priority)**

**Goal:** Enable secure access with localized messages.

- **Story 1.1 – Secure Login:** Build a login form that accepts email and password.
- **Story 1.2 – Social Login:** Integrate OAuth authentication with Google, Facebook, and X (Twitter).
- **Story 1.3 – Two-Factor Authentication:** Implement a 6-digit verification code system sent via email or SMS.
- **Story 1.4 – Role-Based Permissions Middleware:** Develop server-side logic to enforce access controls based on user roles (Parent, Partner, Teen, Child).
    - **UX Criteria:** Role-tailored views load in <2s, with instant confirmation (role efficiency & feedback loop).
- **Story 1.5 – Localized login/registration messages:** Translate all authentication-related messages, errors, and success notifications.
- **Story 1.6 – RWD login and authentication pages:** Ensure all auth pages (login, register, forgot password) are fully responsive.

### **🌍 Epic 8: Multi-Language & RWD (System-Wide)**

**Goal:** Ensure global usability with localization and responsive design.

- **Story 8.1 – Language Support:** Implement full language support for English (EN), Traditional Chinese (ZH-TW), Simplified Chinese (ZH-CN), Japanese (JA), and Spanish (ES).
- **Story 8.2 – Language Switcher:** Build a user interface element to easily switch between languages.
- **Story 8.3 – Auto-detect language:** Implement logic to automatically set the app's language based on the user's browser or device settings.
- **Story 8.4 – Responsive Web Design:** Apply responsive design principles across all application screens and components.
- **Story 8.5 – Centralized i18n library:** Structure all translatable strings in a centralized internationalization library for easy management.
- **Story 8.6 – RTL/LTR support:** Build the application with a structure that supports both Left-To-Right and Right-To-Left languages for future expansion.

### **🎮 Epic 6: Gamification & Education**

**Goal:** Engage younger users with fun and educational tools.

- **Story 6.1 – Gamified Savings Tracker:** Create a visually engaging and game-like interface for children to track their savings progress.
- **Story 6.2 – Badges & Achievements:** Implement a system of rewards and badges for completing financial tasks or reaching milestones.
- **Story 6.3 – Financial Literacy Hub:** Build a section with articles, quizzes, and tips about money management, tailored for different age groups.
- **Story 6.4 – Multi-language content support:** Ensure all educational content is available in the supported languages.
- **Story 6.5 – RWD gamification UI:** Ensure the gamification and education hub is responsive.

### **🔔 Epic 7: Advanced Notifications & Controls**

**Goal:** Provide parental controls and cross-device notifications.

- **Story 7.1 – Push Notifications:** Implement system for push notifications for budget alerts, chore reminders, and goal updates.
- **Story 7.2 – Unusual Spending Alerts:** Create algorithms to detect and alert parents of spending that falls outside a user's typical pattern.
- **Story 7.3 – Parental Controls:** Build a feature for parents to approve or reject expenses made by children.
- **Story 7.4 – Data Security & Compliance:** Ensure the application meets data protection standards like GDPR and CCPA.
- **Story 7.5 – Localized notifications:** Translate all notification content.
- **Story 7.6 – RWD notification banners:** Ensure notification displays are responsive.

---

### **🆕 Changes in Version 0.97.1**

- **Complete Content Merge:** Successfully merged all content from both v0.96.0 and v0.97.0
- **Preserved Detailed Criteria:** Maintained all UX criteria, acceptance criteria, and detailed requirements from v0.96.0
- **New Navigation Structure:** Implemented primary navigation buttons: Home, Overview, Payment, Chat, My Center
- **New Fund/Wallet System:** Added distinction between shared "Funds" and individual "Wallets" with management capabilities
- **New Chat System:** Added comprehensive messaging system similar to Line with text and voice capabilities
- **Enhanced Categorization:** Added detailed income and expenditure categories with customization options
- **New Personalization Features:** Implemented dark mode, theme selection, and style customization
- **Reorganized Epics:** All epics and stories categorized according to new navigation structure
- **New Epics Added:** Epic 13 (Personalization), Epic 14 (Home Screen Management), Epic 15 (Fund Management), Epic 16 (Wallet Management), Epic 17 (Categorization System), Epic 18 (Chat System)
- **Enhanced UX Criteria:** Preserved detailed UX success metrics and criteria from v0.96.0
- Version increment from 0.97.0 to 0.97.1

### **📊 Release Roadmap (v0.97.1)**

- **Sprint 1** → Epic 0, Epic 1, Epic 2 (MVP Onboarding + QR Invites + Authentication)
- **Sprint 2** → Epic 8, Epic 13 (Multi-language + RWD + Personalization foundation)
- **Sprint 3** → Epic 3, Epic 17 (Core Expenses + Hybrid Bank Sync + Categorization)
- **Sprint 4** → Epic 14, Epic 15, Epic 16 (Home Screen + Fund/Wallet Management)
- **Sprint 5** → Epic 9 (Pricing & Subscription MVP)
- **Sprint 6** → Epic 4, Epic 5 (Goals & Savings + Allowances & Chores)
- **Sprint 7** → Epic 6, Epic 7 (Gamification & Education + Notifications & Controls)
- **Sprint 8** → Epic 10, Epic 18 (Feedback & Customer Support + Chat System)
- **Sprint 9** → Epic 11 (Calendar & Scheduling)
- **Sprint 10** → Epic 12 (Multi-Currency & Exchange Management)