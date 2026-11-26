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

## 💸 GitHub Actions cost real money: ship in batches (owner rule — mandatory)

The owner was billed $195 for GitHub Actions in one month. In berocker-api and
berocker-front, EVERY push to ANY branch runs the full CI (about 11 billed
minutes in berocker-api, about 7 in berocker-front), and every merge to main
runs it again before the deploy. berocker-ai-service-be and the docs repo have
no CI today; keep it that way unless the owner asks.

- **Batch.** Collect related fixes and ship them together in one pull request,
  a few releases a day at most. A hotfix ships on its own only when live users
  are being hurt right now (a broken screen, wrong money or data, failed
  payments, lost or wrong messages to customers). Everything else waits for
  the next batch.
- **Push only when it is ready to merge.** Commit locally as you go. Push a
  branch once, when it is ready to become a pull request; push again only to
  fix what that pull request needs. Never push to save work or to "see what CI
  says". If a stop hook asks you to push unpushed commits, push only a branch
  that is ready for its pull request; otherwise say in one line why it stays
  local.
- **Never push a branch that is the same as main.** After a merge, reset the
  working branch to main locally only (`git checkout -B <branch> origin/main`)
  and do not push it; the next real change is the next push.
- **No CI for changes CI cannot check.** A commit that only touches docs,
  CLAUDE.md, README files or `resources/whats-new/whats-new.json` gets
  `[skip ci]` in its commit message, and its merge commit message too.
- **Check locally first.** Run the tests, lint and type-check on your machine
  or container before pushing; CI confirms, it does not discover.
- **Never** re-run a workflow just to see it pass, push an empty commit to
  start CI, or close and reopen a pull request to restart it.
- **Ask first** before adding a workflow, a job, a matrix entry, a scheduled
  run, or anything that makes CI run more often or longer (the Golden Rule
  applies to CI minutes too).
