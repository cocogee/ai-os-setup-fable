# OS_SETUP_TRACKER.md

Claude: read this file at the start of every session. It tells you where the user is, what's done, what's next, and what not to touch.

---

## Status snapshot

- **Current stage:** Stage 0 — Audit
- **Current model in use:** —
- **Recommended model for next action:** Fable
- **Next action:** Run the bootstrap audit prompt (see AI_OS_SETUP_GUIDE.md §7)
- **Blockers:** None
- **Last updated:** — (date + who/what updated it)

## Teaching Mode

Status: **On** by default

Instructions:
- Explain major steps in plain language.
- Keep explanations short.
- Explain what changed after important file edits.
- Ask the user if they want more detail before going deeper.

## Setup stages

- [ ] **Stage 0 — Audit the current system** (Fable)
- [ ] **Stage 1 — Decide the default workflow** (Fable)
- [ ] **Stage 2 — Create or clean up the root AI OS folder** (Sonnet)
- [ ] **Stage 3 — Create or revise the folder structure** (Fable plans, Sonnet executes)
- [ ] **Stage 4 — Build or consolidate the static second brain** (Sonnet, Haiku for extraction)
- [ ] **Stage 5 — Create or revise the root CLAUDE.md router** (Fable)
- [ ] **Stage 6 — Add the process tracker** (Sonnet)
- [ ] **Stage 7 — Add model-routing rules** (Fable)
- [ ] **Stage 8 — Add verification and safety rules** (Fable)
- [ ] **Stage 9 — Create first skills** (Sonnet)
- [ ] **Stage 10 — Add live connections, carefully, one at a time** (Fable for safety design, Sonnet for implementation) ⚠️ requires explicit user approval per connection
- [ ] **Stage 11 — Convert battle-tested workflows into cadence/automation** (Fable for safety review, Sonnet for build) ⚠️ requires explicit user approval per automation
- [ ] **Stage 12 — Review, prune, improve (ongoing)** (Sonnet weekly, Fable quarterly)

## Do not touch yet

(Things the audit flagged as needing user approval before any change.)

-

## Decisions made

| Date | Decision | Why |
|---|---|---|
| | | |

## Files created

-

## Files changed

-

## Files archived

-

## Skills created

- [ ] grill_me
- [ ] update_context
- [ ] create_project_brief
- [ ] weekly_review
- [ ] verify_output

## Connections added

(None until Stage 10. Each needs a row in 05_connections/CONNECTIONS_INDEX.md and user approval.)

-

## Automations created

(None until Stage 11. Each needs: owner, logs, rollback plan, review cadence.)

-

## Model usage notes

(Notable choices: where Fable was spent, what was delegated to Sonnet/Haiku, anything that cost more than expected.)

-

## Safety / permission notes

(Any key created, scope granted, risk flagged, or approval given.)

-

## Open questions

-

---

**How to update this file:** Claude updates the snapshot, checkboxes, and logs whenever something meaningful changes, and refreshes "Last updated." The user can edit anything at any time — this file is the shared source of truth.
