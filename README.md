# Anther

Anther is a proposed Kenyan healthcare marketplace that helps patients find and book verified healthcare professionals for care at home and selected online consultations.

The project is in its research and planning stage. It is not a medical emergency service and must not be used to delay emergency care.

## The problem

Patients and families can struggle to find trusted, convenient healthcare support outside a hospital setting. Anther aims to make it easier to discover appropriate providers, request care, and manage appointments in one place.

## Planned services

- Home nursing
- Physiotherapy
- Elderly care
- Post-surgery care
- Wound care
- Medication assistance
- Online consultation
- Hospital-at-home support

## Phase One MVP

The first release will focus on the essential booking journey:

1. Patients create an account and manage their profile.
2. Verified providers create profiles and list available services.
3. Patients browse services and submit appointment requests.
4. Providers or administrators confirm and manage appointments.
5. Appointments progress through `PENDING`, `CONFIRMED`, `IN_PROGRESS`, and `COMPLETED`.
6. Patients receive booking and status notifications.

Live location tracking, in-app payments, video consultations, chat, medical-record uploads, and provider payouts are planned for later phases unless the team formally brings them into the MVP.

## Proposed technology

The team is evaluating the following beginner-friendly architecture:

- **Mobile app:** Flutter
- **Backend platform:** Supabase
- **Database:** PostgreSQL
- **Authentication and authorization:** Supabase Auth and Row Level Security
- **Notifications:** Firebase Cloud Messaging
- **Maps and location:** Google Maps Platform (future phase)

This stack is still subject to team sign-off. Do not introduce a second backend or database design without an agreed architecture decision.

## Safety, privacy, and compliance

Healthcare information is sensitive. The project will be designed around least-privilege access, verified provider onboarding, secure authentication, auditability, and protected file storage.

Before production use, the team must confirm applicable Kenyan digital-health, practitioner-licensing, and data-protection obligations with current official sources and appropriate professional guidance. No provider should be presented as verified until the agreed verification process is complete.

## Repository standards

- Do not commit passwords, API keys, access tokens, service-account files, or patient data.
- Put local secrets in `.env` files and provide only `.env.example` templates.
- Work in a feature branch named `codex/<short-description>` or `feature/<short-description>`.
- Open a pull request for review before merging into `master`.
- Keep commits focused and describe the change clearly.
- Treat mockup names, people, addresses, and payments as demo data only.

## Suggested project structure

```text
anther/
├── mobile/        # Flutter patient application
├── admin/         # Future provider and administrator dashboard
├── supabase/      # Database migrations, policies, and edge functions
├── docs/          # Product decisions, diagrams, and setup guides
└── README.md
```

## Getting started

Development will begin after the team agrees on:

1. The Phase One feature list.
2. A single canonical database schema.
3. Provider-verification requirements and workflow.
4. The technology stack and account ownership.
5. Security and data-handling requirements.

## Team

Project contributors will be added as the project moves from research into implementation.

## Status

Research and compliance review in progress. Development has not yet started.
