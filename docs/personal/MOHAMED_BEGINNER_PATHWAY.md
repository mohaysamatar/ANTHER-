# Mohamed Beginner Pathway

This is a practical pathway for Mohamed's Anther role: security, quality assurance, integration, notifications, and release support. It assumes you are a first-year cybersecurity student and new to full-stack development.

The aim is not to learn everything before contributing. Learn one small concept, use it on Anther, ask for a cross-check, then move forward.

## Your role in plain language

You help make sure Anther is safe, testable, and reliable.

- **Security:** decide who can access what, protect sensitive information, and stop common mistakes such as exposing passwords or patient data.
- **QA:** test whether each feature works and report bugs clearly.
- **Integration:** check that the Flutter app, Supabase database, and notifications work together.
- **Notifications:** later help send safe appointment reminders and status updates.
- **Release support:** help verify the app is ready before it is shared with users.

You are not expected to build the whole backend or app alone. Your first deliverables are documentation, checklists, and small test exercises that help the whole team build safely.

## Baseline weekly timetable

Use four focused sessions each week. Adjust the days if your class schedule requires it, but keep the order.

| Session | Time | Purpose |
| --- | --- | --- |
| Session 1 | Monday, 19:00-20:30 EAT | Learn one concept and take structured notes. |
| Session 2 | Wednesday, 19:00-20:30 EAT | Practise in a small safe example or Anther branch. |
| Session 3 | Friday, 19:00-20:30 EAT | Complete an Anther file, test it, and request a cross-check. |
| Session 4 | Saturday, 10:00-11:00 EAT | Review feedback, update your checklist, and plan the next session. |

Do not work on a feature until its GitHub issue says what success looks like. Work on your own branch and commit small changes locally.

## Week 0 - prepare your working environment

### Learn

- [ ] Understand the difference between Git (your local history) and GitHub (the shared remote repository).
- [ ] Learn `git status`, `git pull`, `git switch -c`, `git add`, `git commit`, `git diff`, and `git push`.
- [ ] Learn what a branch, commit, pull request, merge conflict, `.gitignore`, and `.env` file are.
- [ ] Install or confirm access to VS Code, Flutter, Git, a GitHub account, and a password manager.

### Apply to Anther

- [ ] Read `README.md`, `docs/WORKFLOW.md`, and `docs/TEAM_CHECKLIST.md`.
- [ ] Create a test branch named `feature/mohamed-git-practice`.
- [ ] Add a small note in `docs/personal/learning-log.md` explaining what you learned about branches and commits.
- [ ] Practise making one local commit. Do not push without the project-owner approval gate.

### Completion check

- [ ] You can explain why secrets and `.env` files must never be committed.
- [ ] You can create a branch, make a change, view the diff, and make a commit.

## Week 1 - understand Anther before securing it

### Learn

- [ ] Learn the client-server model: Flutter app -> Supabase API -> PostgreSQL database.
- [ ] Learn the difference between authentication (who you are) and authorization (what you may do).
- [ ] Learn the four initial Anther roles: patient, provider, admin, and verification reviewer.
- [ ] Learn why health and provider-verification data is sensitive.

### Apply to Anther

- [ ] Read the MVP scope, user flows, canonical schema, and provider-verification workflow when they are created.
- [ ] Create `docs/security/data-classification.md`.
- [ ] List each data category: account details, appointment details, addresses, provider credentials, medical records, payment references, and system logs.
- [ ] Label each category as public, internal, confidential, or highly sensitive.
- [ ] State who should be allowed to access each category.

### Ask for support

- [ ] Ask Najib to explain how Supabase Auth and Row Level Security will enforce your access rules.
- [ ] Ask Salah to explain exactly when a provider becomes verified and visible.
- [ ] Ask Abdikhalaq to show you the patient booking flow from the user’s point of view.

### Completion check

- [ ] You can explain the difference between a logged-in provider and a verified provider.
- [ ] You can identify at least three data types that must never be public.

## Week 2 - build the security baseline and threat model

### Learn

- [ ] Learn the CIA triad: confidentiality, integrity, and availability.
- [ ] Learn common beginner-level risks: weak passwords, leaked API keys, broken access control, insecure file links, unvalidated input, and excessive logging.
- [ ] Learn the idea of least privilege: give each role only the permissions it needs.

### Apply to Anther

- [ ] Create `docs/security/threat-model.md`.
- [ ] Create `docs/security/security-baseline.md`.
- [ ] Document at least these scenarios: a patient tries to read another patient's appointment, an unverified provider tries to receive bookings, a public link exposes a document, and a secret is accidentally committed.
- [ ] For each scenario, describe the likely control: Row Level Security, verification state checks, private storage rules, or secret scanning.
- [ ] Add the team's no-real-data and no-secrets rules to the security baseline.

### Ask for support

- [ ] Ask Najib to review whether the security controls are possible in the planned schema and Supabase policies.
- [ ] Ask Salah to verify that the provider workflow has enough approval/rejection states.

### Completion check

- [ ] You can explain why frontend checks alone are not enough to protect data.
- [ ] You can describe one security control for each listed threat.

## Week 3 - learn practical testing and write the QA plan

### Learn

- [ ] Learn the difference between unit tests, integration tests, manual tests, regression tests, and security tests.
- [ ] Learn how to write a test case with a precondition, steps, expected result, actual result, and evidence.
- [ ] Learn how to write a useful bug report: title, environment, steps to reproduce, expected result, actual result, impact, and screenshot or log if safe.

