# Project Modes

The agent behaves differently depending on the lifecycle of the project. Determine the mode
at session start from `PROJECT_CONTEXT.md`. If it is missing or unclear, ask once, then
propose creating `PROJECT_CONTEXT.md` from `templates/project-context-template.md`.

A repository can contain areas in different modes (for example a legacy core with a
greenfield new module). Record that per area in `PROJECT_CONTEXT.md`.

## 1. Greenfield

Goal: a proportionate, evolvable foundation, not a showcase.

First steps, in order:
1. Requirement analysis (see `AGENTS.md` section 5). Resolve blocking unknowns.
2. Choose architecture using `architecture-governance.md`. Start with the simplest option
   that satisfies known requirements (often a modular monolith). Name the trigger that would
   justify evolving it.
3. Record the choice as ADR-0001 and fill `PROJECT_CONTEXT.md`.
4. Set up enforcement before features: formatter and linter, type check, architecture
   tests (dependency direction), test runner, coverage reporting, CI pipeline.
5. Build a thin vertical slice end to end, then widen.

Avoid: microservices, event-driven infrastructure, CQRS, or generic frameworks without a
demonstrated need. Do not build for imagined scale.

## 2. Legacy (existing codebase)

Goal: change safely without destroying what works.

First steps, in order:
1. Map the system: modules, layers, entry points, data stores, integrations, build and
   deployment, test situation. Report findings before proposing changes.
2. Identify the de facto conventions. These win over this standard.
3. Create a Deviation Register in `PROJECT_CONTEXT.md`: where reality differs from this
   standard, with severity and suggested direction. Do not fix deviations opportunistically.
4. For each change, work inside the existing structure. Improve what you touch only when
   it is within agreed scope (boy scout rule, small and reversible).
5. Add tests around the area before changing behavior-bearing code.

Avoid: "cleanup" refactors across the codebase, introducing a new architecture style
beside the old one without an ADR, style-only churn in unrelated files.

## 3. Migration (modernization or replacement)

Goal: reach a target state through small, verifiable, reversible steps while the system
keeps working.

Before moving anything:
1. Define the target state and the reason (what problem does the migration solve?).
2. Define the intermediate states. Each must be deployable and safe to stop at.
3. Choose an incremental strategy and justify it. Common options: strangler fig,
   branch by abstraction, parallel run, expand/contract for schemas and APIs.
4. Lock current behavior with characterization tests (tests that describe what the system
   does now, not what it should do). Record known bugs as known behavior, then decide
   explicitly whether to preserve or fix each.
5. Define rollback for every step and a measurable done condition.

Approval required: the migration plan itself, any data migration with irreversible effects,
and any contract-breaking cutover. See `workflow/approval-policy.md`.

Avoid: big-bang rewrites, moving code without characterization tests, mixing behavior
changes with structural moves in the same step.

## 4. Mode Summary

| Aspect | Greenfield | Legacy | Migration |
|---|---|---|---|
| First action | Requirements, ADR-0001 | Map system, report | Target + intermediate states |
| Convention source | This standard | Existing code | Target state, with ADR |
| Test approach | Test first, enforcement early | Tests around touched area | Characterization tests first |
| Biggest risk | Over-engineering | Breaking working behavior | Big-bang, lost behavior |
| Deviations | Fix immediately | Register, fix gradually | Track per step |
