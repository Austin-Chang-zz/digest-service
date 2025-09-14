📄 Sprint 1 Story Draft – Family Expense Tracker (v0.92.0)

Scope: MVP Onboarding + QR Invites
Sprint Goal: Enable new users to create accounts, authenticate securely, set up a family group, and invite members via QR code.

🏁 Sprint 1 Epics Covered

Epic 0: Account Creation & Onboarding

Epic 1: Authentication & Security (subset)

Epic 2: Group Management & Dashboard (subset: QR invites, preview, sharing)

📌 User Stories
🚀 Epic 0: Account Creation & Onboarding

Story 0.1 – Account Creation Page

As a new user, I want to enter my first name, last name, persona, and group name, so that I can start setting up my family account.

Story 0.2 – Host/Owner Definition

As a host, I want to be marked as the group manager, so that I can invite and manage members.

Story 0.3 – Add Members Placeholder

As a host, I want a “+ Add Member” placeholder, so that I can visually prepare for future group members.

Story 0.4 – Current Member Display

As a host, I want to see a list of current members with a checkbox (all joined), so I can confirm my group is complete.

Story 0.5 – RWD Onboarding Page

As a mobile user, I want the account creation page to be responsive, so that it works across phone, tablet, and desktop.

🔐 Epic 1: Authentication & Security (Subset)

Story 1.1 – Secure Login (MVP)

As a user, I want to log in with email + password, so I can access my account securely.

Story 1.2 – Social Login Integration (Google)

As a user, I want to sign in with Google, so that I can onboard quickly without creating a new password.

Story 1.3 – Email Verification (6-digit code)

As a new user, I want to receive a 6-digit code by email, so I can confirm my account securely.

Story 1.4 – Localized Login/Registration Messages

As a user, I want login and error messages in my language, so I can understand them clearly.

👥 Epic 2: Group Management & Dashboard (Subset: QR Invites)

Story 2.1 – Generate QR Code for Group Invite

As a host, I want to generate a QR code containing group details, so that others can join easily.

Story 2.2 – QR Auto-Join (Scan & Fill)

As a member, I want to scan a QR code to auto-fill group + owner info, so I can join a family group quickly.

Story 2.3 – Invite Preview Modal

As a host, I want a preview modal with invite message + QR code, so I can share/screenshot/print the invite.

Story 2.4 – Multi-Channel Invite Sharing (MVP)

As a host, I want to share the invite by email, copy, WhatsApp, and Telegram, so I can invite members via their preferred channel.

Story 2.5 – RWD Group Management UI

As a user, I want the group management and QR invite features to be responsive, so that they work on any device.

📊 Acceptance Criteria

✅ Onboarding

User can create an account with group + persona details.

Host is clearly marked as group manager.

Member placeholders visible.

Current members list + checkbox functional.

✅ Authentication

Login with email + password works.

Google login works.

Email verification (6-digit code) functional.

Login/register messages available in EN, ZH-TW, ZH-CN, JA, ES.

✅ Group Management (QR Invites)

Host can generate QR with group details.

Members can scan QR to auto-join.

Invite preview modal works.

Sharing options functional (Email, Copy, WhatsApp, Telegram).

UI responsive for mobile/tablet/desktop.

📅 Sprint Goal Definition

At the end of Sprint 1, a family can:

Create an account (with language & responsive support).

Authenticate securely (Google + Email/Password + 2FA).

Create a family group.

Invite members via QR code (multi-channel, preview modal).

Have a fully functional MVP onboarding flow.