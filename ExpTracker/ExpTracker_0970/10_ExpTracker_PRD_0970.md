### **Product Requirements Document (PRD) – Family Expense Tracker**

**Version:** 0.97.0

### **🎯 Vision**

The Family Expense Tracker is a family-first financial management platform that enables households to:

- Navigate through intuitive primary sections: Home, Overview, Payment, Chat, and My Center
- Manage both shared Funds (group expenses) and individual Wallets (personal tracking)
- Communicate seamlessly through integrated chat functionality similar to Line messenger
- Categorize all income and expenditures with comprehensive classification systems
- Personalize experience with dark mode, themes, and visual customization
- Securely onboard and manage family groups with multi-language support
- Track expenses, allowances, savings goals, and individual balances
- Support multi-currency transactions and exchange management
- Encourage financial literacy through gamification and education
- Provide flexible subscription plans to sustain long-term growth

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
    - **UX Criteria:** Complete setup in <3 minutes; 95% success rate on mobile.
- **Story 0.2 – Host/Owner Definition:** Designate the group creator as the manager/owner of the family group with administrative permissions.
- **Story 0.3 – Add Members Placeholder:** Implement a visual "+ Add Member" button or option on the onboarding screen.
- **Story 0.4 – Current Member Display:** Create a list to display members who have joined with "all joined" confirmation.
- **Story 0.5 – Multi-language onboarding labels:** Ensure all text supports defined languages (EN, ZH-TW, ZH-CN, JA, ES).
- **Story 0.6 – RWD onboarding page:** Implement responsive design for all devices.

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

- **Story 2.1 – Family Dashboard:** Create main dashboard view summarizing family financial activity.
- **Story 2.2 – Role-Based Permissions:** Define capabilities and data visibility for each role (Parent, Partner, Teen, Child).
- **Story 2.3 – Group Creation & Setup:** Build workflow for host to create group with localized invitations.
- **Story 2.4 – QR Invite Auto-Fill:** Generate QR codes for group invites with auto-population.
- **Story 2.5 – Invite Preview Modal:** Create optimized modal for invite screenshotting/printing.
- **Story 2.6 – Multi-Channel Invite Sharing:** Implement sharing via Email, Copy Link, WhatsApp, Telegram, QR Code.
- **Story 2.7 – RWD dashboard and group UI:** Ensure responsive design for all group management interfaces.

---

## **💳 PAYMENT NAVIGATION EPICS**

### **🏦 Epic 3: Core Expense Management (Hybrid Bank Sync Included)**

**Goal:** Enable universal yet localized expense and budget management.

- **Story 3.1 – Expense CRUD:** Build core functionality to Create, Read, Update, and Delete expense entries.
- **Story 3.2 – Recurring Expense Scheduling:** Implement system for automatically creating repeating expenses.
- **Story 3.3 – Budget Alerts:** Create system for budget limits and proximity notifications.
- **Story 3.4 – Hybrid Bank Account Sync Strategy:** Develop global bank synchronization feature.
- **Story 3.5 – RWD expenses & bank sync UI:** Ensure responsive interfaces for expense tracking.
- **Story 3.6 – Monthly Personal Balance View:** Implement personal running balance calculation and display.

### **📋 Epic 17: Comprehensive Categorization System**

**Goal:** Implement detailed income and expenditure categorization.

- **Story 17.1 – Income Categories Setup:** Create system for income classification (Salary/Wages, Business Income, Investment Returns, Government Benefits, Gifts, etc.).
- **Story 17.2 – Expenditure Categories Setup:** Build expenditure classification (Housing, Food & Groceries, Transportation, Healthcare, Personal & Family Care, etc.).
- **Story 17.3 – Custom Category Creation:** Allow users to create custom categories beyond predefined options.
- **Story 17.4 – Category-Based Reporting:** Generate reports filtered by specific categories.
- **Story 17.5 – Multi-language Category Support:** Ensure all category names are properly localized.

