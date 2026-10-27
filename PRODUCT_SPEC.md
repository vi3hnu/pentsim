# PentSim — MVP Product Specification

## Product goal
Help freshers and job seekers practice the complete penetration-testing lifecycle in realistic scenarios, combining guided simulation with future isolated hands-on labs. Reward demonstrated process, safe scope handling, reproducible evidence and professional reporting—not just flags.

## MVP personas
- Learner: completes missions, captures evidence, creates findings and reports.
- Reviewer/instructor: reviews work and provides feedback (backend role planned; not implemented in static demo).
- Administrator: manages missions and approved lab templates (planned).
- Employer: views consent-based portfolios (planned).

## Core user journey
1. Browse mission catalog.
2. Review client brief and scope.
3. Save test plan.
4. Use fixed-command simulated workspace.
5. Record findings and evidence notes.
6. Generate a report preview and export JSON or print to PDF.
7. Review competency indicators and achievements.

## Modules
- Dashboard and XP progression
- Mission board with difficulty filters
- Engagement workspace with scope, test plan, safe terminal and objectives
- Findings and evidence vault
- Report studio
- Career skills and portfolio view

## Assessment model
Proposed rubric: scoping/authorization 15%; planning/reconnaissance 10%; validation 25%; evidence/reproducibility 15%; risk/remediation 10%; report quality 20%; client communication 5%. XP is a separate engagement reward and must not be treated as proof of competence. Critical scope/safety violations are mandatory review gates.

## Security architecture for production
- Keep public app/API, lab controller and lab execution plane separate.
- Provision only approved, versioned lab templates.
- Use per-session networks and deny external egress by default.
- Deny access to host services, cloud metadata, management interfaces, production data and other learners.
- Do not mount container-runtime sockets or production secrets into workloads.
- Enforce non-root execution, capability restrictions, resource quotas, expiry and cleanup.
- Audit provisioning, authorization, session access and policy violations.
- Verify tenant/ownership permissions on every protected operation.

## Data model (planned)
`users`, `learner_profiles`, `missions`, `mission_versions`, `mission_objectives`, `engagements`, `engagement_scope_versions`, `scope_assets`, `lab_sessions`, `submissions`, `findings`, `evidence`, `report_versions`, `assessment_results`, `competency_scores`, `xp_ledger`, `audit_events`.

## Proposed stack
- Frontend: Next.js, TypeScript, Tailwind CSS
- Backend: Python, FastAPI, Pydantic, SQLAlchemy, Alembic
- Database: PostgreSQL
- Background jobs: Redis + task queue
- Evidence storage: S3-compatible object storage
- Lab execution: dedicated worker nodes with isolated containers or VMs and a restricted session gateway
- Observability: structured logs, metrics, tracing and security audit events

## MVP acceptance criteria
1. Learners can navigate all core modules.
2. Mission scope and test plan can be reviewed and saved.
3. The simulated terminal only accepts a predefined command allowlist and makes no network calls.
4. Findings can be created, edited and deleted.
5. Report preview reflects saved findings.
6. JSON export and browser print-to-PDF work.
7. Demo progress persists locally in the browser.
8. The interface labels seeded data as fictional training data.

## Current limitations
The supplied build is a static browser prototype. It has no authentication, backend, database, real lab orchestration, shared multi-user state, AI integration, production authorization, or verified employability assessment. Do not expose real lab execution until the lab isolation design is implemented and independently tested.
