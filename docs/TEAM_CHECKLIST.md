# Anther Team Checklist

Use this checklist with `docs/WORKFLOW.md`. Complete the individual work first, then the linked support and cross-check work. Every item must be associated with a GitHub issue before implementation begins.

## Mohamed - Security, QA, Integration, Notifications, and Releases

### Individual work

- [ ] Create `docs/security/threat-model.md`.
- [ ] List the sensitive data Anther will handle and classify its risk.
- [ ] Define patient, provider, admin, and verification-reviewer access boundaries.
- [ ] Create `docs/security/security-baseline.md` with authentication, secrets, audit logging, storage, and least-privilege requirements.
- [ ] Create `docs/qa/test-plan.md`.
- [ ] Create `docs/qa/acceptance-checklist.md` for login, authorization, bookings, validation errors, and privacy.
- [ ] Create test files in `mobile/test/` as Flutter features become available.
- [ ] Create `docs/qa/week-2-results.md` and log failed checks as GitHub issues.
- [ ] Plan notification requirements and later implement Firebase Cloud Messaging and email notifications.
- [ ] Own integration testing, security testing, performance testing, release checks, and deployment support.

### Support and cross-check work

- [ ] Review `docs/decisions/ADR-001-technology-stack.md` for security implications.
- [ ] Review Najib’s schema and Row Level Security policies for unauthorized data exposure.
- [ ] Verify provider-verification changes keep unapproved providers hidden and create an audit trail.
- [ ] Test the appointment workflow using only fictional demo data.
- [ ] Check Flutter forms for input validation, useful errors, and secure handling of sessions.
- [ ] Cross-check each completed feature against the security baseline before a push is requested.

## Najib - Supabase, Database, API, and Access Control

### Individual work

- [ ] Create `docs/decisions/ADR-001-technology-stack.md` and record the team’s approved technology choice.
- [ ] Create `docs/data/canonical-schema.md` with one agreed set of entities, fields, constraints, and booking statuses.
- [ ] Create `docs/data/er-diagram.md` showing the relationships between users, profiles, providers, services, appointments, bookings, payments, records, and notifications.
- [ ] Create `supabase/migrations/0001_initial_schema.sql`.
- [ ] Create `supabase/migrations/0002_rls_policies.sql`.
- [ ] Create `supabase/seed.sql` with fictional data only.
- [ ] Set up Supabase authentication, PostgreSQL, storage, Edge Functions, backups, and environment-variable templates after the architecture is signed off.
- [ ] Build the database/API contract needed by the Flutter app.

### Support and cross-check work

- [ ] Review Mohamed’s security baseline and confirm every required control can be implemented in Supabase.
- [ ] Review Salah’s booking workflow for database constraints, conflicting bookings, and status-history requirements.
- [ ] Review Abdikhalaq’s screen inventory and user flows to ensure the app requests only data provided by the schema.
- [ ] Verify each Flutter feature uses the approved auth and data contract.
- [ ] Test Row Level Security as each role: patient, provider, admin, and verification reviewer.
- [ ] Cross-check that migrations are reversible where practical and never include real data or secrets.

## Salah - Provider Verification, Services, Availability, and Booking Logic

### Individual work

- [ ] Create `docs/provider-verification/workflow.md`.
- [ ] Create `docs/provider-verification/checklist.md`.
- [ ] Define the provider evidence required, reviewer, verification states, approval/rejection reasons, and re-verification dates.
- [ ] Define how doctor, nurse, physiotherapist, and allied-health verification paths differ.
- [ ] Build the provider-review state workflow in `supabase/functions/provider-verification/`.
- [ ] Ensure providers are not visible or bookable until approved.
- [ ] Define services, provider availability, appointment-request rules, and the MVP booking status flow.
- [ ] Build appointment logic in `supabase/functions/appointments/`.

### Support and cross-check work

- [ ] Review `docs/data/canonical-schema.md` and `docs/data/er-diagram.md` for provider, service, availability, and booking needs.
- [ ] Review Abdikhalaq’s user flows for missing booking states or unclear provider information.
- [ ] Review provider-verification audit requirements with Mohamed.
- [ ] Confirm that pending, confirmed, in-progress, and completed states are represented consistently in the app and database.
- [ ] Test that an unverified provider cannot appear in search results or receive appointments.
- [ ] Cross-check appointment creation for availability conflicts and invalid state transitions.

## Abdikhalaq - Flutter Mobile App, User Experience, and Forms

### Individual work

- [ ] Create `docs/product/screen-inventory.md` from the supplied mockups.
- [ ] Create `docs/product/user-flows.md` for sign-up, service browsing, provider selection, booking, appointment status, and profile management.
- [ ] Mark every screen control as MVP, future phase, or mockup-only.
- [ ] Create `mobile/lib/main.dart` and `mobile/lib/app.dart`.
- [ ] Build routes and the authentication screens in `mobile/lib/features/auth/`.
- [ ] Build service browsing in `mobile/lib/features/services/`.
- [ ] Build appointment request and status views in `mobile/lib/features/appointments/`.
- [ ] Implement responsive layouts, state management, API integration, and form validation.
- [ ] Keep future features such as maps, payments, chat, video, and medical-record uploads disabled until approved for the scope.

### Support and cross-check work

- [ ] Review the canonical schema to identify all data required by each screen.
- [ ] Review the provider-verification workflow to show accurate verification status and prevent booking unavailable providers.
- [ ] Test forms with Mohamed for validation, error states, privacy, and session handling.
- [ ] Test service and appointment screens with Salah for accurate business rules and status labels.
- [ ] Confirm UI labels never imply emergency care, verified status, payment completion, or live tracking when the supporting feature is not active.
- [ ] Cross-check each screen against `docs/product/mvp-scope.md` before implementation.

## Shared work - all four team members

### Before coding

- [ ] Agree the Phase One MVP in `docs/product/mvp-scope.md`.
- [ ] Confirm the technology-stack decision and a single canonical schema.
- [ ] Record unresolved regulatory questions and do not present the app as production-ready until they are resolved.
- [ ] Create and assign GitHub issues with acceptance criteria.
- [ ] Confirm account ownership for GitHub, Supabase, Firebase, and any future maps provider.

### Weekly review

- [ ] Attend the Friday 19:00 EAT weekly sign-off.
- [ ] Review open risks, failed tests, unresolved questions, and scope changes.
- [ ] Update `docs/decisions/weekly-signoff-week-1.md` or `docs/decisions/weekly-signoff-week-2.md` as applicable.
- [ ] Demonstrate only fictional data.
- [ ] Agree the next week’s issue assignments and owners.

### Completion and push gate

- [ ] Owner completes the relevant acceptance criteria and self-check.
- [ ] Owner posts the `WORK COMPLETE - awaiting cross-check` update from `docs/WORKFLOW.md`.
- [ ] A named peer completes the cross-check and records the result.
- [ ] The owner resolves any requested changes.
- [ ] The owner sends the `PUSH APPROVAL REQUEST` with changed files, commits, checks, and cross-check evidence.
- [ ] The project owner replies `APPROVE PUSH` before anything is pushed.
- [ ] After the push, post the repository link and final completion notification.
