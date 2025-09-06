💻 Sprint 1 Implementation Plan – Family Expense Tracker
1. Scope of Sprint 1 (MVP)

Stories included:

Family Dashboard

Expense CRUD

Role-Based Permissions

Secure Login

2. Technical Breakdown
🔑 Secure Login (Foundation First)

Backend:

Use Auth0 (fast integration) or custom OAuth2 server.

JWT tokens issued with role claims.

Refresh token flow implemented.

Frontend:

React (Web) & React Native (Mobile).

Token stored securely (HttpOnly cookies for Web, SecureStorage for Mobile).

DB Changes:

User table → id, familyId, role, email, passwordHash.

Priority: 🚀 Must be first → other stories depend on authentication.

🛡️ Role-Based Permissions

Backend:

Middleware checks JWT claims → enforce RBAC.

Role table + mapping (Parent, Partner, Teen, Child).

Frontend:

UI guards (hide/disable restricted features).

Parent-only role management screen.

DB Changes:

roles table linked to userId.

Dependency: Relies on Secure Login.

📊 Family Dashboard

Backend:

Dashboard API aggregates:

Expenses (from Expense Service)

Savings (placeholder for Goals)

Cache results for performance.

Frontend:

Responsive dashboard layout.

Role-based views (Parent sees budgets, Child sees savings only).

DB Changes:

None (uses expense table).

Dependency: Requires Expense CRUD.

📝 Expense CRUD

Backend:

Expense service with endpoints:

POST /expenses

GET /expenses

PUT /expenses/{id}

DELETE /expenses/{id}

Schema: id, familyId, category, amount, date, notes, createdBy.

Frontend:

Expense entry form + expense list view.

Role-based access (Parents/Partners can add/edit/delete, Kids read-only).

DB Changes:

expenses table.

Dependency: None (can start in parallel with Login).

3. Sprint 1 Architecture Snapshot
flowchart TD
    subgraph Frontend
        A[Login Screen] --> B[Dashboard UI]
        B --> C[Expense Entry Form]
        B --> D[Expense List]
    end

    subgraph Backend
        E[Auth Service] --> F[Role Middleware]
        F --> G[Dashboard API]
        F --> H[Expense API]
    end

    subgraph Database
        I[(Users Table)]
        J[(Roles Table)]
        K[(Expenses Table)]
    end

    A --> E
    E --> I
    E --> J
    G --> K
    H --> K
    B --> G
    C --> H
    D --> H

4. Sprint 1 Deliverables

Working login system with role enforcement.

Functional family dashboard with expense listing.

Expense CRUD with role-based restrictions.

Secure storage & unit + integration tests.

5. Risks & Mitigation

Auth complexity → mitigate by using Auth0 for v1, migrate later if needed.

RBAC bugs → add automated tests for each role.

Cross-platform UI differences → start with shared React components.