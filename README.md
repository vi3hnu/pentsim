# PentSim MVP — Local Demo

A responsive, interactive frontend prototype for PentSim, a gamified penetration-testing experience platform. This is a static application and does not require Node.js or a build step.

## Run it

1. Extract the ZIP.
2. Open `index.html` in a modern browser.
3. Use the sidebar to explore Dashboard, Mission Board, Active Engagement, Findings & Evidence, Report Studio, and Skills & Portfolio.

Optional local server:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080` from the directory containing `index.html`.

## Included interactions

- Navigation between all main product areas.
- Mission filtering and mission selection.
- Scope review and test-plan completion actions.
- Safe simulated terminal with a fixed command allowlist (`help`, `map`, `routes`, `headers`, `check`, `status`, `clear`). No shell execution or network requests occur.
- Create, edit and delete fictional training findings.
- XP and competency score updates for selected actions.
- Report preview populated from the findings vault.
- JSON report export and browser print-to-PDF.
- Browser-local persistence using `localStorage`.

## Important limitations

This is a frontend MVP prototype, not a production platform. It has no authentication, shared database, real lab orchestrator, backend API, multi-tenant isolation, real AI service or independently verified assessment engine. Sample metrics and seeded findings are illustrative. The report is explicitly labeled as fictional training data.

Do not connect this prototype to production targets or treat its scores as proof of employability. Before introducing real hands-on labs, implement a separate lab control plane, per-session network isolation, strict egress controls, workload limits, audit logging, expiry and cleanup, and independent security testing.

## Proposed next production steps

1. Convert the interface to Next.js + TypeScript.
2. Implement FastAPI endpoints and PostgreSQL schema from the PentSim product specification.
3. Add authentication and ownership/tenant authorization checks.
4. Build a versioned scenario engine and deterministic objective validators.
5. Add a separately hosted lab controller and restricted session gateway.
6. Add server-side report generation, evidence storage and auditable competency assessment.
