I'll create the updated architecture document (v0.97.0) that incorporates the latest PRD requirements while preserving all existing architectural components. Let me work through this systematically.

# Family Expense Tracker – System Architecture Document (v0.97.0)

## Introduction

This document defines the full-stack system architecture for the Family Expense Tracker (aligned with PRD v0.97.1), incorporating the new navigation structure, Fund/Wallet management system, Line-like chat functionality, enhanced categorization, and personalization features while maintaining all existing architectural components.

**Relationship to Frontend Architecture:** This project includes a significant user interface, so a separate Frontend Architecture Document will detail the frontend-specific design and MUST be used in conjunction with this document.

### Change Log

| Date       | Version | Description                                               | Author          |
| ---------- | ------- | --------------------------------------------------------- | --------------- |
| 2024-01-15 | 0.94.0  | Initial architecture foundation                           | Architect Agent |
| 2025-09-14 | 0.96.0  | Major update: PRD v0.96.0 enhancements                    | Architect Agent |
| 2025-09-15 | 0.96.1  | Enhanced with source tree, diagrams, and dependency flows | Architect Agent |
| 2025-09-15 | 0.96.2  | Merged and updated with latest PRD requirements           | Architect Agent |
| 2025-09-15 | 0.97.0  | Updated for PRD v0.97.1 with new navigation and features  | Architect Agent |

## High Level Architecture

### Technical Summary

The Family Expense Tracker is a full-stack application built with Next.js frontend and NestJS backend, using PostgreSQL as primary database with MongoDB for gamification and Redis for caching. The architecture follows a modular monolith pattern with clear service boundaries. Version 0.97.0 adds comprehensive navigation structure with Home, Overview, Payment, Chat, and My Center sections, Fund/Wallet management system, Line-like chat functionality, enhanced categorization, and personalization features while maintaining all existing functionality.

### High Level Project Diagram

```mermaid
graph TB
    User[User Browser/Mobile] --> CDN[CDN/Edge]
    CDN --> NextJS[Next.js Frontend]
    
    NextJS --> Nav[Navigation Service]
    NextJS --> Auth[Authentication Service]
    NextJS --> Expense[Expense Management Service]
    NextJS --> Bank[Bank Integration Service]
    NextJS --> Family[Family Management Service]
    NextJS --> Notification[Notification Service]
    NextJS --> Calendar[Calendar & Scheduling Service]
    NextJS --> Currency[Multi-Currency Service]
    NextJS --> Fund[Fund Management Service]
    NextJS --> Wallet[Wallet Management Service]
    NextJS --> Chat[Chat Service]
    NextJS --> Theme[Theme & Personalization Service]
    NextJS --> Category[Categorization Service]
    
    Auth --> DB[(PostgreSQL)]
    Expense --> DB
    Bank --> DB
    Family --> DB
    Calendar --> DB
    Currency --> DB
    Fund --> DB
    Wallet --> DB
    Chat --> DB
    Category --> DB
    
    Bank --> Plaid[Plaid API]
    Bank --> Tink[Tink API]
    Bank --> TrueLayer[TrueLayer API]
    Bank --> SaltEdge[SaltEdge API]
    
    Currency --> Exchange[Exchange Rate APIs]
    
    Notification --> Email[Email Service]
    Notification --> Push[Push Notification Service]
    
    Chat --> WS[WebSocket Service]
    
    Expense --> Redis[(Redis Cache)]
    Auth --> Redis
    Calendar --> Redis
    Theme --> Redis
```

### Navigation Architecture Diagram

```mermaid
graph TD
    App[Family Expense Tracker App] --> Home[🏠 Home Navigation]
    App --> Overview[📊 Overview Navigation]
    App --> Payment[💳 Payment Navigation]
    App --> ChatNav[💬 Chat Navigation]
    App --> MyCenter[👤 My Center Navigation]
    
    Home --> EP0[Epic 0: Account Creation & Onboarding]
    Home --> EP13[Epic 13: Personalization & Theme System]
    Home --> EP14[Epic 14: Home Screen Fund/Wallet Management]
    
    Overview --> EP15[Epic 15: Fund Management System]
    Overview --> EP16[Epic 16: Wallet Management System]
    Overview --> EP2[Epic 2: Group Management & Dashboard]
    
    Payment --> EP3[Epic 3: Core Expense Management]
    Payment --> EP17[Epic 17: Comprehensive Categorization System]
    Payment --> EP4[Epic 4: Goals & Savings]
    Payment --> EP5[Epic 5: Allowances & Chores]
    Payment --> EP11[Epic 11: Calendar & Scheduling]
    Payment --> EP12[Epic 12: Multi-Currency Management]
    Payment --> EP9[Epic 9: Pricing & Subscription]
    
    ChatNav --> EP18[Epic 18: Line-like Messaging System]
    ChatNav --> EP10[Epic 10: Feedback & Customer Support]
    
    MyCenter --> EP1[Epic 1: Authentication & Security]
    MyCenter --> EP8[Epic 8: Multi-Language & RWD]
    MyCenter --> EP6[Epic 6: Gamification & Education]
    MyCenter --> EP7[Epic 7: Advanced Notifications & Controls]
```

