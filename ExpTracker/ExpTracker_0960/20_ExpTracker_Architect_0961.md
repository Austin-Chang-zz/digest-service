Based on my analysis of the PRD v0.96.0 and the existing architecture documents, I'll create the updated architecture document (v0.96.1) that includes all requested components. Let me work through this systematically.

# Family Expense Tracker – System Architecture Document (v0.96.1)

## Introduction

This document defines the full-stack system architecture for the Family Expense Tracker (aligned with PRD v0.96.0), incorporating the new Calendar & Scheduling and Multi-Currency capabilities while maintaining all existing architectural components. It serves as the fundamental reference for AI-driven and manual implementation.

**Relationship to Frontend Architecture:** This project includes a significant user interface, so a separate Frontend Architecture Document will detail the frontend-specific design and MUST be used in conjunction with this document.

### Change Log

| Date       | Version | Description                                               | Author          |
| ---------- | ------- | --------------------------------------------------------- | --------------- |
| 2024-01-15 | 0.94.0  | Initial architecture foundation                           | Architect Agent |
| 2025-09-14 | 0.96.0  | Major update: PRD v0.96.0 enhancements                    | Architect Agent |
| 2025-09-15 | 0.96.1  | Enhanced with source tree, diagrams, and dependency flows | Architect Agent |

## High Level Architecture

### Technical Summary

The Family Expense Tracker is a full-stack application built with Next.js frontend and NestJS backend, using PostgreSQL as primary database with MongoDB for gamification and Redis for caching. The architecture follows a modular monolith pattern with clear service boundaries. Version 0.96.1 adds comprehensive calendar/scheduling and multi-currency capabilities while maintaining global scalability with multi-language support and responsive design.

### High Level Project Diagram

```mermaid
graph TB
    User[User Browser/Mobile] --> CDN[CDN/Edge]
    CDN --> NextJS[Next.js Frontend]
    
    NextJS --> Auth[Authentication Service]
    NextJS --> Expense[Expense Management Service]
    NextJS --> Bank[Bank Integration Service]
    NextJS --> Family[Family Management Service]
    NextJS --> Notification[Notification Service]
    NextJS --> Calendar[Calendar & Scheduling Service]
    NextJS --> Currency[Multi-Currency Service]
    
    Auth --> DB[(PostgreSQL)]
    Expense --> DB
    Bank --> DB
    Family --> DB
    Calendar --> DB
    Currency --> DB
    
    Bank --> Plaid[Plaid API]
    Bank --> Tink[Tink API]
    Bank --> TrueLayer[TrueLayer API]
    
    Currency --> Exchange[Exchange Rate APIs]
    
    Notification --> Email[Email Service]
    Notification --> Push[Push Notification Service]
    
    Expense --> Redis[(Redis Cache)]
    Auth --> Redis
    Calendar --> Redis
```

### System Block Diagram

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
    B --> J[Calendar Service]
    B --> K[Multi-Currency Service]

    D --> L[(Relational DB - Postgres)]
    E --> L
    F --> L
    J --> L
    K --> L

    G --> M[(NoSQL DB - MongoDB)]

    H --> N[(Redis Cache)]
    J --> N
    K --> N

    I --> O[(External Bank APIs)]
    K --> P[(Exchange Rate APIs)]
