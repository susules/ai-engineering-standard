# Architecture Governance

## 1. Objective

Select and evolve architecture based on business needs, quality attributes, constraints, and
operational reality. Architecture is a means to manage change and risk, not an end in itself.

## 2. Required Context

Before proposing a consequential design, understand as much as is relevant about:
- Business capabilities, domain complexity, and important workflows.
- System context, actors, integrations, and ownership boundaries.
- Data ownership, consistency, lifecycle, and migration needs.
- Quality attributes: security, availability, latency, throughput, scalability, and changeability.
- Deployment topology, runtime environment, observability, and operational capability.
- Team size, skills, ownership, and delivery constraints.
- Existing architecture, legacy constraints, and compatibility requirements.

Mark unknowns explicitly. Do not invent requirements.

## 3. Architecture Decision Method

For a material decision:

1. Frame the problem and desired outcome.
2. State known facts, assumptions, constraints, and unknowns.
3. Identify the quality attributes that drive the decision.
4. Establish the simplest viable baseline.
5. Identify two or three genuinely viable options when alternatives matter.
6. Compare benefits, costs, risks, failure modes, and reversibility.
7. Recommend one option and explain why.
8. Identify migration, rollout, and verification needs.
9. Obtain approval where the approval policy requires it.
10. Record significant decisions in an ADR.

Do not manufacture alternatives when there is only one sensible option. Explain why.

## 4. Proportionality and Common Patterns

The following are options, not mandatory defaults:
- Layered architecture.
- Modular monolith.
- Clean Architecture.
- Hexagonal / Ports and Adapters.
- Domain-Driven Design.
- CQRS and event-driven architecture.
- Microservices and distributed systems patterns.

Evaluate each only when relevant. For example, microservices require a reason to accept distributed
deployment, network failure, data ownership, observability, and operational complexity. A desire
for "independent modules" does not by itself prove a need for microservices; modular boundaries
inside a monolith may be sufficient.

## 5. Boundaries and Dependency Direction

For each meaningful module or service, clarify:
- Responsibility and ownership.
- Public interfaces and contracts.
- Allowed dependencies.
- Data ownership and access rules.
- Transaction and consistency boundaries.
- Error and failure semantics.

Prefer acyclic dependency graphs. Avoid shared database access that bypasses ownership
boundaries unless explicitly designed and governed.

## 6. Greenfield Governance

For a new system:
- Start from business capabilities and quality requirements.
- Choose a proportionate architecture.
- Define only boundaries that have a current reason.
- Establish conventions and verification early.
- Avoid speculative platform engineering and premature distribution.

## 7. Legacy Governance

For an existing system:
- Map the current architecture before changing it.
- Identify critical flows, implicit contracts, and hidden coupling.
- Use characterization tests where behavior is uncertain.
- Prefer incremental extraction or restructuring over a big-bang rewrite.
- Plan data and contract migrations, compatibility, rollout, and rollback.
- Distinguish architectural target state from safe intermediate states.

## 8. Architecture Fitness and Enforcement

Use deterministic checks where possible:
- Module dependency tests.
- Architecture tests (for example, ArchUnit where suitable).
- API/schema compatibility checks.
- Static analysis and dependency vulnerability scanning.
- Build and test pipelines.

A documented rule that is not checked automatically remains a human/agent review responsibility.
Do not claim an architectural rule is enforced unless a real check exists and is executed.

## 9. Architecture Review Output

For significant work, report:
- Context and problem.
- Existing and proposed boundaries.
- Options and trade-offs.
- Recommendation and rationale.
- Risks and mitigations.
- Migration and operational implications.
- Approval needed.
- ADR required: yes/no, with reason.