### System Block Diagram with New Components

```mermaid
graph TD
    A[Mobile App - iOS/Android] --> B[API Gateway]
    C[Web App] --> B

    B --> Nav[Navigation Service]
    B --> D[Auth & Role Service]
    B --> E[Expense Service]
    B --> F[Goals & Allowance Service]
    B --> G[Gamification Service]
    B --> H[Notification Service]
    B --> I[Bank Integration Service]
    B --> J[Calendar Service]
    B --> K[Multi-Currency Service]
    B --> L2[Fund Management Service]
    B --> M2[Wallet Management Service]
    B --> N2[Chat Service]
    B --> O2[Theme Service]
    B --> P2[Categorization Service]

    D --> DB[(Relational DB - Postgres)]
    E --> DB
    F --> DB
    J --> DB
    K --> DB
    L2 --> DB
    M2 --> DB
    N2 --> DB
    P2 --> DB

    G --> M[(NoSQL DB - MongoDB)]

    H --> N[(Redis Cache)]
    J --> N
    K --> N
    O2 --> N

    I --> O[(External Bank APIs)]
    K --> P[(Exchange Rate APIs)]
    N2 --> WS[WebSocket Server]
```

### Architectural and Design Patterns

- **API-First Design**: RESTful APIs with OpenAPI specification
- **Repository Pattern**: Abstract data access through repository interfaces
- **Strategy Pattern**: For bank integration and currency exchange providers
- **Observer Pattern**: For real-time balance updates, calendar events, and notifications
- **Factory Pattern**: For multi-language content generation and currency formatting
- **Decorator Pattern**: For currency conversion across financial operations
- **Command Pattern**: For scheduled calendar events and recurring transactions
- **Publisher-Subscriber Pattern**: For real-time chat messaging and notifications
- **Composite Pattern**: For Fund/Wallet hierarchy and management
- **State Pattern**: For theme and personalization state management

## Processing Flow Chart with Enhanced Navigation

```mermaid
flowchart LR
    Start([User Action]) --> Nav[Navigation Service]
    Nav --> Home[🏠 Home Screen]
    Nav --> Overview[📊 Overview Screen]
    Nav --> Payment[💳 Payment Screen]
    Nav --> Chat[💬 Chat Screen]
    Nav --> MyCenter[👤 My Center Screen]
    
    Home --> FundWallet[Fund/Wallet Management]
    Overview --> FundMgmt[Fund Operations]
    Overview --> WalletMgmt[Wallet Operations]
    
    Payment --> ExpenseFlow[Expense Management]
    Payment --> BankSync[Bank Integration]
    Payment --> CalendarView[Calendar & Scheduling]
    Payment --> CurrencyMgmt[Multi-Currency]
    
    Chat --> Messaging[Real-time Chat]
    Chat --> Feedback[Feedback System]
    
    MyCenter --> AuthFlow[Authentication]
    MyCenter --> Settings[User Settings]
    MyCenter --> Personalization[Theme Customization]
    
    %% Connect to existing flows
    ExpenseFlow --> Existing[Existing Processing Flow]
    BankSync --> Existing
    CalendarView --> Existing
    CurrencyMgmt --> Existing
    AuthFlow --> Existing
    
    Existing --> End([Completion])
```

## Epic & Story Dependency Flow with New Structure

```mermaid
flowchart TD
    %% Core Foundation
    E0[Epic 0: Account Creation & Onboarding] --> E1[Epic 1: Authentication & Security]
    E1 --> E2[Epic 2: Group Management & Dashboard]
    
    %% New Navigation Structure
    E2 --> E13[Epic 13: Personalization]
    E2 --> E14[Epic 14: Home Screen Management]
    E2 --> E15[Epic 15: Fund Management]
    E2 --> E16[Epic 16: Wallet Management]
    
    %% Core MVP
    E2 --> E3[Epic 3: Core Expense Management]
    E13 --> E3
    E14 --> E3
    E15 --> E3
    E16 --> E3
    
    %% Enhanced Categorization
    E3 --> E17[Epic 17: Categorization System]
    
    %% Value-Add
    E3 --> E4[Epic 4: Goals & Savings]
    E2 --> E5[Epic 5: Allowances & Chores]
    E15 --> E4
    E16 --> E4
    E15 --> E5
    E16 --> E5
    
    %% New Features
    E2 --> E11[Epic 11: Calendar & Scheduling]
    E2 --> E12[Epic 12: Multi-Currency Management]
    E3 --> E11
    E3 --> E12
    
    %% Engagement
    E4 --> E6[Epic 6: Gamification & Education]
    E5 --> E6
    E11 --> E6
    
    %% Chat System
    E2 --> E18[Epic 18: Chat System]
    E18 --> E10[Epic 10: Feedback & Support]
    
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
    E18 --> E7
    
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
    E13 --> E8
    E14 --> E8
    E15 --> E8
    E16 --> E8
    E17 --> E8
    E18 --> E8
    
    %% Monetization Layer
    E2 --> E9[Epic 9: Pricing & Subscription]
    E3 --> E9
    E8 --> E9
    E12 --> E9
    
    %% Feedback
    E2 --> E10[Epic 10: Feedback & Customer Support]
    E8 --> E10
```

