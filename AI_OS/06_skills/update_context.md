# Skill: Update Memory / Context

## Purpose
Route new information to the right static file so the second brain stays current, without duplicating or overwriting existing knowledge.

## When to use
- After a conversation that surfaced new facts, decisions, or preferences
- After importing a transcript, document, or research
- When the user says "remember this"

## Required inputs
- The new information (text, file, or "what we just discussed")

## Instructions (the prompt)
1. Identify the discrete facts/updates in the new information.
2. For each one, find where it belongs: profile? business? a project? knowledge? a decision log?
3. **Check whether an equivalent statement already exists.** If yes: update it in place and note the date. If it conflicts: flag the conflict to the user instead of silently choosing.
4. If a large rewrite is needed, copy the old version to `10_archive/old_versions/` first.
5. Apply the updates. Refresh "Last updated" dates.
6. Report back: a short list of file → change.
7. Add one line to `00_system/CHANGELOG.md`.

## Output format
Table or short list: fact → destination file → action taken (added / updated / conflict flagged).

## Recommended model
Sonnet. Haiku for the extraction step on long inputs (delegate, get facts back, then route with Sonnet).

## Safety notes
Never deletes. Conflicts get flagged, not auto-resolved. Secrets never get written into markdown.

## Improving this skill
When a fact gets routed to the wrong file, add a routing rule here (e.g., "pricing changes → OFFERS.md, not BUSINESS_OVERVIEW.md").

## Log after use
Changelog line + tracker "Files changed."

## Teaching Mode explanation
"I'm filing new information where future sessions will look for it. The key habit: check what already exists before writing, so the brain doesn't accumulate contradictions."
