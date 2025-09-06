flowchart TD
    %% Core MVP
    E1[Epic 1: Core Expense Management] --> E2[Epic 2: Role-Based Access & Dashboard]

    %% Value-Add
    E2 --> E3[Epic 3: Goals & Savings]
    E2 --> E4[Epic 4: Allowances & Chores]

    %% Engagement
    E3 --> E5[Epic 5: Gamification & Education]
    E4 --> E5

    %% Security & Notifications
    E1 --> E6[Epic 6: Notifications & Security]
    E2 --> E6
    E3 --> E6
    E4 --> E6
    E5 --> E6

    %% Story-level dependencies (examples)
    S1[Story: Expense CRUD] --> S2[Story: Budget Alerts]
    S1 --> S3[Story: Bank Sync]
    S3 --> S2
    S4[Story: Role-Based Permissions] --> S5[Story: Parental Controls]
    S2 --> S5