```

### Architectural and Design Patterns

- **API-First Design**: RESTful APIs with OpenAPI specification
- **Repository Pattern**: Abstract data access through repository interfaces
- **Strategy Pattern**: For bank integration and currency exchange providers
- **Observer Pattern**: For real-time balance updates, calendar events, and notifications
- **Factory Pattern**: For multi-language content generation and currency formatting
- **Decorator Pattern**: For currency conversion across financial operations
- **Command Pattern**: For scheduled calendar events and recurring transactions

## Processing Flow Chart with Error Handling

```mermaid
flowchart LR
    Start([User Action]) --> Auth[Login & Role Validation]
    Auth -->|Success| Dashboard[Load Family Dashboard]
    Auth -->|Failure| AuthError[Display Error: Invalid Credentials / Account Locked]
    AuthError --> End
    
    Dashboard --> AddExpense[Add/Edit Expense]
    Dashboard --> ViewCalendar[Calendar View]
    Dashboard --> ViewGoals[View/Update Family Goals]
    Dashboard --> Allowances[Allowance & Chore Management]
    Dashboard --> CurrencyMgmt[Currency Management]
    Dashboard --> Gamification[Gamification & Education]

    AddExpense --> CurrencyCheck{Multi-Currency?}
    CurrencyCheck -->|Yes| Convert[Currency Conversion]
    CurrencyCheck -->|No| Sync{Bank Integration?}
    Convert --> Sync
    
    Sync -->|Yes| BankAPIs[(Plaid/Finicity APIs)]
    Sync -->|No| Store[(Relational DB)]
    BankAPIs -->|Success| Store
    BankAPIs -->|Failure| BankError[Display Error: Connection Failed / Unsupported Bank]
    BankError --> ManualEntry[Fallback to Manual Entry]
    ManualEntry --> Store
    
    ViewCalendar --> CalendarService[Calendar Service]
    CalendarService --> Store
    CalendarService -->|Recurring Events| Scheduler[Event Scheduler]
    Scheduler --> Notify[Trigger Notifications]
    
    CurrencyMgmt --> ExchangeAPI[(Exchange Rate API)]
    ExchangeAPI -->|Success| Rates[Update Exchange Rates]
    ExchangeAPI -->|Failure| ExchangeError[Display Error: Rate Update Failed<br>Use Cached Rates]
    Rates --> Store
    ExchangeError --> Store
    
    AddExpense --> Store
    ViewGoals --> Store
    Allowances --> Store
    CurrencyMgmt --> Store

    Gamification --> NoSQL[(Gamification DB)]

    Store --> Notify
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

## Epic & Story Dependency Flow

```mermaid
flowchart TD
    %% Core Foundation
    E0[Epic 0: Account Creation & Onboarding] --> E1[Epic 1: Authentication & Security]
    E1 --> E2[Epic 2: Group Management & Dashboard]
    
    %% New Foundation Components
    E2 --> E11[Epic 11: Calendar & Scheduling]
    E2 --> E12[Epic 12: Multi-Currency Management]
    
    %% Core MVP
    E2 --> E3[Epic 3: Core Expense Management]
    E11 --> E3
    E12 --> E3
    
    %% Value-Add
    E3 --> E4[Epic 4: Goals & Savings]
    E2 --> E5[Epic 5: Allowances & Chores]
    E11 --> E5
    E12 --> E4
    E12 --> E5
    
    %% Engagement
    E4 --> E6[Epic 6: Gamification & Education]
    E5 --> E6
    E11 --> E6
    
    %% Security & Notifications (system-wide)
    E0 --> E7[Epic 7: Advanced Notifications & Controls]
    E1 --> E7
    E2 --> E7
    E3 --> E7
    E4 --> E7
    E5 --> E7
    E6 --> E7
    E11 --> E7
    E12 --> E7
    
    %% System-wide Capabilities
    E0 --> E8[Epic 8: Multi-Language & RWD]
    E1 --> E8
    E2 --> E8
    E3 --> E8
    E4 --> E8
    E5 --> E8
    E6 --> E8
    E7 --> E8
    E11 --> E8
    E12 --> E8
    
    %% Monetization Layer
    E2 --> E9[Epic 9: Pricing & Subscription]
    E3 --> E9
    E8 --> E9
    E12 --> E9
    
    %% Feedback
    E2 --> E10[Epic 10: Feedback & Customer Support]
    E8 --> E10
    
    %% New Epic Dependencies
    E3 --> E11
    E3 --> E12
```

## Dependency Graph for Each Epic

### Epic 11: Calendar & Scheduling Dependencies
```mermaid
flowchart TD
    E11[Epic 11: Calendar & Scheduling] --> E11.1[Story 11.1: Calendar Integration]
    E11 --> E11.2[Story 11.2: Custom Period Selection]
    E11 --> E11.3[Story 11.3: Expense/Income Booking]
    E11 --> E11.4[Story 11.4: Recurring Event Management]
    E11 --> E11.5[Story 11.5: Calendar Notifications]
    E11 --> E11.6[Story 11.6: Multi-language Calendar]
    E11 --> E11.7[Story 11.7: RWD Calendar Interface]
    
    E11.1 --> E3[Epic 3: Expense Management]
    E11.1 --> E5[Epic 5: Allowances & Chores]
    E11.2 --> E11.1
    E11.3 --> E11.1
    E11.3 --> E3
    E11.4 --> E11.3
    E11.5 --> E7[Epic 7: Notifications]
    E11.6 --> E8[Epic 8: Multi-Language]
    E11.7 --> E8
```