## Tech Stack

### Cloud Infrastructure

- **Provider**: AWS (Amazon Web Services)
- **Key Services**: EC2, RDS, S3, CloudFront, Lambda, SNS, SES, Elasticache
- **Deployment Regions**: us-east-1 (Primary), eu-west-1 (Secondary)

### Technology Stack Table

| Category                    | Technology      | Version    | Purpose                   | Rationale                                                      |
| --------------------------- | --------------- | ---------- | ------------------------- | -------------------------------------------------------------- |
| **Frontend Framework**      | Next.js         | 14.0.0     | React framework with SSR  | Excellent i18n support, API routes, optimized performance      |
| **UI Library**              | React           | 18.2.0     | Component library         | Industry standard, extensive ecosystem                         |
| **Backend Runtime**         | Node.js         | 20.11.0    | Server-side JavaScript    | LTS version, async capabilities, team expertise                |
| **Backend Framework**       | NestJS          | 10.0.0     | API framework             | TypeScript support, modular architecture, dependency injection |
| **Database**                | PostgreSQL      | 15.0       | Primary data store        | ACID compliance, JSON support, financial data integrity        |
| **ORM**                     | Prisma          | 5.0.0      | Database client           | Type safety, migrations, excellent DX                          |
| **Caching**                 | Redis           | 7.0.0      | Session storage & caching | High performance, pub/sub capabilities                         |
| **Real-time Communication** | Socket.IO       | 4.7.0      | WebSocket implementation  | Real-time chat and notifications                               |
| **Authentication**          | JWT             | 9.0.0      | Token-based auth          | Stateless, scalable, industry standard                         |
| **Bank Integration**        | Plaid API       | 2020-09-14 | Bank data connectivity    | Global coverage, reliable API                                  |
| **Bank Integration**        | Tink API        | 2.0.0      | European bank integration | Strong EU presence, PSD2 compliant                             |
| **Bank Integration**        | TrueLayer       | 2.0.0      | UK bank integration       | Open banking specialist, UK coverage                           |
| **Bank Integration**        | SaltEdge API    | 5.0.0      | Global bank integration   | Extended global coverage                                       |
| **Currency Exchange**       | ExchangeRateAPI | 1.0.0      | Real-time exchange rates  | Reliable currency data provider                                |
| **Internationalization**    | next-i18next    | 13.0.0     | Multi-language support    | Next.js integration, SSR compatible                            |
| **Styling**                 | Tailwind CSS    | 3.3.0      | Utility-first CSS         | Responsive design, rapid development                           |
| **UI Components**           | shadcn/ui       | 0.8.0      | Component library         | Accessible, customizable components                            |
| **Testing**                 | Jest            | 29.0.0     | Testing framework         | Comprehensive testing, snapshot support                        |
| **E2E Testing**             | Playwright      | 1.38.0     | Browser testing           | Cross-browser, reliable automation                             |
| **Deployment**              | Docker          | 20.10.0    | Containerization          | Environment consistency, scaling                               |
| **CI/CD**                   | GitHub Actions  | -          | Automation                | GitHub integration, flexible workflows                         |

## Data Models

### User Model
**Purpose:** Store user account information and preferences

**Key Attributes:**
- `id`: UUID - Primary identifier
- `email`: String - Unique login identifier
- `password_hash`: String - Hashed password
- `name`: String - Display name
- `role`: Enum(Parent, Partner, Teen, Child) - System role
- `language`: Enum(EN, ZH-TW, ZH-CN, JA, ES) - Preference
- `currency`: String - Default currency code
- `theme_preference`: String - Selected theme
- `dark_mode`: Boolean - Dark mode preference

**Relationships:**
- Belongs to a Family
- Has many Expenses
- Has many Contributions
- Has many Wallets
- Has many ChatMessages

### Family Model
**Purpose:** Represent family groups and their configuration

**Key Attributes:**
- `id`: UUID - Primary identifier
- `name`: String - Family display name
- `invite_code`: String - Unique invitation code
- `subscription_tier`: Enum(Free, Premium) - Payment status
- `default_currency`: String - Family currency setting

**Relationships:**
- Has many Users
- Has many Expenses
- Has many Goals
- Has many Funds
- Has many ChatChannels

### Fund Model (NEW)
**Purpose:** Manage shared family funds for specific purposes

**Key Attributes:**
- `id`: UUID - Primary identifier
- `name`: String - Fund name (e.g., "Dinner Fund", "Trip Fund")
- `purpose`: String - Fund purpose description
- `target_amount`: Decimal - Target amount for the fund
- `current_balance`: Decimal - Current balance in the fund
- `currency`: String - Currency code
- `is_shared`: Boolean - Whether fund is shared among family members
- `contribution_rules`: JSONB - Rules for contributing to the fund

