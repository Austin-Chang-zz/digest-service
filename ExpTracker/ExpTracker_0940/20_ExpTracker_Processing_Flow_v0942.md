# System Architecture & Processing Flow — v0.94.2

> Derived from v0.94.1, expanded with error handling flows
> 

---

## 1. Overview

This update (v0.94.2) extends the **system processing flow chart** with **error handling paths** for critical user journeys: login, bank sync, and payments. These flows ensure users receive localized, meaningful error states while maintaining system resilience.

---

## 2. Block Diagram (unchanged from v0.94.1)

```mermaid
graph TD
    A[Mobile App - iOS/Android] --> B[API Gateway]
    C[Web App] --> B

    B --> D[Auth & Role Service]
    B --> E[Expense Service]
    B --> F[Goals & Allowance Service]
    B --> G[Gamification Service]
    B --> H[Notification Service]
    B --> I[Bank Integration Service]

    D --> J[(Relational DB - Postgres)]
    E --> J
    F --> J

    G --> K[(NoSQL DB - MongoDB)]

    H --> L[(Redis Cache)]

    I --> M[(External Bank APIs - Plaid / Finicity / Tink / TrueLayer)]

```

---

## 3. Processing Flow Chart with Error Handling

```mermaid
flowchart LR
    Start([User Action]) --> Auth[Login & Role Validation]
    Auth -->|Success| Dashboard[Load Family Dashboard]
    Auth -->|Failure| AuthError[Display Error: Invalid Credentials / Account Locked]
    AuthError --> End

    Dashboard --> AddExpense[Add/Edit Expense]
    Dashboard --> ViewGoals[View/Update Family Goals]
    Dashboard --> Allowances[Allowance & Chore Management]
    Dashboard --> Gamification[Gamification & Education]

    AddExpense --> Sync{Bank Integration?}
    Sync -->|Yes| BankAPIs[(Plaid/Finicity APIs)]
    Sync -->|No| Store[(Relational DB)]
    BankAPIs -->|Success| Store
    BankAPIs -->|Failure| BankError[Display Error: Connection Failed / Unsupported Bank]
    BankError --> End

    AddExpense --> Store
    ViewGoals --> Store
    Allowances --> Store

    Gamification --> NoSQL[(Gamification DB)]

    Store --> Notify[Trigger Notifications]
    NoSQL --> Notify
    Notify --> End([User Receives Updates])

    %% Payment flow for subscription
    Dashboard --> Payment[Initiate Subscription/Payment]
    Payment --> BillingAPI[(Stripe/PayPal API)]
    BillingAPI -->|Success| Confirm[Payment Confirmed]
    BillingAPI -->|Failure| PaymentError[Display Error: Payment Failed / Retry or Change Method]
    Confirm --> End
    PaymentError --> End

```

---

## 4. Key Highlights

- **Auth Errors:** Localized messages (invalid login, locked account, verification required).
- **Bank Sync Errors:** Fallback to manual entry if provider fails or unsupported.
- **Payment Errors:** Retry flow with multiple payment methods, clear error transparency.
- **Notifications:** Error states also generate push/email alerts where relevant.

---

## 5. Next Steps

1. Integrate **localized error dictionaries** (EN, ZH-TW, ZH-CN, JA, ES).
2. Add retry and fallback mechanisms to UX flows.
3. Conduct usability testing on error states to ensure clarity and trust.

---

*Prepared by: Architect — Winston*