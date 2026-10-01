# Requirements and Acceptance Criteria — Zestion

[English](requirements.md) | [Português](../pt-BR/requisitos.md)

## Product Goal

Provide players with a secure and accessible web space to create, maintain, and use Ruptura RPG character sheets while applying the system's progression and calculation rules consistently.

## Actors

- **Visitor:** can register, log in, confirm an email, and recover a password.
- **Player:** can manage only their own characters, sheets, portraits, skills, and game tools.
- **Game Master:** planned actor who will manage campaign content and online sessions.

## Current Functional Requirements

| ID | Requirement | Acceptance Criterion |
|---|---|---|
| FR-001 | Register an account | A visitor can submit valid registration data and receive the configured confirmation flow |
| FR-002 | Authenticate a user | Valid credentials grant access to the protected dashboard |
| FR-003 | Recover a password | A registered user can request recovery and define a new password |
| FR-004 | Protect private routes | Unauthenticated access to the dashboard redirects to authentication |
| FR-005 | End a session | Logout invalidates the active session and returns the user to authentication |
| FR-006 | List characters | A player sees only characters associated with their user account |
| FR-007 | Create characters | A player can create more than one character |
| FR-008 | Edit and save a sheet | Valid changes persist and remain after reloading |
| FR-009 | Delete a character | The selected character is removed only after an explicit user action |
| FR-010 | Manage portraits | A player can upload a supported private portrait for their character |
| FR-011 | Enforce level-one restrictions | A level-one character cannot select a class |
| FR-012 | Unlock classes | Class selection becomes available from level two |
| FR-013 | Validate point budgets | Attribute, proficiency, and progression choices cannot exceed their available limits |
| FR-014 | Calculate derived values | HP, Sanity, Defense, Initiative, and Carrying Capacity follow the current rules |
| FR-015 | Apply bonuses | Species, class, and passive-skill bonuses update the relevant sheet values |
| FR-016 | Manage skill trees | A player can select only skills allowed by level, tier, requirements, and available points |
| FR-017 | Persist skill choices | Valid tree selections remain linked to the correct character |
| FR-018 | Manage inventory and notes | A player can save inventory, equipment, and character information |
| FR-019 | Roll dice | A player can roll supported dice and view individual results and totals |
| FR-020 | Read game rules | Players can access the current General Rules / How to Play content |

## Current Non-Functional Requirements

| ID | Requirement | Acceptance Criterion |
|---|---|---|
| NFR-001 | Data isolation | Reads and writes are scoped to the authenticated user and reinforced by database RLS |
| NFR-002 | Upload security | Portrait uploads validate origin, size, and actual file content |
| NFR-003 | Session protection | Authentication cookies use appropriate security attributes |
| NFR-004 | Responsiveness | Main player flows remain usable on desktop and mobile layouts |
| NFR-005 | Accessibility | Primary controls are labeled, keyboard reachable, and expose status feedback where applicable |
| NFR-006 | Error handling | Expected failures display understandable feedback without exposing sensitive details |
| NFR-007 | Privacy | Public documentation and evidence contain no credentials or player data |

## Planned Requirements

| ID | Planned Requirement |
|---|---|
| GM-001 | Provide a dedicated Game Master workspace |
| GM-002 | Allow campaign document management |
| GM-003 | Allow private notes organized by campaign or session |
| OS-001 | Allow a Game Master to create an online session |
| OS-002 | Generate invitations for players |
| OS-003 | Allow invited players to join a session |
| OS-004 | Require each player to select one of their existing characters |
| OS-005 | Allow the Game Master to access the sheets selected for that session |
| OS-006 | Protect session membership, permissions, and private information |
| OS-007 | Keep participant and selected-character information updated during the session |

## Out of Scope for the Current MVP

- Public sharing of private character sheets;
- Game Master management features;
- Online session rooms;
- Real-time combat automation;
- Payment or subscription processing.