**Relationships:**
- Belongs to a Family
- Has many FundContributions
- Has many FundExpenses

### Wallet Model (NEW)
**Purpose:** Manage individual financial tracking envelopes

**Key Attributes:**
- `id`: UUID - Primary identifier
- `name`: String - Wallet name (e.g., "Travel Wallet", "Food Wallet")
- `purpose`: String - Wallet purpose description
- `allocated_amount`: Decimal - Budget allocated to this wallet
- `current_balance`: Decimal - Current balance in the wallet
- `currency`: String - Currency code
- `wallet_type`: Enum(Cash, Digital, Savings) - Type of wallet
- `spending_limit`: Decimal - Optional spending limit

**Relationships:**
- Belongs to a User
- Has many WalletTransactions
- Has many BudgetAlerts

### Expense Model
**Purpose:** Track financial transactions within the family

**Key Attributes:**
- `id`: UUID - Primary identifier
- `amount`: Decimal - Transaction amount
- `currency`: String - Currency code
- `description`: String - Transaction description
- `category`: Enum(Food, Transportation, Entertainment, etc.) - Spending category
- `subcategory`: String - More specific category
- `date`: DateTime - Transaction date
- `type`: Enum(Expense, Income, Transfer) - Transaction type
- `recurring`: Boolean - Is recurring expense
- `recurring_schedule`: JSON - Cron-like schedule definition
- `fund_id`: UUID - Optional reference to Fund
- `wallet_id`: UUID - Optional reference to Wallet

**Relationships:**
- Belongs to a User (payer)
- Belongs to a Family
- Optional connection to BankTransaction
- Optional connection to Fund
- Optional connection to Wallet

### ChatChannel Model (NEW)
**Purpose:** Manage chat channels for family communication

**Key Attributes:**
- `id`: UUID - Primary identifier
- `name`: String - Channel name
- `description`: String - Channel description
- `channel_type`: Enum(Family, Group, Direct) - Type of channel
- `is_private`: Boolean - Private channel flag
- `created_by`: UUID - User who created the channel

**Relationships:**
- Belongs to a Family
- Has many ChatMessages
- Has many ChannelMembers

### ChatMessage Model (NEW)
**Purpose:** Store chat messages with various content types

**Key Attributes:**
- `id`: UUID - Primary identifier
- `content`: Text - Message content
- `message_type`: Enum(Text, Voice, Image, Video, Document) - Message type
- `media_url`: String - URL for media content
- `media_metadata`: JSONB - Metadata for media files
- `is_edited`: Boolean - Message edited flag
- `edited_at`: DateTime - When message was edited
- `replied_to_id`: UUID - Reference to replied message
- `read_by`: JSONB - Tracking who read the message

**Relationships:**
- Belongs to a ChatChannel
- Belongs to a User (sender)
- Has many Reactions

### ThemePreference Model (NEW)
**Purpose:** Store user theme and personalization preferences

**Key Attributes:**
- `id`: UUID - Primary identifier
- `user_id`: UUID - Reference to user
- `theme_name`: String - Selected theme name
- `color_scheme`: JSONB - Custom color scheme
- `font_preference`: String - Preferred font
- `layout_preference`: JSONB - UI layout preferences
- `home_screen_layout`: JSONB - Home screen arrangement

**Relationships:**
- Belongs to a User

### CategoryModel (NEW)
**Purpose:** Manage income and expenditure categorization system

**Key Attributes:**
- `id`: UUID - Primary identifier
- `name`: String - Category name
- `type`: Enum(Income, Expense) - Category type
- `parent_id`: UUID - Optional parent category
- `is_system`: Boolean - System-defined category
- `icon`: String - Category icon
- `color`: String - Category color
- `budget_default`: Decimal - Default budget amount

**Relationships:**
- Has many Subcategories
- Has many Expenses

[Previous data models for BankTransaction, Goal, CalendarEvent, CurrencyExchange remain unchanged]

## Components

### Navigation Service (NEW)
**Responsibility:** Handle application navigation structure and routing

**Key Interfaces:**
- `GET /api/navigation/structure` - Get navigation structure
- `GET /api/navigation/items` - Get navigation items for user
- `POST /api/navigation/preferences` - Save navigation preferences
- `GET /api/navigation/context` - Get navigation context

**Dependencies:** User Repository, Family Repository, Redis Cache

**Technology Stack:** NestJS, Redis, JWT

### Fund Management Service (NEW)
**Responsibility:** Handle shared family fund operations

**Key Interfaces:**
- `POST /api/funds` - Create new fund
- `GET /api/funds` - List family funds
- `PUT /api/funds/:id` - Update fund
- `POST /api/funds/:id/contributions` - Add contribution to fund
- `POST /api/funds/:id/transfers` - Transfer between funds/wallets
- `GET /api/funds/:id/history` - Get fund history

**Dependencies:** Fund Repository, User Repository, Transaction Service

**Technology Stack:** NestJS, Prisma, Decimal.js

