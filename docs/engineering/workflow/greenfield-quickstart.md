# Greenfield Quickstart

Use this guide when starting a new project from scratch with the AI Engineering Standard.
For existing projects, see `project-modes.md` (Legacy mode).

## Before You Start

The agent must not generate code until steps 1–3 are complete.
Skipping them produces a technically correct but contextually wrong result.

---

## Step 1 — Requirement Analysis

Answer these questions before any design decision:

- What business problem does this system solve?
- Who are the users and what are their primary workflows?
- What are the functional boundaries — what is explicitly out of scope?
- What are the non-functional requirements: latency, throughput, availability, security level?
- What integrations are required (identity provider, external APIs, messaging, storage)?
- What are the deployment and operational constraints (cloud, on-prem, team size, CI/CD)?
- What is the expected data volume and growth pattern?

Record answers in `PROJECT_CONTEXT.md` (copy from `project-context-template.md`).
Mark unknowns explicitly. Do not invent requirements.

---

## Step 2 — Architecture Decision

Using the answers from Step 1, select a proportionate architecture.

Default starting point: **modular monolith with a layered structure**.

Justify moving to a more complex style only when a specific requirement demands it:

| Trigger | Possible evolution |
|---|---|
| Independent deployment of a bounded context by a separate team | Extract to a service |
| Event-driven audit trail or temporal queries | Event sourcing for that context |
| Read/write performance asymmetry with separate scaling needs | CQRS for that context |
| Regulatory or data-residency isolation | Separate service or database |

Record the decision as `ADR-0001` using `docs/engineering/templates/adr-template.md`.

---

## Step 3 — Quality Gates First

Set up enforcement before writing feature code.
A project without quality gates accumulates debt from the first commit.

### Spring Boot minimum
- Formatter: `spring-javaformat` or `google-java-format`
- Linter / static analysis: `checkstyle`, `spotbugs`
- Architecture tests: `ArchUnit` — enforce layer dependency direction from day one
- Test runner: `JUnit 5` + `AssertJ`
- Build: `Maven` or `Gradle` with a `verify` goal that runs all checks
- CI: at minimum, build + test on every push

### React minimum
- Formatter: `prettier`
- Linter: `eslint` with `react`, `react-hooks`, `jsx-a11y` plugins
- Type checker: `TypeScript` strict mode
- Test runner: `vitest` or `jest` + `@testing-library/react`
- CI: lint + type check + test on every push

### Angular minimum
- Formatter: `prettier`
- Linter: `eslint` with `@angular-eslint`
- Type checker: TypeScript strict mode (already enforced by Angular CLI)
- Test runner: `jest` or `karma` + `@testing-library/angular`
- CI: lint + type check + test on every push

---

## Step 4 — Thin Vertical Slice

Build one complete user-facing flow end to end before adding breadth.

Example for a Spring Boot + React project:
1. One API endpoint (e.g. `GET /api/health` or the simplest domain read).
2. One service and one repository with a real database connection.
3. One integration test that hits the database.
4. One React page that calls the API and renders the result.
5. One component test.

This validates the full stack, build pipeline, and deployment before complexity grows.

---

## Step 5 — Fill PROJECT_CONTEXT.md

After the thin slice is working, complete `PROJECT_CONTEXT.md`:

- Confirm the architecture style and key boundaries.
- Record the exact quality commands the agent should run.
- Document naming, error handling, and API conventions.
- List any do-not-touch areas.

The agent reads this file at the start of every session. Keep it current.

---

## Common Mistakes to Avoid

| Mistake | Why it hurts |
|---|---|
| Designing for imagined scale | Adds complexity with no current benefit |
| Skipping quality gates "until later" | Later never comes; debt compounds |
| Starting with microservices | Distributed systems cost before you have a reason |
| Building generic frameworks before features | YAGNI; frameworks should emerge from patterns |
| Leaving PROJECT_CONTEXT.md empty | Agent loses context every session |
| Writing tests after the feature is done | Tests become a formality, not a design tool |