### **💰 Epic 4: Goals & Savings**

**Goal:** Help families define and track savings goals.

- **Story 4.1 – Create Family Goal:** Build form to define new savings goals with target amount and deadline.
- **Story 4.2 – Track Goal Progress:** Implement visual progress bar for goal achievement.
- **Story 4.3 – Shared Contributions:** Enable multiple family members to contribute to shared goals.
- **Story 4.4 – Localized goal setup & progress messages:** Translate all goal-related text.
- **Story 4.5 – RWD goal dashboard:** Ensure responsive goals interface.

### **🧹 Epic 5: Allowances & Chores**

**Goal:** Automate allowances and link chores to financial rewards.

- **Story 5.1 – Chore Assignment:** Create system for parents to assign chores with due dates and values.
- **Story 5.2 – Allowance Automation:** Implement scheduled allowance distribution.
- **Story 5.3 – Chore Completion → Rewards:** Build workflow where completed chores trigger allowance payments.
- **Story 5.4 – Localized tasks & reminders:** Translate chore and allowance-related content.
- **Story 5.5 – RWD chores & allowance lists:** Ensure responsive interfaces.

### **📅 Epic 11: Calendar & Scheduling**

**Goal:** Provide comprehensive calendar functionality for financial planning.

- **Story 11.1 – Calendar Integration:** Build calendar interface with daily, weekly, monthly, yearly views.
- **Story 11.2 – Custom Period Selection:** Implement date range picker for any chosen period.
- **Story 11.3 – Expense/Income Booking:** Enable scheduling future transactions from calendar.
- **Story 11.4 – Recurring Event Management:** Create, edit, and manage recurring financial events.
- **Story 11.5 – Calendar Notifications:** Build notification system for upcoming financial events.
- **Story 11.6 – Multi-language Calendar:** Ensure calendar supports all defined languages.
- **Story 11.7 – RWD Calendar Interface:** Ensure responsive calendar across all devices.

### **💱 Epic 12: Multi-Currency & Exchange Management**

**Goal:** Support multi-currency transactions and real-time exchange rate management.

- **Story 12.1 – Multi-Currency Account Setup:** Enable managing multiple currencies within account.
- **Story 12.2 – Real-Time Exchange Rates:** Integrate currency exchange APIs for real-time rates.
- **Story 12.3 – Travel Mode:** Create specialized travel interface for multi-country trips.
- **Story 12.4 – Multi-Currency Expense Entry:** Allow logging expenses in any supported currency.
- **Story 12.5 – Exchange Rate History:** Maintain historical exchange rate data.
- **Story 12.6 – Currency Conversion Calculator:** Build integrated calculator for quick conversions.
- **Story 12.7 – Travel Budget Allocation:** Enable budget allocation by country/currency.
- **Story 12.8 – Multi-Currency Reporting:** Generate financial reports with multi-currency support.
- **Story 12.9 – Localized Currency Support:** Ensure currency formatting follows international standards.
- **Story 12.10 – RWD Currency Interface:** Ensure responsive currency management interfaces.

### **💳 Epic 9: Pricing & Subscription**

**Goal:** Monetize with flexible, family-friendly pricing options.

- **Story 9.1 – Free Tier:** Implement free forever plan for users aged 18 and under.
- **Story 9.2 – Free Trial:** Offer 3-month free trial for all new adult users.
- **Story 9.3 – Monthly Subscription Plan:** Create monthly paid subscription option.
- **Story 9.4 – Yearly Subscription Plan:** Create discounted yearly paid subscription option.
- **Story 9.5 – Group/Family Subscription Pricing:** Implement pricing logic for entire family groups.
- **Story 9.6 – Discount Framework:** Build backend infrastructure for promotional discounts.
- **Story 9.7 – Payment Methods:** Integrate credit/debit cards, PayPal, Apple Pay, Google Pay.
- **Story 9.8 – Localized pricing page:** Ensure translated pricing with local currencies.
- **Story 9.9 – RWD pricing page:** Ensure responsive pricing page.

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