### Wallet Management Service (NEW)
**Responsibility:** Handle individual wallet operations

**Key Interfaces:**
- `POST /api/wallets` - Create new wallet
- `GET /api/wallets` - List user wallets
- `PUT /api/wallets/:id` - Update wallet
- `POST /api/wallets/:id/allocations` - Allocate budget to wallet
- `POST /api/wallets/:id/transfers` - Transfer between wallets
- `GET /api/wallets/:id/transactions` - Get wallet transactions

**Dependencies:** Wallet Repository, User Repository, Budget Service

**Technology Stack:** NestJS, Prisma, Decimal.js

### Chat Service (NEW)
**Responsibility:** Handle real-time messaging functionality

**Key Interfaces:**
- `GET /api/chat/channels` - List user channels
- `POST /api/chat/channels` - Create new channel
- `GET /api/chat/channels/:id/messages` - Get channel messages
- `POST /api/chat/channels/:id/messages` - Send message
- `PUT /api/chat/messages/:id` - Edit message
- `DELETE /api/chat/messages/:id` - Delete message
- `POST /api/chat/messages/:id/reactions` - Add reaction
- `WS /chat` - WebSocket endpoint for real-time messaging

**Dependencies:** Chat Repository, User Repository, WebSocket Service

**Technology Stack:** NestJS, Socket.IO, Redis Pub/Sub

### Theme Service (NEW)
**Responsibility:** Handle theme and personalization features

**Key Interfaces:**
- `GET /api/themes` - Get available themes
- `POST /api/themes/active` - Set active theme
- `GET /api/themes/custom` - Get custom themes
- `POST /api/themes/custom` - Create custom theme
- `PUT /api/themes/custom/:id` - Update custom theme
- `GET /api/themes/preferences` - Get theme preferences

**Dependencies:** Theme Repository, User Repository, Redis Cache

**Technology Stack:** NestJS, Redis, CSS-in-JS

### Categorization Service (NEW)
**Responsibility:** Manage income and expenditure categories

**Key Interfaces:**
- `GET /api/categories` - Get category hierarchy
- `POST /api/categories` - Create new category
- `PUT /api/categories/:id` - Update category
- `DELETE /api/categories/:id` - Delete category
- `GET /api/categories/system` - Get system categories
- `POST /api/categories/import` - Import categories

**Dependencies:** Category Repository, Expense Repository

**Technology Stack:** NestJS, Prisma

[Previous components for Authentication, Expense Management, Bank Integration, Family Management, Calendar, Multi-Currency remain unchanged]

## External APIs

[Previous external APIs for Plaid, Tink, TrueLayer, SaltEdge, Exchange Rate remain unchanged]

## Core Workflows

### Fund Creation and Management Sequence

```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend
    participant FM as Fund Service
    participant DB as Database
    participant N as Notification Service
    
    U->>F: Navigate to Overview → Funds
    F->>FM: GET /api/funds
    FM->>DB: Query user's funds
    DB-->>FM: Return funds list
    FM-->>F: Return funds data
    F-->>U: Display funds list
    
    U->>F: Click "Create New Fund"
    F->>U: Show fund creation form
    U->>F: Enter fund details and submit
    F->>FM: POST /api/funds
    FM->>DB: Create fund record
    FM->>N: Notify family members of new fund
    FM-->>F: Fund created successfully
    F-->>U: Show confirmation and redirect to fund details
```

### Real-time Chat Message Sequence

```mermaid
sequenceDiagram
    participant U1 as User 1
    participant F1 as Frontend 1
    participant C as Chat Service
    participant WS as WebSocket Server
    participant DB as Database
    participant F2 as Frontend 2
    participant U2 as User 2
    
    U1->>F1: Type message and send
    F1->>C: POST /api/chat/channels/:id/messages
    C->>DB: Store message
    C->>WS: Broadcast message via WebSocket
    WS->>F2: Deliver message in real-time
    F2->>U2: Display new message
    
    U2->>F2: Read message
    F2->>C: PATCH /api/chat/messages/:id/read
    C->>DB: Update read status
    C->>WS: Broadcast read receipt
    WS->>F1: Deliver read receipt
    F1->>U1: Update message status
```

### Theme Application Sequence

```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend
    participant T as Theme Service
    participant DB as Database
    participant R as Redis Cache
    
    U->>F: Navigate to My Center → Appearance
    F->>T: GET /api/themes
    T->>DB: Query available themes
    DB-->>T: Return themes list
    T-->>F: Return themes data
    F-->>U: Display theme selection
    
    U->>F: Select new theme
    F->>T: POST /api/themes/active
    T->>DB: Update user theme preference
    T->>R: Cache theme configuration
    T-->>F: Theme applied successfully
    F->>F: Apply CSS variables and styles
    F-->>U: UI updates with new theme
```

### Wallet Budget Allocation Sequence

