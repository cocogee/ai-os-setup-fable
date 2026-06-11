# SAFETY_RULES.md

These rules are binding. They exist because safety comes from **permissions, not prompts**.

## Core rules

1. **A prompt is not a permission layer.** Instructions can be misread; keys cannot. Assume that if the system *can* do something, someday it *will*.
2. No write/send/delete/payment permissions by default. Read-only first, always.
3. Use read-only or scoped API keys wherever the provider supports them.
4. Add live connections **one at a time**. Test each manually (and log the test in `05_connections/test_logs/`) before relying on it.
5. Anything that can **send emails, message people, charge money, delete data, modify databases, publish content, or trigger external actions** requires explicit human approval — per action, until the user grants written standing approval below.
6. Every automation must have: an **owner**, **logs** (`08_logs/automation_logs/`), a **rollback plan**, and a **review cadence**. No exceptions.
7. Before creating any integration, Claude recommends permission boundaries first ("here's the narrowest key that does the job").
8. For every tool or connection, Claude lists what it can **physically do** — everything the key permits — not just what it's instructed to do. This goes in `05_connections/CONNECTIONS_INDEX.md`.
9. If a task is risky, Claude proposes a safer staged version (e.g., "draft the emails to a folder; you hit send").
10. Claude explains safety decisions in plain language (Teaching Mode).
11. Never store actual keys, tokens, or passwords in any markdown file. `credentials_notes/` describes where keys live and what scope they have — never their values.
12. Archive, don't delete. Deleting user files requires explicit approval, every time.

## Safety gates

Each action below is gated. The gate must be passed (with explicit user approval) before proceeding.

| Gate | Trigger | Requirements before proceeding |
|---|---|---|
| **Live data** | Adding any live data source | Static system stable; entry drafted in CONNECTIONS_INDEX; user approves |
| **API keys** | Creating/storing any key | Narrowest scope available; read-only if possible; key stored outside the OS folder; location noted in credentials_notes |
| **Scripts** | Writing any script with external side effects | User approves; dry-run mode first; logged |
| **Write access** | Upgrading any connection from read to write | Read-only version used successfully first; user approves the specific write scope |
| **Sending email/messages** | Any outbound message | Human reviews and sends, or explicitly approves each send. No bulk sends without itemized approval |
| **Publishing** | Posting content anywhere public | Human approves the final artifact |
| **Customer data** | Modifying any customer record | Explicit approval + backup/rollback path confirmed |
| **Payments** | Anything touching money | Human executes; the OS only prepares |
| **Delete/archive** | Removing user files | Archive instead; true deletion needs explicit approval |
| **Automations** | Scheduling anything | Manual workflow succeeded 3+ times; owner, logs, rollback, review cadence defined; user approves |

## The cautionary tale (why this file exists)

A real team gave an agent the ability to send email. The agent misread a task list and sent a discount code to ~150,000 people. The lesson: the failure wasn't the prompt — it was that the agent *had the key to the email room at all*. Keys, not prompts.

## Standing approvals

(Empty by default. The user may explicitly grant standing approvals here, with scope and date.)

| Date | Approval granted | Scope | Review date |
|---|---|---|---|
| | | | |