### Apply to Anther

- [ ] Create `docs/qa/test-plan.md`.
- [ ] Create `docs/qa/acceptance-checklist.md`.
- [ ] Write test cases for sign-up, sign-in, invalid form input, logout, appointment request, appointment status display, and role-based access.
- [ ] Write negative tests: wrong password, missing required fields, invalid status change, unavailable provider, and a patient attempting to access another patient's data.
- [ ] Create a GitHub issue template for bugs if the team approves it.

### Ask for support

- [ ] Ask Abdikhalaq to identify the expected screen behaviour for each test.
- [ ] Ask Najib to identify expected API/database behaviour for each test.

### Completion check

- [ ] Another teammate can run your test case without asking you what it means.
- [ ] Each test has a clear pass or fail condition.

## Week 4 - practise Flutter and app-level testing

### Learn

- [ ] Learn basic Dart: variables, functions, classes, null safety, lists, maps, and `async` / `await`.
- [ ] Learn Flutter basics: widgets, `MaterialApp`, navigation, forms, `TextFormField`, validators, and state.
- [ ] Learn how Flutter unit and widget tests are organized.

### Apply to Anther

- [ ] Pair with Abdikhalaq to run the Flutter app locally.
- [ ] Add one basic widget test in `mobile/test/` for a form-validation rule once the login or booking screen exists.
- [ ] Test at least one invalid input and one successful input.
- [ ] Record results in `docs/qa/week-4-results.md`.

### Completion check

- [ ] You can run the project’s test command and read whether it passed or failed.
- [ ] You can explain what one widget test is checking.

## Week 5 - test Supabase authorization safely

### Learn

- [ ] Learn PostgreSQL basics: tables, rows, primary keys, foreign keys, and queries.
- [ ] Learn how Supabase Row Level Security policies restrict reading, inserting, updating, and deleting data.
- [ ] Learn why authorization must be enforced by the database or backend, not only hidden in the app interface.

### Apply to Anther

- [ ] With Najib, create fictional patient, provider, admin, and reviewer accounts in the development environment.
- [ ] Run the role-access tests from `docs/qa/acceptance-checklist.md`.
- [ ] Confirm a patient can access only their own appointments and profile.
- [ ] Confirm an unverified provider cannot become searchable or accept appointments.
- [ ] Confirm only authorized reviewers/admins can access provider-verification evidence.
- [ ] Record passing and failing results in `docs/qa/week-5-results.md`.

### Completion check

- [ ] You have evidence for each role test: test data used, action attempted, and actual result.
- [ ] Failed authorization tests are logged as GitHub issues before a push is requested.

## Week 6 - integration and notification design

### Learn

- [ ] Learn what an API request and response are, including success and error responses.
- [ ] Learn the purpose of Firebase Cloud Messaging and why notification content must avoid unnecessary health details.
- [ ] Learn the difference between an in-app notification record and a device push notification.

### Apply to Anther

- [ ] Create `docs/notifications/notification-plan.md`.
- [ ] Define the MVP events: appointment requested, confirmed, changed, cancelled, reminder, and completed.
- [ ] Write privacy-safe notification examples, such as “Your appointment status has changed” instead of including diagnosis or treatment details.
- [ ] Create a notification test checklist before implementation begins.
- [ ] Pair with Najib to trace one appointment-status change from database to Flutter screen.

### Completion check

- [ ] Every notification has an event, recipient, safe message, and test case.
- [ ] No notification includes a diagnosis, medical record, or unnecessary precise address.

## Week 7 - release readiness and repeatable quality checks

### Learn

- [ ] Learn the difference between development, test, and production environments.
- [ ] Learn release checklists, regression testing, versioning, and rollback planning.
- [ ] Learn basic performance checks: slow screen, failed request, repeated request, and offline/error state.

### Apply to Anther

- [ ] Create `docs/qa/release-checklist.md`.
- [ ] Include account creation, login, booking, authorization, error handling, and data-privacy checks.
- [ ] Add a checklist item to verify no development keys, debug information, or fictional test accounts are accidentally exposed in a release.
- [ ] Run a small regression test after each major merged feature.

### Completion check

- [ ] The team can use your checklist to make a clear go/no-go decision.
- [ ] Each release issue has a documented owner and resolution or acceptance decision.

## Your routine for every Anther task

1. Read the GitHub issue and acceptance criteria.
2. Confirm the files you are expected to change.
3. Create or switch to your branch.
4. Make one small, focused change.
5. Run the relevant test or manual check.
6. Review your own diff for secrets, personal data, broken formatting, and unrelated edits.
7. Use the `WORK COMPLETE - awaiting cross-check` template in `docs/WORKFLOW.md`.
8. Ask the named teammate to cross-check your work.
9. Resolve feedback and request project-owner approval before pushing.

## What to defer for now

- Do not attempt penetration testing against real services or accounts.
- Do not use real patient records, provider credentials, payment information, or addresses.
- Do not implement live tracking, payments, video calls, chat, or medical-record uploads until the team formally approves them for the MVP.
- Do not create or share API keys in chat, commits, screenshots, or documentation.

## First session - start here

At your next Monday session, complete only these steps:

- [ ] Read the three existing project documents in `docs/`.
- [ ] Create the practice branch.
- [ ] Add `docs/personal/learning-log.md` with three short notes: what Git is, what a branch is, and why `.env` files are private.
- [ ] Make one local commit.
- [ ] Send a completion update for cross-checking. Do not push until approval is given.