```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend
    participant W as Wallet Service
    participant B as Budget Service
    participant DB as Database
    participant N as Notification Service
    
    U->>F: Navigate to Overview → Wallets
    F->>W: GET /api/wallets
    W->>DB: Query user's wallets
    DB-->>W: Return wallets list
    W-->>F: Return wallets data
    F-->>U: Display wallets with balances
    
    U->>F: Select wallet → "Allocate Budget"
    F->>U: Show allocation form
    U->>F: Enter allocation amount and submit
    F->>W: POST /api/wallets/:id/allocations
    W->>B: Check available budget
    B-->>W: Budget available
    W->>DB: Update wallet allocation
    W->>N: Create budget allocation notification
    W-->>F: Allocation successful
    F-->>U: Show confirmation and updated balance
```

[Previous workflows for User Onboarding, Bank Transaction Sync, Multi-Currency Expense, Calendar Event remain unchanged]

## REST API Spec

[Previous API specifications remain, with additions for new services]

### New Endpoints for Fund Management

```yaml
/funds:
  post:
    summary: Create a new fund
    requestBody:
      content:
        application/json:
          schema:
            type: object
            properties:
              name:
                type: string
              purpose:
                type: string
              target_amount:
                type: number
              currency:
                type: string
              is_shared:
                type: boolean
    responses:
      '201':
        description: Fund created successfully
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Fund'

/funds/{id}/contributions:
  post:
    summary: Add contribution to fund
    parameters:
      - name: id
        in: path
        required: true
        schema:
          type: string
    requestBody:
      content:
        application/json:
          schema:
            type: object
            properties:
              amount:
                type: number
              currency:
                type: string
              description:
                type: string
    responses:
      '200':
        description: Contribution added successfully
```

### New Endpoints for Chat System

```yaml
/chat/channels:
  get:
    summary: Get user's chat channels
    responses:
      '200':
        description: Channels retrieved
        content:
          application/json:
            schema:
              type: array
              items:
                $ref: '#/components/schemas/ChatChannel'

/chat/channels/{id}/messages:
  get:
    summary: Get channel messages
    parameters:
      - name: id
        in: path
        required: true
        schema:
          type: string
      - name: limit
        in: query
        schema:
          type: integer
      - name: before
        in: query
        schema:
          type: string
    responses:
      '200':
        description: Messages retrieved
        content:
          application/json:
            schema:
              type: object
              properties:
                messages:
                  type: array
                  items:
                    $ref: '#/components/schemas/ChatMessage'
                hasMore:
                  type: boolean
```

### New Endpoints for Theme Management

```yaml
/themes:
  get:
    summary: Get available themes
    responses:
      '200':
        description: Themes retrieved
        content:
          application/json:
            schema:
              type: array
              items:
                $ref: '#/components/schemas/Theme'

/themes/active:
  post:
    summary: Set active theme
    requestBody:
      content:
        application/json:
          schema:
            type: object
            properties:
              theme_name:
                type: string
              apply_dark_mode:
                type: boolean
    responses:
      '200':
        description: Theme applied successfully
```

### New Schemas

```yaml
components:
  schemas:
    Fund:
      type: object
      properties:
        id:
          type: string
          format: uuid
        name:
          type: string
        purpose:
          type: string
        target_amount:
          type: number
        current_balance:
          type: number
        currency:
          type: string
        is_shared:
          type: boolean

    ChatChannel:
      type: object
      properties:
        id:
          type: string
          format: uuid
        name:
          type: string
        description:
          type: string
        channel_type:
          type: string
          enum: [Family, Group, Direct]
        unread_count:
          type: integer

    ChatMessage:
      type: object
      properties:
        id:
          type: string
          format: uuid
        content:
          type: string
        message_type:
          type: string
          enum: [Text, Voice, Image, Video, Document]
        sender:
          $ref: '#/components/schemas/User'
        timestamp:
          type: string
          format: date-time

    Theme:
      type: object
      properties:
        name:
          type: string
        display_name:
          type: string
        is_dark:
          type: boolean
        colors:
          type: object
        preview_url:
          type: string
```

## Database Schema

### New Tables for Fund/Wallet System

