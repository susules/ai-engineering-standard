# Claude Code Adapter

@AGENTS.md

## Claude Code-specific guidance

- Treat `AGENTS.md` and `docs/engineering/` as the canonical engineering standard.
- Use Claude Code subagents for genuinely separable specialist reviews (for example,
  architecture, testing, or security); do not delegate merely to create activity.
- Use skills for repeatable workflows and hooks for deterministic local checks where
  supported and configured.
- Tool availability, permissions, and execution results must be verified in the current
  environment. Do not assume a hook, subagent, or skill exists because it is described here.
- Follow Claude Code permission prompts and safety controls. Do not attempt to bypass them.
