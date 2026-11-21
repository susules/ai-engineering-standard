# Engineering Principles

## 1. Purpose

These principles define the shared engineering philosophy across technology stacks. They are
decision aids, not a checklist to apply mechanically. The agent must explain applicability
and justify exceptions for consequential deviations.

## 2. Correctness Before Cleverness

Prefer behavior that is correct, explicit, understandable, and easy to verify. Avoid clever
constructs that reduce local clarity or make failure modes difficult to reason about.

## 3. Simplicity and Proportionality

Choose the simplest design that satisfies current, evidenced requirements and foreseeable
constraints. Simplicity does not mean ignoring real complexity; it means not inventing
complexity prematurely.

Before introducing a layer, abstraction, framework, service, queue, cache, or pattern, ask:
- What concrete problem does it solve?
- Is that problem present now or supported by credible requirements?
- What new concepts, failure modes, and operational costs does it introduce?
- Can a smaller solution meet the need?

## 4. Cohesion, Coupling, and Boundaries

- Keep related behavior and data close together.
- Minimize knowledge required across module boundaries.
- Make dependencies explicit.
- Direct dependencies toward stable policies and abstractions where appropriate.
- Avoid cyclic dependencies and uncontrolled shared mutable state.
- Define ownership of data and behavior clearly.

Do not create interfaces or modules solely to satisfy a slogan. An abstraction should protect
a meaningful boundary, enable a real substitution, or improve testability without obscuring
the design.

## 5. SOLID and Design Principles

Apply SOLID as diagnostic guidance:
- SRP: change responsibilities should be cohesive, not reduced to arbitrary one-method classes.
- OCP: extend behavior through stable seams when extension is a real requirement.
- LSP: substitutable implementations must preserve behavioral contracts.
- ISP: consumers should not depend on irrelevant operations.
- DIP: high-level policy should not be tightly coupled to volatile implementation details.

Also consider DRY, KISS, YAGNI, separation of concerns, composition, and least knowledge.
Avoid over-generalizing DRY: duplicated code can be preferable to a premature shared abstraction
when the concepts are not truly the same or likely to evolve together.

## 6. Changeability and Legacy Evolution

For existing systems:
- Understand current behavior before changing it.
- Identify compatibility and migration constraints.
- Prefer small changes with clear rollback or recovery paths.
- Add characterization tests when behavior is poorly documented and risky to change.
- Separate required changes from optional cleanup.
- Avoid broad rewrites without a compelling, evidence-based case and an approved migration plan.

For greenfield systems, do not over-engineer for hypothetical future requirements. Make
important boundaries clear while preserving room to evolve.

## 7. Testability and Feedback

Design components so important behavior can be verified at appropriate boundaries. Prefer
fast, deterministic feedback. Test observable behavior and meaningful failure cases rather
than implementation details. See `quality-governance.md` for test selection.

## 8. Security, Privacy, and Data Integrity

Treat security and privacy as design constraints from the beginning:
- Validate untrusted input at trust boundaries.
- Enforce authorization at the server or trusted enforcement point.
- Apply least privilege.
- Protect credentials and sensitive data.
- Use safe defaults and secure failure behavior.
- Consider data integrity, auditability, retention, and recovery.
- Do not log secrets or unnecessary personal data.

A material security, privacy, or data-integrity concern is a hard boundary, not a stylistic
preference.

## 9. Performance and Scalability

Do not optimize based on intuition alone. Identify measurable expectations, likely
bottlenecks, and relevant workload characteristics. Prefer simple designs until evidence or
requirements justify more advanced techniques. Consider resource use, latency, throughput,
concurrency, and tail behavior where relevant.

## 10. Reliability and Operability

Consider timeouts, retries, idempotency, backpressure, graceful degradation, failure
isolation, health signals, logs, metrics, traces, and recovery only where appropriate to the
system's actual operating model. Retries must account for duplicate side effects and bounded
attempts.

## 11. Accessibility and User Experience

For user-facing systems, consider accessibility, predictable interaction, error clarity,
responsive behavior, and user-perceived performance. Treat accessibility as a quality
requirement appropriate to the product and applicable obligations.

## 12. Documentation

Document why consequential decisions were made, important boundaries, contracts, setup,
operations, and non-obvious behavior. Avoid comments that merely restate readable code.
Keep docs consistent with the implementation.

## 13. Pragmatic Application

For each relevant principle, classify it as:
- Required: a hard boundary or explicit project requirement.
- Applicable: useful and proportionate for this change.
- Not applicable: no meaningful relevance to the current scope.
- Deferred: relevant, but intentionally postponed with rationale and risk noted.

Do not present a deferred or unverified concern as completed.