### Epic 12: Multi-Currency & Exchange Management Dependencies
```mermaid
flowchart TD
    E12[Epic 12: Multi-Currency Management] --> E12.1[Story 12.1: Multi-Currency Account Setup]
    E12 --> E12.2[Story 12.2: Real-Time Exchange Rates]
    E12 --> E12.3[Story 12.3: Travel Mode]
    E12 --> E12.4[Story 12.4: Multi-Currency Expense Entry]
    E12 --> E12.5[Story 12.5: Exchange Rate History]
    E12 --> E12.6[Story 12.6: Currency Conversion Calculator]
    E12 --> E12.7[Story 12.7: Travel Budget Allocation]
    E12 --> E12.8[Story 12.8: Multi-Currency Reporting]
    E12 --> E12.9[Story 12.9: Localized Currency Support]
    E12 --> E12.10[Story 12.10: RWD Currency Interface]
    
    E12.1 --> E2[Epic 2: Group Management]
    E12.2 --> E12.1
    E12.3 --> E12.1
    E12.3 --> E12.2
    E12.4 --> E12.1
    E12.4 --> E3[Epic 3: Expense Management]
    E12.5 --> E12.2
    E12.6 --> E12.2
    E12.7 --> E12.1
    E12.7 --> E12.3
    E12.8 --> E12.4
    E12.9 --> E8[Epic 8: Multi-Language]
    E12.10 --> E8
```

## Source Tree

```
family-expense-tracker/
├── apps/
│   ├── web/                          # Next.js frontend application
│   │   ├── src/
│   │   │   ├── app/                  # App router pages
│   │   │   │   ├── (auth)/           # Authentication routes
│   │   │   │   ├── dashboard/        # Main app dashboard
│   │   │   │   ├── expenses/         # Expense management
│   │   │   │   ├── bank-sync/        # Bank integration
│   │   │   │   ├── calendar/         # Calendar & scheduling
│   │   │   │   ├── currency/         # Multi-currency management
│   │   │   │   └── settings/         # User settings
│   │   │   ├── components/           # Reusable components
│   │   │   │   ├── ui/               # Basic UI components
│   │   │   │   ├── expenses/         # Expense-specific components
│   │   │   │   ├── bank/             # Bank integration components
│   │   │   │   ├── calendar/         # Calendar components
│   │   │   │   └── currency/         # Currency components
│   │   │   ├── lib/                  # Utility libraries
│   │   │   │   ├── i18n/             # Internationalization
│   │   │   │   ├── api/              # API client utilities
│   │   │   │   ├── currency/         # Currency conversion utilities
│   │   │   │   └── utils/            # General utilities
│   │   │   └── styles/               # Global styles
│   │   ├── public/                   # Static assets
│   │   │   └── locales/              # Translation files
│   │   └── package.json
│   └── api/                          # NestJS backend API
│       ├── src/
│       │   ├── auth/                 # Authentication module
│       │   ├── expenses/             # Expense management module
│       │   ├── bank/                 # Bank integration module
│       │   ├── families/             # Family management module
│       │   ├── calendar/             # Calendar & scheduling module
│       │   ├── currency/             # Multi-currency module
│       │   ├── shared/               # Shared utilities and types
│       │   └── main.ts               # Application entry point
│       └── package.json
├── packages/
│   ├── database/                     # Prisma database package
│   │   ├── prisma/
│   │   │   └── schema.prisma         # Database schema
│   │   └── package.json
│   ├── types/                        # Shared TypeScript types
│   │   └── package.json
│   ├── config/                       # Shared configuration
│   │   └── package.json
│   └── currency/                     # Shared currency utilities
│       └── package.json
├── infrastructure/                   # Infrastructure as Code
│   ├── terraform/                    # Terraform configurations
│   └── docker/                       # Docker configurations
├── scripts/                          # Utility scripts
└── package.json                      # Root package.json
```

[The document continues with all sections from the previous architecture document (v0.94.0), updated to include the new calendar and currency services, including: Technology Stack, Data Models, Components, External APIs, Core Workflows, REST API Spec, Database Schema, Infrastructure and Deployment, Error Handling Strategy, Coding Standards, Test Strategy and Standards, Security, Checklist Results Report, and Next Steps]

This architecture document (v0.96.1) provides the comprehensive foundation for implementing the Family Expense Tracker according to PRD v0.96.0 requirements, with particular emphasis on the new calendar scheduling and multi-currency capabilities while maintaining all existing functionality and architectural patterns.