**Goal:** Provide seamless feedback and help access.

- **Story 10.1 – Instant Feedback Floating Button:** Implement always-accessible feedback button.
- **Story 10.2 – Feedback Integration & Management:** Log all user feedback in central system.

---

## **👤 MY CENTER NAVIGATION EPICS**

### **🔐 Epic 1: Authentication & Security (High Priority)**

**Goal:** Enable secure access with localized messages.

- **Story 1.1 – Secure Login:** Build login form with email and password.
- **Story 1.2 – Social Login:** Integrate OAuth with Google, Facebook, and X (Twitter).
- **Story 1.3 – Two-Factor Authentication:** Implement 6-digit verification via email/SMS.
- **Story 1.4 – Role-Based Permissions Middleware:** Develop server-side access controls.
- **Story 1.5 – Localized login/registration messages:** Translate all authentication messages.
- **Story 1.6 – RWD login and authentication pages:** Ensure responsive auth pages.

### **🌍 Epic 8: Multi-Language & RWD (System-Wide)**

**Goal:** Ensure global usability with localization and responsive design.

- **Story 8.1 – Language Support:** Implement full language support for EN, ZH-TW, ZH-CN, JA, ES.
- **Story 8.2 – Language Switcher:** Build UI element for easy language switching.
- **Story 8.3 – Auto-detect language:** Set app language based on browser/device settings.
- **Story 8.4 – Responsive Web Design:** Apply responsive principles across all application screens.
- **Story 8.5 – Centralized i18n library:** Structure all translatable strings for easy management.
- **Story 8.6 – RTL/LTR support:** Build structure supporting both text directions.

### **🎮 Epic 6: Gamification & Education**

**Goal:** Engage younger users with fun and educational tools.

- **Story 6.1 – Gamified Savings Tracker:** Create game-like interface for children's savings.
- **Story 6.2 – Badges & Achievements:** Implement rewards system for financial milestones.
- **Story 6.3 – Financial Literacy Hub:** Build section with articles, quizzes, and tips.
- **Story 6.4 – Multi-language content support:** Ensure educational content in all languages.
- **Story 6.5 – RWD gamification UI:** Ensure responsive gamification interface.

### **🔔 Epic 7: Advanced Notifications & Controls**

**Goal:** Provide parental controls and cross-device notifications.

- **Story 7.1 – Push Notifications:** Implement system for budget alerts, chore reminders, goal updates.
- **Story 7.2 – Unusual Spending Alerts:** Create algorithms for spending pattern detection.
- **Story 7.3 – Parental Controls:** Build feature for parents to approve/reject children's expenses.
- **Story 7.4 – Data Security & Compliance:** Ensure GDPR, CCPA, and other compliance standards.
- **Story 7.5 – Localized notifications:** Translate all notification content.
- **Story 7.6 – RWD notification banners:** Ensure responsive notification displays.

---

### **🆕 Changes in Version 0.97.0**

- **New Navigation Structure:** Implemented primary navigation buttons: Home, Overview, Payment, Chat, My Center
- **New Fund/Wallet System:** Added distinction between shared "Funds" and individual "Wallets" with management capabilities
- **New Chat System:** Added comprehensive messaging system similar to Line with text and voice capabilities
- **Enhanced Categorization:** Added detailed income and expenditure categories with customization options
- **New Personalization Features:** Implemented dark mode, theme selection, and style customization
- **Reorganized Epics:** All epics and stories categorized according to new navigation structure
- **New Epics Added:** Epic 13 (Personalization), Epic 14 (Home Screen Management), Epic 15 (Fund Management), Epic 16 (Wallet Management), Epic 17 (Categorization System), Epic 18 (Chat System)
- Version increment from 0.96.0 to 0.97.0

### **📊 Release Roadmap (v0.97.0)**

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