# Anther Team Delivery Workflow

This workflow gives the team one shared rhythm for planning, building, reviewing, and releasing Anther. Times use East Africa Time (EAT). The timetable is a proposed baseline for a student team and can be adjusted at the weekly planning meeting.

## Working rules

1. Work only from an assigned GitHub issue with a clear acceptance checklist.
2. Each person works in a separate branch: `feature/<issue-number>-<short-name>`.
3. Every completed task must include a self-check, a peer cross-check, and a written completion update.
4. No code, configuration, or documentation is pushed to GitHub until the project owner gives explicit approval in this chat or in the agreed team channel.
5. Never commit real patient data, provider documents, passwords, API keys, tokens, or `.env` files.

## Team ownership

| Owner | Primary responsibility | Primary folders |
| --- | --- | --- |
| Mohamed | Security, QA, integration, notifications, releases | `docs/security/`, `docs/qa/`, `mobile/test/`, `.github/` |
| Najib | Supabase, database, API, access control | `supabase/`, `docs/data/`, `docs/decisions/` |
| Salah | Provider verification, services, availability, booking logic | `docs/provider-verification/`, `supabase/functions/` |
| Abdikhalaq | Flutter user experience, navigation, forms | `mobile/lib/`, `docs/product/` |

Ownership means one person makes the change; it does not remove peer review.

## Two-week foundation timetable

### Week 1 - agree what will be built

| Day and time | Owner | Files to create or update | Outcome and cross-check |
| --- | --- | --- | --- |
| Monday 19:00-20:00 | All | `docs/product/mvp-scope.md` | Agree the Phase One features and explicitly mark deferred features. All four members approve. |
| Monday 20:00-21:00 | Najib | `docs/decisions/ADR-001-technology-stack.md` | Record the Flutter + Supabase decision, ownership of accounts, and rejected alternatives. Mohamed checks security implications. |
| Tuesday 19:00-20:30 | Najib | `docs/data/canonical-schema.md`, `docs/data/er-diagram.md` | Produce one named set of entities, relationships, validation rules, and booking statuses. Salah checks booking needs; Abdikhalaq checks screen-data needs. |
| Tuesday 20:30-21:30 | Mohamed | `docs/security/threat-model.md`, `docs/security/security-baseline.md` | Identify sensitive data, roles, main threats, controls, and secrets policy. Najib checks that the controls are implementable in Supabase. |
| Wednesday 19:00-20:30 | Salah | `docs/provider-verification/workflow.md`, `docs/provider-verification/checklist.md` | Define the manual verification steps, evidence, reviewer, approval/rejection states, and re-verification dates. Mohamed cross-checks audit requirements. |
| Wednesday 20:30-21:30 | Abdikhalaq | `docs/product/screen-inventory.md`, `docs/product/user-flows.md` | Map each supplied UI screen to an MVP feature, data needed, and deferred controls. Salah cross-checks appointment flow. |
| Thursday 19:00-20:30 | Najib | `supabase/migrations/0001_initial_schema.sql`, `supabase/seed.sql` | Draft migration and fictional demo data only. Mohamed reviews roles, constraints, and data exposure. |
| Thursday 20:30-21:30 | Mohamed | `docs/qa/test-plan.md`, `docs/qa/acceptance-checklist.md` | Define test cases for login, authorization, booking, errors, and privacy. All owners validate their feature tests. |
| Friday 19:00-20:00 | All | `docs/decisions/weekly-signoff-week-1.md` | Record decisions, risks, open questions, and whether coding may begin. Everyone signs off. |
| Friday 20:00-21:00 | Project owner | No file changes unless approved | Review the week’s diffs and approve or reject the push request. |

### Week 2 - build the safe booking foundation

| Day and time | Owner | Files to create or update | Outcome and cross-check |
| --- | --- | --- | --- |
| Monday 19:00-21:30 | Najib | `supabase/migrations/0001_initial_schema.sql`, `supabase/migrations/0002_rls_policies.sql` | Create core tables and Row Level Security policies. Mohamed runs the authorization test checklist. |
| Tuesday 19:00-21:30 | Abdikhalaq | `mobile/lib/main.dart`, `mobile/lib/app.dart`, `mobile/lib/features/auth/` | Create the Flutter shell, routes, and login/signup screens. Najib verifies auth contract; Mohamed checks validation and error handling. |
| Wednesday 19:00-21:30 | Salah | `supabase/functions/provider-verification/`, `docs/provider-verification/workflow.md` | Create the review-state workflow only; provider visibility stays disabled until approval. Mohamed checks audit trail. |
| Thursday 19:00-21:30 | Abdikhalaq and Salah | `mobile/lib/features/services/`, `mobile/lib/features/appointments/`, `supabase/functions/appointments/` | Build service browsing and appointment request creation. Najib checks database integrity and conflict handling. |
| Friday 19:00-20:00 | Mohamed | `mobile/test/`, `docs/qa/week-2-results.md` | Run functional and authorization checks. Log failed tests as GitHub issues. |
| Friday 20:00-21:00 | All | `docs/decisions/weekly-signoff-week-2.md` | Demo the flow with fictional data; document approval, defects, and next-week priorities. |

## Daily work cycle

| Time | Activity |
| --- | --- |
| 18:50-19:00 | Confirm issue, branch, acceptance criteria, and files in scope. |
| 19:00-20:30 | Build the assigned change. Keep commits small and local. |
| 20:30-20:50 | Run tests, linting, and the relevant acceptance checklist. |
| 20:50-21:10 | Peer cross-check: inspect changed files, test the acceptance criteria, and record findings. |
| 21:10-21:20 | Post the completion update and request push approval. |

## Completion notification template

Post this update in the team channel and send it here when a work item is ready:

```text
WORK COMPLETE - awaiting cross-check
Issue: #<number> <title>
Owner: <name>
Branch: <branch>
Files changed: <list>
What works: <one or two sentences>
Checks run: <tests, lint, manual checks>
Known limits or risks: <list or none>
Cross-checker requested: <name>
Push status: not pushed
```

## Cross-check and approval gate

The cross-checker must verify the changed files against the issue’s acceptance criteria, inspect security and privacy impact, and test the feature using fictional data. They respond using:

```text
CROSS-CHECK RESULT
Issue: #<number>
Result: approved / changes requested
Evidence: <tests or observations>
Required changes: <list or none>
```

After a successful cross-check, request push approval from the project owner:

```text
PUSH APPROVAL REQUEST
Issue: #<number> <title>
Branch: <branch>
Commit(s): <short hashes>
Files: <list>
Cross-check: approved by <name>
Ready to push to: origin/<branch>
Please reply: APPROVE PUSH or HOLD.
```

Only the explicit response `APPROVE PUSH` authorizes a push. `HOLD` means keep the work local and state what is needed next.

## Definition of done

A task is done only when all of the following are true:

- The acceptance criteria are met.
- The owner has tested the change.
- A peer has cross-checked it.
- Documentation is updated when behaviour, data, or setup changes.
- No secrets or real health data appear in the branch.
- The project owner has explicitly approved the push.
- The approved commit is pushed and the team receives the final confirmation with a repository link.
