# Skill: Create Project Brief

## Purpose
Start every project with a one-page brief so any future session (or cheaper model) can pick up the project without re-explanation.

## When to use
Whenever work will take more than one session or produce a deliverable.

## Required inputs
- Project name and goal (one sentence is enough; the skill asks for the rest)

## Instructions (the prompt)
1. Check `03_projects/` — does this project already exist under another name? If yes, update it instead.
2. Create `03_projects/active/<project_name>/BRIEF.md` with:
   - **Goal** (one sentence) and **Done when** (testable criteria)
   - **Why now** (context)
   - **Relevant context files** (links into 01/02/04 — so workers don't re-read everything)
   - **Deliverables** (what lands in 09_outputs/)
   - **Model plan** (which tiers do which parts)
   - **Safety notes** (does anything touch the outside world? If yes → SAFETY_RULES gates)
   - **Status log** (dated one-liners, newest first)
3. Ask the user max 3 clarifying questions, only ones the brief truly needs.
4. Add the project to the tracker's "Files created."

## Output format
The BRIEF.md file plus a 2-line confirmation in chat.

## Recommended model
Sonnet.

## Safety notes
A brief never triggers external actions. If the project will need connections or automations, the brief flags it — the gates are passed later, explicitly.

## Improving this skill
If briefs keep missing a section people need, add it to the template above.

## Log after use
Tracker "Files created" + session log.

## Teaching Mode explanation
"I'm writing the project's one-page memory. Next week, a cheaper model can read this brief and continue the work without you re-explaining anything — that's how the OS saves you money."
