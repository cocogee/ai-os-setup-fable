# Skill: Grill Me (interview skill)

## Purpose
Extract knowledge from the user's head into the second brain through a focused interview. The fastest way to populate `01_profile/` and `02_business/` — or to think through any topic deeply.

## When to use
- During initial setup (Stage 4), to fill the static context files
- Before a big decision, launch, or project
- Whenever Claude's answers sound like a stranger wrote them — that means context is missing

## Required inputs
- A topic ("my business," "my goals," "this new product idea")
- 15–30 minutes of the user's attention

## Instructions (the prompt)
Run this skill by following these steps exactly:

1. State the topic and ask the user to confirm or narrow it.
2. Ask ONE question at a time. Wait for the answer before the next.
3. Start broad, then drill into specifics, numbers, examples, and contradictions. Push back gently: "Earlier you said X, but this sounds like Y — which is it?"
4. Ask 15–30 questions, or stop when answers start repeating.
5. Save the full Q&A to `04_knowledge/notes/brainstorms/YYYY-MM-DD_<topic>.md`.
6. Propose specific updates to the relevant static files (`01_profile/`, `02_business/`) as a diff-style summary. Apply only after the user approves.
7. Update "Last updated" dates on every file changed.

## Output format
- Brainstorm doc: full Q&A plus a "Key extractions" section (5–10 bullets)
- Proposed file updates: file name → what changes → why

## Recommended model
Sonnet. (Fable optionally for the very first business-wide grill, where deeper inference about gaps pays off.)

## Safety notes
Read/write inside the OS folder only. Never sends or publishes anything. If the user shares sensitive data (financials, health), note it stays in local markdown and ask before recording it.

## Improving this skill
After each use, ask: "Which questions were most/least useful?" Fold the answer into the Instructions above and log the change in `00_system/CHANGELOG.md`.

## Log after use
- Session log entry (topic, # questions, files updated)
- Tracker: files changed

## Teaching Mode explanation
"I'm interviewing you to move knowledge from your head into files Claude can read later. Every answer becomes permanent context, so future sessions start out already knowing this instead of asking again."
