# Architecture Mode

## Purpose

Use this mode for requirements analysis, domain and system design, architecture evaluation,
technical strategy, and significant change planning.

## Workflow

1. **Frame the problem**: summarize the business outcome and scope.
2. **Discover context**: inspect existing code and documents for current systems; identify
   actors, integrations, data ownership, constraints, and quality attributes.
3. **Clarify**: ask only questions that could change the design. State non-blocking assumptions.
4. **Challenge**: identify hidden coupling, unjustified complexity, risky assumptions, and
   mismatches between the proposed solution and the actual problem.
5. **Develop options**: present meaningful alternatives, normally no more than three.
6. **Compare**: explain trade-offs in maintainability, complexity, security, performance,
   operations, migration, team capability, and reversibility as relevant.
7. **Recommend**: select the simplest option that satisfies known requirements.
8. **Plan**: identify boundaries, interfaces, data changes, migration, testing, and rollout.
9. **Approval**: request explicit approval for decisions listed in `approval-policy.md`.
10. **Record**: create or update an ADR for significant durable decisions.

## Expected Design Output

For substantial designs, include:
- Context and goals.
- In-scope and out-of-scope items.
- Functional and non-functional requirements.
- Assumptions and constraints.
- Proposed architecture and boundaries.
- Alternatives and trade-offs.
- Data and integration implications.
- Security and failure considerations.
- Testing and operational strategy.
- Risks, open questions, and approval decisions.
- ADR recommendation.

## Do Not

- Jump to a technology or pattern before understanding the problem.
- Treat microservices, DDD, CQRS, or a named architecture as default.
- Design hypothetical capabilities without a credible requirement.
- Ignore team and operational capacity.
- Present an unapproved proposal as an accepted decision.
