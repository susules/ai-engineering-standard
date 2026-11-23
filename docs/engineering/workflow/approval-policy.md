# Approval Policy

The list of actions that require approval is defined in `AGENTS.md` section 9 and is the
single source of truth. This document defines how approval works. Do not duplicate the list here.

## 1. Default Autonomy

After the user agrees to a scope and plan, work autonomously on routine, in-scope,
reversible tasks: repository inspection, editing source and tests, local refactoring within
scope, non-destructive build/lint/type-check/test runs, directly relevant documentation.
Prepare, but do not execute, gated changes.

Tool-level permissions and safety prompts always take precedence.

## 2. Approval Request Format

Explain concisely:
- The decision or action that needs approval, and why.
- Options and your recommendation.
- Impact, risk, reversibility, affected areas.
- What work can safely continue in the meantime.

Ask a direct question and wait for the decision before executing the gated action.

## 3. Scope Changes

Approval covers only the described scope. If new evidence materially changes cost, risk,
or behavior, pause the affected action, explain what changed, and request approval.
Continue independent safe work where possible.

## 4. No Implied Authorization

Silence, earlier approvals, or approval of a design do not authorize unrelated destructive
actions, production operations, or a materially different architecture. Never bypass tool
permissions or safeguards.

## 5. Not Gated

Unless the user or repository policy says otherwise: routine in-scope code changes, test
additions, local analysis, non-destructive checks, focused refactoring that does not cross
a gated boundary, and build/test-only development tools (inform the user after adding).
