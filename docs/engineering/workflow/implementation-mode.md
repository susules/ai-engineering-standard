# Implementation Mode

## Purpose

Deliver production-quality changes while preserving the architecture and conventions of the
target repository.

## Workflow

1. **Inspect**: examine repository structure, stack, build scripts, conventions, related code,
   tests, configuration, and relevant documentation.
2. **Understand**: identify expected behavior, acceptance criteria, affected boundaries, and
   compatibility constraints.
3. **Plan**: for non-trivial work, summarize the approach, affected areas, tests, and approval
   gates. Do not over-plan a trivial change.
4. **Gate**: obtain approval for any action requiring it under `approval-policy.md`.
5. **Implement**: make small, focused changes. Avoid unrelated cleanup and broad rewrites.
6. **Test**: add or update tests that verify behavior and relevant failure cases.
7. **Verify**: run the actual project checks available in the environment.
8. **Review**: inspect the diff for correctness, accidental scope expansion, security issues,
   maintainability, and missing tests.
9. **Report**: state what changed, what ran, actual outcomes, and remaining risks.

## Existing / Legacy Projects

- Preserve existing conventions unless a reasoned change is approved.
- Add characterization tests when behavior is uncertain and risky.
- Avoid replacing architecture wholesale as a side effect of a feature.
- Maintain compatibility or provide an approved migration plan.
- Separate essential work from optional technical-debt remediation.

## Greenfield Projects

- Confirm core requirements and constraints first.
- Establish a proportionate structure and minimum useful quality gates.
- Avoid speculative abstractions and infrastructure.
- Document significant decisions and setup instructions.

## Implementation Rules

- Never fabricate files, APIs, commands, dependencies, test results, or tool capabilities.
- Do not silently modify generated files or lockfiles without understanding why.
- Do not expose secrets in code, logs, examples, or reports.
- Do not perform destructive operations without explicit approval.
- If blocked, explain the blocker and offer the safest next step.
