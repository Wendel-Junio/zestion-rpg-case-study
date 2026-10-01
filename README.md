# Zestion RPG — QA and Product Case Study

[English](README.md) | [Português](README.pt-BR.md)

A bilingual QA and product case study for **Zestion**, a functional web MVP for creating, managing, and evolving character sheets for the original **Ruptura** tabletop RPG system.

This public repository contains documentation and testing evidence only. The application source code remains in a private repository.

## Live Application

[https://zestion-rpg.com.br/](https://zestion-rpg.com.br/)

## Project Overview

Zestion combines authentication, private user data, character management, progression rules, class skill trees, portrait uploads, and a 3D dice roller. The project is under continuous development: the current player features are functional, while the Game Master area and online sessions are part of the roadmap.

## Implemented Scope

- Registration, login, email confirmation, password recovery, and logout;
- Protected player dashboard;
- Creation, editing, saving, and deletion of multiple characters;
- Private character sheets and portraits scoped to each user;
- Attributes, proficiencies, HP, Sanity, Defense, Initiative, and Carrying Capacity;
- Species, class, progression, and automatic bonus rules;
- Class skill trees with tiers, requirements, costs, and passive effects;
- Inventory, equipment, notes, and character information;
- 3D dice roller supporting D4, D6, D8, D10, D12, D20, and D100;
- General Rules / How to Play content;
- Responsive web interface.

## QA Documentation

- [Requirements and acceptance criteria](docs/en/requirements.md)
- [Test cases](docs/en/test-cases.md)
- [QA report](docs/en/qa-report.md)
- [Requisitos e critérios de aceite](docs/pt-BR/requisitos.md)
- [Casos de teste](docs/pt-BR/casos-de-teste.md)
- [Relatório de QA](docs/pt-BR/relatorio-qa.md)
- [Evidence guide](evidence/screenshots/README.md)

## Testing Approach

The case study combines:

- Manual functional validation of the production MVP;
- Business-rule testing for calculations, progression, and skill trees;
- Security-focused automated tests in the private source repository;
- Planned formal execution for responsiveness, accessibility, compatibility, and negative scenarios;
- Traceability between requirements, acceptance criteria, and test cases.

Statuses in the test documentation distinguish owner-confirmed behavior from automated coverage and cases still awaiting a formally recorded execution cycle.

## Automated Security Coverage

The private application repository currently includes five automated tests covering:

1. Trusted-origin validation for portrait uploads;
2. Real image-content validation independently from the declared MIME type;
3. Bounded parsing of valid multipart uploads;
4. Oversized body rejection, including requests without `Content-Length`;
5. Supabase session cookies using `HttpOnly`, `SameSite=Lax`, and `Secure` in production.

## Roadmap

### Game Master Area

- Dedicated Game Master workspace;
- Campaign document management;
- Private notes;
- Centralized world, adventure, and session information.

### Online Sessions

- Session creation and player invitations;
- Players joining through an invitation;
- Selection of an existing character when entering;
- Game Master access to the sheets selected by participants;
- Session membership and permission rules;
- Character monitoring during the session.

### Quality Evolution

- Formal cross-browser and device test cycles;
- Accessibility checks with keyboard and assistive technology;
- Integration tests for authentication and persistence;
- Automated regression coverage for critical player flows;
- Evidence collection for each formal test cycle.

## Technologies Used by the Product

- React 19;
- TypeScript;
- Next.js 16 and Vinext;
- Tailwind CSS;
- Three.js;
- Supabase Auth, Database, and Storage;
- Cloudflare Workers;
- Git and GitHub.

## Skills Demonstrated

- Requirements analysis and acceptance criteria;
- Manual test design and execution;
- Business-rule and negative testing;
- Security risk analysis;
- Defect and improvement classification;
- Product roadmap planning;
- Bilingual technical documentation;
- Communication between user needs and implementation behavior;
- Responsible use of AI-assisted tools with human review and validation.

## Evidence

Screenshots and execution records will be added incrementally without exposing player data, credentials, private character sheets, or application source code.

---

Zestion is an original project developed for learning, portfolio use, and support for Ruptura tabletop RPG sessions.
