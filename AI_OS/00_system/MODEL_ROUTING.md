# MODEL_ROUTING.md

**Principle: use the strongest model to design the system, then use cheaper models to run the system.**

Fable tokens are expensive. Spend them on decisions that affect the future shape of the OS — not on routine output.

## The four tiers

### Fable — the architect
Use for:
- Initial and periodic system audits
- Architecture and folder-structure design
- Writing/revising root CLAUDE.md, SAFETY_RULES.md, this file
- Major refactors of the OS
- Safety and permission design
- Complex stage detection (messy existing systems)
- High-stakes verification (anything external, financial, or structural)

### Opus — the second opinion
Use for:
- Optional critique of architecture Fable designed
- Deep reasoning when Fable is unavailable or budget is spent
- Refining complex systems

### Sonnet — the builder (default)
Use for:
- Day-to-day implementation: creating/editing files, writing, coding
- Project work and briefs
- Creating and refining skills
- Running established workflows
- Working through the setup checklist once the design exists

### Haiku — the worker
Use for:
- Extraction (pulling facts from transcripts/documents)
- Summarization, tagging, classification
- Formatting, batch cleanup, deduplication
- Any low-risk, high-volume task

## When NOT to use Fable

- Routine writing, repetitive formatting, simple summaries
- File cleanup or renaming
- Daily execution once architecture is stable
- Anything Sonnet can do at acceptable quality

## Switching rules

- **Fable → Sonnet:** the moment design is decided and the remaining work is execution. Fable writes the plan; Sonnet does the typing.
- **Sonnet → Haiku:** when a subtask is mechanical (summarize these 10 files, tag these notes). Delegate in batches.
- **Sonnet → Fable:** only when a decision will be hard to reverse (restructuring folders, safety rules, new connection design).

## Delegation rules

When delegating to a worker model:
1. Give it one narrow job and the exact files/inputs.
2. Require a concise structured return: a summary, extracted facts, or a table — not raw dumps.
3. The main session integrates the result; the worker never modifies system files (CLAUDE.md, tracker, safety rules).

## Logging

Note in `OS_SETUP_TRACKER.md → Model usage notes` whenever:
- Fable is used (and on what)
- A delegation pattern works well (reuse it)
- Something cost more than expected

## Explaining choices (Teaching Mode)

One plain sentence, e.g.:
- "This decision shapes the whole system, so I recommend Fable here."
- "This is routine writing — Sonnet handles it fine at a fraction of the cost."
- "This is mechanical extraction, so I'll hand it to Haiku and bring back a summary."
