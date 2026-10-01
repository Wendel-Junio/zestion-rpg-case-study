# QA Report — Zestion

[English](qa-report.md) | [Português](../pt-BR/relatorio-qa.md)

## 1. Executive Summary

Zestion is a functional web MVP with a broad player flow and complex business rules. The current documentation identifies the implemented scope, defines acceptance criteria, and establishes a traceable test baseline without exposing private source code or player data.

The strongest QA value of the project is the combination of authentication, private data, character CRUD operations, rule-driven calculations, progression constraints, class skill trees, file uploads, and interactive 3D behavior.

## 2. Current Assessment

### Confirmed Strengths

- Protected authentication and player dashboard;
- Multiple characters per account;
- Persistent character sheets;
- Automatic calculations and bonuses;
- Level, point-budget, tier, and prerequisite restrictions;
- Private portrait workflow;
- 3D dice rolling;
- Explicit Game Master roadmap;
- Security-focused automated tests in the private source repository;
- Clear separation between current features and planned functionality.

### Evidence Maturity

Core player features have been reported as functional in production. A formal evidence cycle is still required to record browser versions, devices, screenshots, and actual results for each case. Until that cycle is complete, confirmed statuses should not be interpreted as independent certification or complete regression coverage.

## 3. Test Strategy

| Level | Purpose |
|---|---|
| Functional | Verify that users complete authentication and character-management flows |
| Business rules | Validate calculations, limits, progression, bonuses, tiers, and prerequisites |
| Negative | Verify safe behavior for invalid credentials, invalid values, and failed operations |
| Security | Validate upload boundaries, session cookies, data isolation, and safe errors |
| Responsive | Verify critical flows across viewport sizes and touch interaction |
| Accessibility | Verify labels, focus order, keyboard operation, and status announcements |
| Regression | Recheck critical flows after rule or feature changes |

## 4. Main Product Risks

| ID | Area | Priority | Risk | Recommendation |
|---|---|---:|---|---|
| QA-001 | Access control | Critical | A player could access another user's sheet if application queries or RLS are misconfigured | Execute a two-account authorization test and retain database RLS verification |
| QA-002 | Business rules | High | Rule changes may break calculations or invalidate saved sheets | Create unit tests for every derived value and progression constraint |
| QA-003 | Authentication | High | Email confirmation or recovery may behave differently across providers or environments | Run repeatable end-to-end authentication tests |
| QA-004 | Uploads | High | Invalid or oversized portraits may affect security or storage | Keep current automated controls and add integration tests against storage |
| QA-005 | Regression | High | New classes, species, and skills may break existing characters | Create a versioned regression pack with representative characters |
| QA-006 | Accessibility | Medium | Complex sheets and skill trees may be difficult to use by keyboard or assistive technology | Perform keyboard, focus, semantics, and screen-reader checks |
| QA-007 | Mobile UX | Medium | Dense forms and tree nodes may become difficult to use on small screens | Execute device-based tests and record screenshots |
| QA-008 | Compatibility | Medium | Three.js behavior may differ across browsers and GPUs | Test Chrome, Firefox, Edge, Safari/mobile, and reduced-motion behavior |
| QA-009 | Evidence | Medium | Portfolio claims may lack reproducible environment details | Record each formal run with version, device, browser, and evidence |
| QA-010 | Online sessions | Future high | Session invitations and shared sheet access will introduce new permission risks | Define authorization rules and threat scenarios before implementation |

## 5. Defect Classification

- **Defect:** implemented behavior differs from a defined requirement.
- **Improvement:** current behavior works but can provide a better experience.
- **Risk:** a condition that may produce future impact or failure.
- **Planned feature:** explicitly outside the current MVP and therefore not a defect.

## 6. Suggested Formal Test Cycle

1. Create two isolated test accounts;
2. Record environment and deployed version;
3. Execute authentication and password-recovery cases;
4. Create representative level 1 and level 2+ characters;
5. Validate every derived value against an independent calculation;
6. Exercise valid and invalid skill-tree paths;
7. Verify cross-user authorization;
8. Run portrait negative cases in a controlled environment;
9. Test keyboard navigation and mobile layouts;
10. Attach sanitized evidence and open defects when needed;
11. Re-run critical cases after corrections.

## 7. Roadmap Quality Gates

Before releasing the Game Master and online-session features:

- Define actors, permissions, invitation lifecycle, and session states;
- Decide whether Game Master sheet access is read-only or editable;
- Define when player access can be revoked;
- Prevent users from joining sessions without a valid invitation;
- Scope every query by authenticated user and session membership;
- Add audit-friendly records for invites and selected characters;
- Test concurrent updates and disconnected participants;
- Define privacy expectations for notes, documents, and sheets.

## Conclusion

Zestion already offers a strong portfolio case for QA, product analysis, front-end behavior, authentication, and business-rule testing. Its next quality milestone is not adding more claims, but creating a repeatable formal execution cycle with sanitized evidence and automated regression for the most critical rules.
