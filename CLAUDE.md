# CLAUDE.md — BeRocker help site

The page rules are in README.md. Every screen, tab, card, field and button name on these pages
is taken from the app (StepDeckCRM/berocker-front), never from memory.

## 🧠 Plan with the session's model, build with Opus agents (owner rule — mandatory)

The owner pays for every token. The most capable model (Fable) is for
thinking: understanding the request, planning, deciding, writing the
instructions and reviewing the result. The work itself is done by subagents,
and subagents run on Opus.

- When you start a subagent (the Agent tool, a workflow, a background or
  cloud session), set its model to `opus` explicitly, every time. Never start
  one on Fable. Never leave the model unset when the session itself runs on
  Fable: an unset model inherits the session's.
- Do not use the `fork` agent type from a Fable session: a fork always runs
  on the session's own model.
- Keep for yourself: the plan, the brief each agent gets, decisions that are
  yours or the owner's, the review of what agents hand back, and small edits
  that are quicker to make than to explain.
- Hand to Opus agents: sweeps and audits, multi-file implementation, writing
  documentation, research, long test-and-fix loops.
- A cheaper model than Opus is fine for a trivial lookup.
- If the owner says otherwise in a session, that wins.
