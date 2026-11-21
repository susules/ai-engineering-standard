# Approval Policy

## 1. Default Autonomy

After the user agrees to a scope and plan, the agent may autonomously perform routine,
in-scope, reversible engineering work, including:
- Repository inspection and technical research.
- Editing or adding source and test files.
- Local refactoring within the approved scope.
- Running non-destructive build, lint, type-check, and test commands.
- Updating directly relevant documentation.
- Preparing (but not executing) gated changes for review.

Tool-level permissions and safety prompts always take precedence.

## 2. Explicit Approval Required

Obtain explicit approval before:
- Material changes to architecture, module boundaries, or dependency direction.
- Breaking public APIs, event schemas, data contracts, or compatibility guarantees.
- High-risk schema/data migrations, destructive data operations, or irreversible changes.
- Adding a significant runtime, infrastructure, platform, or third-party dependency.
- Production deployment, production configuration changes, or production data operations.
- Deleting or overwriting user data or performing broad destructive file operations.
- Expanding beyond the agreed scope in a way that materially changes cost, risk, or behavior.

## 3. Approval Request Format

Explain:
- The decision/action requiring approval.
- Why it is needed.
- Options and recommendation.
- Impact, risk, reversibility, and affected areas.
- What work can safely continue without approval.

Ask a direct question and wait for the user's decision before executing the gated action.

## 4. Scope Changes

Approval applies only to the described scope. If new evidence reveals a material change,
pause the affected action, explain the new information, and request approval where needed.
Continue independent safe work where possible.

## 5. What Does Not Need Separate Approval

Unless the user or repository policy says otherwise, no separate approval is needed for
routine in-scope code changes, test additions, local analysis, non-destructive checks, or
focused refactoring that does not cross a gated boundary.

## 6. No Implied Authorization

Silence, previous approvals, or approval of a design proposal do not authorize unrelated
destructive actions, production operations, or materially different architecture changes.
Never bypass tool permissions or safeguards.