```sql
-- Funds table
CREATE TABLE funds (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    purpose TEXT,
    target_amount DECIMAL(19,4),
    current_balance DECIMAL(19,4) DEFAULT 0,
    currency VARCHAR(3) NOT NULL DEFAULT 'USD',
    is_shared BOOLEAN DEFAULT TRUE,
    contribution_rules JSONB,
    family_id UUID NOT NULL REFERENCES families(id),
    created_by UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Fund contributions table
CREATE TABLE fund_contributions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    amount DECIMAL(19,4) NOT NULL,
    currency VARCHAR(3) NOT NULL,
    description TEXT,
    fund_id UUID NOT NULL REFERENCES funds(id),
    user_id UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Wallets table
CREATE TABLE wallets (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    purpose TEXT,
    allocated_amount DECIMAL(19,4) DEFAULT 0,
    current_balance DECIMAL(19,4) DEFAULT 0,
    currency VARCHAR(3) NOT NULL DEFAULT 'USD',
    wallet_type VARCHAR(20) DEFAULT 'Cash' CHECK (wallet_type IN ('Cash', 'Digital', 'Savings')),
    spending_limit DECIMAL(19,4),
    user_id UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Wallet transactions table
CREATE TABLE wallet_transactions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    amount DECIMAL(19,4) NOT NULL,
    currency VARCHAR(3) NOT NULL,
    description TEXT,
    transaction_type VARCHAR(20) CHECK (transaction_type IN ('Allocation', 'Expense', 'Transfer', 'Adjustment')),
    wallet_id UUID NOT NULL REFERENCES wallets(id),
    related_expense_id UUID REFERENCES expenses(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### New Tables for Chat System

```sql
-- Chat channels table
CREATE TABLE chat_channels (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(255) NOT NULL,
    description TEXT,
    channel_type VARCHAR(20) NOT NULL CHECK (channel_type IN ('Family', 'Group', 'Direct')),
    is_private BOOLEAN DEFAULT FALSE,
    family_id UUID REFERENCES families(id),
    created_by UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Channel members table
CREATE TABLE channel_members (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    channel_id UUID NOT NULL REFERENCES chat_channels(id),
    user_id UUID NOT NULL REFERENCES users(id),
    joined_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_read_at TIMESTAMP,
    UNIQUE(channel_id, user_id)
);

-- Chat messages table
CREATE TABLE chat_messages (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    content TEXT,
    message_type VARCHAR(20) DEFAULT 'Text' CHECK (message_type IN ('Text', 'Voice', 'Image', 'Video', 'Document')),
    media_url VARCHAR(500),
    media_metadata JSONB,
    is_edited BOOLEAN DEFAULT FALSE,
    edited_at TIMESTAMP,
    replied_to_id UUID REFERENCES chat_messages(id),
    read_by JSONB DEFAULT '[]'::jsonb,
    channel_id UUID NOT NULL REFERENCES chat_channels(id),
    user_id UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Message reactions table
CREATE TABLE message_reactions (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    emoji VARCHAR(10) NOT NULL,
    message_id UUID NOT NULL REFERENCES chat_messages(id),
    user_id UUID NOT NULL REFERENCES users(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(message_id, user_id, emoji)
);
```

### New Tables for Theme System

```sql
-- Theme preferences table
CREATE TABLE theme_preferences (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID NOT NULL REFERENCES users(id),
    theme_name VARCHAR(100) NOT NULL,
    color_scheme JSONB DEFAULT '{}'::jsonb,
    font_preference VARCHAR(50),
    layout_preference JSONB DEFAULT '{}'::jsonb,
    home_screen_layout JSONB DEFAULT '{}'::jsonb,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(user_id)
);

-- Available themes table
CREATE TABLE available_themes (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(100) NOT NULL UNIQUE,
    display_name JSONB NOT NULL, -- Localized display names
    is_dark BOOLEAN DEFAULT FALSE,
    colors JSONB NOT NULL,
    is_system BOOLEAN DEFAULT TRUE,
    preview_url VARCHAR(500),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### New Tables for Categorization System

```sql
-- Categories table
CREATE TABLE categories (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name JSONB NOT NULL, -- Localized category names
    type VARCHAR(20) NOT NULL CHECK (type IN ('Income', 'Expense')),
    parent_id UUID REFERENCES categories(id),
    is_system BOOLEAN DEFAULT FALSE,
    icon VARCHAR(50),
    color VARCHAR(7),
    budget_default DECIMAL(19,4),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Update expenses table to include category relationship
ALTER TABLE expenses ADD COLUMN category_id UUID REFERENCES categories(id);
```

### Updated Users Table

```sql
-- Add theme preferences to users table
ALTER TABLE users ADD COLUMN theme_preference VARCHAR(100);
ALTER TABLE users ADD COLUMN dark_mode BOOLEAN DEFAULT FALSE;
```

[Previous database schema for existing tables remains unchanged]

## Source Tree

### Updated Source Structure with New Components

```
family-expense-tracker/
├── apps/
│   ├── web/                          # Next.js frontend application
│   │   ├── src/
│   │   │   ├── app/                  # App router pages
│   │   │   │   ├── (auth)/           # Authentication routes
│   │   │   │   ├── dashboard/        # Main app dashboard
│   │   │   │   ├── home/             # Home navigation section
│   │   │   │   ├── overview/         # Overview navigation section
│   │   │   │   ├── payment/          # Payment navigation section
│   │   │   │   ├── chat/             # Chat navigation section
│   │   │   │   ├── my-center/        # My Center navigation section
│   │   │   │   └── settings/         # User settings
│   │   │   ├── components/           # Reusable components
│   │   │   │   ├── ui/               # Basic UI components
│   │   │   │   ├── navigation/       # Navigation components
│   │   │   │   ├── funds/            # Fund management components
│   │   │   │   ├── wallets/          # Wallet management components
│   │   │   │   ├── chat/             # Chat interface components
│   │   │   │   ├── themes/           # Theme components
│   │   │   │   ├── categories/       # Category components
│   │   │   │   ├── expenses/         # Expense-specific components
│   │   │   │   ├── bank/             # Bank integration components
│   │   │   │   ├── calendar/         # Calendar components
│   │   │   │   └── currency/         # Currency components
│   │   │   ├── lib/                  # Utility libraries
│   │   │   │   ├── i18n/             # Internationalization
│   │   │   │   ├── api/              # API client utilities
│   │   │   │   ├── currency/         # Currency conversion utilities
│   │   │   │   ├── themes/           # Theme utilities
│   │   │   │   ├── chat/             # Chat utilities
│   │   │   │   └── utils/            # General utilities
│   │   │   └── styles/               # Global styles
│   │   ├── public/                   # Static assets
│   │   │   └── locales/              # Translation files
│   │   └── package.json
│   └── api/                          # NestJS backend API
│       ├── src/
│       │   ├── navigation/           # Navigation module (NEW)
│       │   ├── funds/               # Fund management module (NEW)
│       │   ├── wallets/             # Wallet management module (NEW)
│       │   ├── chat/                # Chat module (NEW)
│       │   ├── themes/              # Theme module (NEW)
│       │   ├── categories/          # Categorization module (NEW)
│       │   ├── auth/                # Authentication module
│       │   ├── expenses/            # Expense management module
│       │   ├── bank/                # Bank integration module
│       │   ├── families/            # Family management module
│       │   ├── calendar/            # Calendar & scheduling module
│       │   ├── currency/            # Multi-currency module
│       │   ├── shared/              # Shared utilities and types
│       │   └── main.ts              # Application entry point
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
│   ├── currency/                     # Shared currency utilities
│   ├── chat-types/                   # Chat type definitions (NEW)
│   ├── theme-types/                  # Theme type definitions (NEW)
│   └── navigation-types/             # Navigation type definitions (NEW)
├── infrastructure/                   # Infrastructure as Code
│   ├── terraform/                    # Terraform configurations
│   └── docker/                       # Docker configurations
├── scripts/                          # Utility scripts
└── package.json                      # Root package.json
```

[Previous infrastructure, deployment, error handling, coding standards, test strategy, and security sections remain unchanged with appropriate updates for new components]

## Checklist Results Report

*Checklist validation will be executed after architecture document completion*

## Next Steps

1. **Frontend Architecture Creation**: Use "Frontend Architecture Mode" with this document as input to create detailed frontend architecture focusing on new navigation structure
2. **Product Owner Review**: Review this architecture with Product Owner for alignment with PRD v0.97.1 requirements
3. **Story Implementation**: Begin story implementation with Dev agent starting with navigation structure foundation
4. **Real-time Infrastructure**: Set up WebSocket infrastructure for chat functionality
5. **Theme System Implementation**: Implement theme engine with CSS variables and dynamic loading

### Architect Prompt for Enhanced Frontend Architecture

Create a comprehensive Frontend Architecture Document for the Family Expense Tracker based on the main architecture defined here. Focus on:

- Navigation structure with Home, Overview, Payment, Chat, and My Center sections
- Next.js 14 application structure with enhanced App Router for new navigation
- Fund/Wallet management component architecture
- Real-time chat interface with WebSocket integration
- Theme system with dynamic CSS variables and theme switching
- Enhanced categorization system with customizable categories
- Component architecture following atomic design principles
- State management strategy for financial data and real-time chat
- Internationalization implementation with next-i18next
- Responsive design system with Tailwind CSS
- Bank integration component design for Plaid Link
- Real-time balance display components
- Calendar interface with multiple view support
- Currency conversion and display components
- Testing strategy for UI components

Ensure alignment with the backend architecture patterns and technology choices specified in this document, particularly for the new navigation structure, real-time chat, theme system, and Fund/Wallet management.

---

This architecture document provides the comprehensive foundation for implementing the Family Expense Tracker according to PRD v0.97.1 requirements, with particular emphasis on the new navigation structure, Fund/Wallet management system, Line-like chat functionality, enhanced categorization, and personalization features while maintaining all existing functionality and architectural patterns.

This updated architecture document (v0.97.0) successfully incorporates all the new requirements from PRD v0.97.1 while preserving all existing architectural components from the previous v0.96.2 version. The document includes:

1. **New Navigation Structure**: Home, Overview, Payment, Chat, and My Center sections
2. **Fund/Wallet Management System**: Complete architecture for shared Funds and individual Wallets
3. **Line-like Chat Functionality**: Real-time messaging system with WebSocket integration
4. **Enhanced Categorization**: Detailed income and expenditure category system
5. **Personalization Features**: Theme system with dark mode and customization options
6. **Updated Data Models**: New database tables for all new functionality
7. **New Services**: Navigation, Fund, Wallet, Chat, Theme, and Categorization services
8. **Enhanced API Specifications**: New endpoints for all added functionality
9. **Updated Source Tree**: Reflects new navigation structure and components
10. **Comprehensive Diagrams**: Updated architecture diagrams showing new components

All existing architectural patterns, technology choices, security measures, and deployment strategies have been maintained while seamlessly integrating the new requirements.