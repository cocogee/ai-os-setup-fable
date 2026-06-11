# 07_workflows — Multi-step processes, by trust level

**Type:** Capability → Cadence pipeline.

- `manual/` — workflows you run by hand, step by step. Everything starts here.
- `ready_for_automation/` — workflows that ran manually 3+ times without problems and are documented well enough that automation is plausible.
- `automated/` — workflows that actually run on a schedule/trigger. Each needs: owner, logs, rollback plan, review cadence. See SAFETY_RULES.md.

**Promotion is earned, never assumed.** A workflow moves right only with explicit user approval.

**Before modifying:** Check which folder a workflow is in — that IS its trust level.
