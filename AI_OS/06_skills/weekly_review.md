# Skill: Weekly Review

## Purpose
A scheduled look at the whole OS: what happened, what's stale, what should improve. This is the system's heartbeat.

## When to use
Once a week (pick a consistent day). Also after any chaotic stretch.

## Required inputs
None — everything comes from the OS itself.

## Instructions (the prompt)
1. Read: `OS_SETUP_TRACKER.md`, `03_projects/active/*/BRIEF.md` (status logs), `08_logs/session_logs/` (last 7 days), `08_logs/error_logs/` (any new).
   - On long log sets, delegate summarization to Haiku and use the returned summaries.
2. Produce a review covering:
   - **Wins** — what got done
   - **Stuck** — blockers and stale projects (no status update in 14+ days → propose pausing)
   - **System health** — anything hard to find? Any file 60+ days stale? Any error repeated?
   - **Skill candidates** — tasks done 2+ times this week by hand
   - **Archive candidates** — list, never auto-archive
   - **Next week's top 3**
3. Save to `09_outputs/reports/YYYY-MM-DD_weekly_review.md`.
4. Update the tracker snapshot (stage, next action, blockers).
5. Walk the user through it in ~10 lines, decisions clearly marked.

## Output format
The report file + a short chat summary ending with explicit yes/no decisions for the user.

## Recommended model
Sonnet (Haiku for log summarization). Quarterly: run a deeper version with Fable as a full system audit.

## Safety notes
Read-only except the report and tracker. Archive/pause actions require user approval in the moment.

## Improving this skill
If a section is never useful, cut it. If the user keeps asking something the review misses, add a section.

## Log after use
The report IS the log. Add a changelog line if system changes were approved.

## Teaching Mode explanation
"This is the maintenance loop. A second brain rots quietly — stale facts, dead projects, unused files. A weekly review catches the rot early and turns repeated work into skills."
