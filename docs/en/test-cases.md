# Test Cases — Zestion

[English](test-cases.md) | [Português](../pt-BR/casos-de-teste.md)

## Scope

Authentication, protected access, character management, sheet rules, progression, class skill trees, portrait uploads, dice rolling, responsiveness, accessibility, and security controls.

## Status Guide

- **Confirmed:** behavior reported as working in the deployed MVP; formal evidence is still being organized.
- **Automated coverage:** the private source repository contains an automated test for the control.
- **Pending formal run:** requires a documented execution with environment details and evidence.
- **Not implemented:** roadmap functionality and not a defect in the current MVP.

## Preconditions

- Production URL is available;
- Test email access is available for confirmation and recovery;
- At least two test users are available for isolation scenarios;
- No real player data is used.

## Test Cases

| ID | Requirement | Scenario | Main Steps | Expected Result | Status |
|---|---|---|---|---|---|
| ZES-AUTH-001 | FR-001 | Register with valid data | Open registration, enter valid data, submit | Account is created and the configured confirmation flow starts | Confirmed |
| ZES-AUTH-002 | FR-002 | Log in with valid credentials | Enter confirmed credentials and submit | Protected dashboard opens | Confirmed |
| ZES-AUTH-003 | FR-002 | Reject invalid credentials | Submit an invalid email/password combination | Access is denied and a safe message is displayed | Pending formal run |
| ZES-AUTH-004 | FR-004 | Block unauthenticated dashboard access | Open a protected URL without a session | User is redirected to authentication | Confirmed |
| ZES-AUTH-005 | FR-005 | Log out | Select logout from an authenticated page | Session ends and protected content is no longer available | Confirmed |
| ZES-AUTH-006 | FR-003 | Recover password | Request recovery, open the email link, define a new password | New password is accepted and can be used to log in | Confirmed |
| ZES-AUTH-007 | FR-001 | Register an existing email | Submit an email already registered | Account duplication is prevented without exposing sensitive information | Pending formal run |
| ZES-CHAR-001 | FR-007 | Create a character | Select create character | A new character opens and appears in the player's list | Confirmed |
| ZES-CHAR-002 | FR-007 | Create multiple characters | Create more than one character | All characters appear independently | Confirmed |
| ZES-CHAR-003 | FR-008 | Save valid sheet changes | Edit valid fields and save | Success feedback appears and data is stored | Confirmed |
| ZES-CHAR-004 | FR-008 | Preserve changes after reload | Save changes and reload the page | Saved values remain unchanged | Confirmed |
| ZES-CHAR-005 | FR-009 | Delete a character | Select delete and confirm the explicit action | Correct character is removed from the list | Confirmed |
| ZES-CHAR-006 | FR-006 / NFR-001 | Isolate characters between users | Compare two test accounts and attempt direct access | Each account sees only its own characters | Pending formal run |
| ZES-CHAR-007 | FR-010 | Upload a valid portrait | Upload a supported image within the limit | Portrait is stored privately and displayed | Confirmed |
| ZES-CHAR-008 | NFR-002 | Reject unsupported portrait content | Attempt an invalid or spoofed image upload | Upload is rejected safely | Automated coverage |
| ZES-SHEET-001 | FR-011 | Keep class locked at level 1 | Set character to level 1 | Class selection remains unavailable or is cleared | Confirmed |
| ZES-SHEET-002 | FR-012 | Unlock class at level 2 | Change level from 1 to 2 | Class selection becomes available | Confirmed |
| ZES-SHEET-003 | FR-013 | Enforce attribute budget | Attempt to exceed available attribute points | Save is prevented with understandable feedback | Confirmed |
| ZES-SHEET-004 | FR-013 | Enforce proficiency budget and limits | Attempt an invalid proficiency distribution | Save is prevented with understandable feedback | Confirmed |
| ZES-SHEET-005 | FR-014 | Calculate derived values | Change attributes that affect derived values | HP, Sanity, Defense, Initiative, or Carrying Capacity update according to rules | Confirmed |
| ZES-SHEET-006 | FR-015 | Apply species bonuses | Select a species with bonuses | Correct bonuses appear without consuming distributed points | Confirmed |
| ZES-SHEET-007 | FR-015 | Apply class and passive bonuses | Select a valid class/passive combination | Relevant totals update according to the rules | Confirmed |
| ZES-SHEET-008 | FR-018 | Save inventory and notes | Enter inventory, equipment, and character information and save | Content remains linked to the character | Confirmed |
| ZES-SKILL-001 | FR-016 | Access a valid class tree | Use a level 2+ character with a class | Correct class tree opens | Confirmed |
| ZES-SKILL-002 | FR-016 | Enforce tier gates | Attempt to select a locked-tier node | Selection is blocked and requirements remain visible | Confirmed |
| ZES-SKILL-003 | FR-016 | Enforce skill prerequisites and cost | Attempt an invalid selection | Invalid combination is rejected | Confirmed |
| ZES-SKILL-004 | FR-017 | Persist valid skill choices | Select valid nodes, return to the sheet, and reopen the tree | Choices remain selected for the same character | Confirmed |
| ZES-SKILL-005 | FR-015 | Reflect passive effects on the sheet | Select a passive that changes a total | Character sheet shows the correct updated value | Confirmed |
| ZES-DICE-001 | FR-019 | Roll every supported die | Roll D4, D6, D8, D10, D12, D20, and D100 | Every result is within the selected die range | Confirmed |
| ZES-DICE-002 | FR-019 | Roll multiple dice | Choose quantity greater than one and roll | Individual results and correct total are displayed | Confirmed |
| ZES-DICE-003 | FR-019 | Enforce quantity limit | Attempt to go below 1 or above 20 dice | Controls keep the quantity within the allowed range | Confirmed |
| ZES-UX-001 | NFR-004 | Use critical flows on mobile layout | Run authentication, character, sheet, tree, and dice flows on mobile | No clipped, overlapping, or unreachable critical controls | Pending formal run |
| ZES-UX-002 | NFR-005 | Navigate primary controls by keyboard | Use Tab, Shift+Tab, Enter, and Space | Focus is visible and controls are operable in a logical order | Pending formal run |
| ZES-UX-003 | NFR-006 | Display safe error feedback | Trigger expected authentication, save, and upload failures | Clear feedback appears without technical or sensitive details | Pending formal run |
| ZES-SEC-001 | NFR-002 | Reject untrusted upload origins | Send portrait requests from missing or untrusted origins | Requests are rejected | Automated coverage |
| ZES-SEC-002 | NFR-002 | Validate real image signature | Declare a misleading MIME type or submit unsafe content | Only supported JPEG, PNG, or WebP signatures are accepted | Automated coverage |
| ZES-SEC-003 | NFR-002 | Reject oversized upload bodies | Submit a body above the configured limit | Request is rejected even without `Content-Length` | Automated coverage |
| ZES-SEC-004 | NFR-003 | Protect authentication cookies | Create a Supabase session | Cookies use `HttpOnly`, `SameSite=Lax`, and production `Secure` | Automated coverage |
| ZES-GM-001 | GM-001–GM-003 | Access Game Master area | Select the Game Master option | Feature remains identified as under development | Not implemented |
| ZES-OS-001 | OS-001–OS-007 | Create and join an online session | Attempt the planned session flow | Feature is not available in the current MVP | Not implemented |

## Initial Execution Record

| Date | Version | Environment | Result |
|---|---|---|---|
| October 1, 2026 | Production MVP | Production URL; browser and device details not formally recorded | Implemented player flows reported as functional; formal evidence cycle pending |

## Evidence Template

For each formal execution, record:

- Date and application version;
- Browser, version, operating system, and device;
- Test case ID;
- Expected and actual result;
- Status;
- Screenshot or recording without personal data;
- Defect ID when applicable.
