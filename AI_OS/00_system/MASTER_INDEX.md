# MASTER_INDEX.md — Map of this AI OS

Claude reads this at session start. Update it whenever something is hard to find or the structure changes.

## Layout

| Folder | What it is | Layer |
|---|---|---|
| `CLAUDE.md` | Root router — read first | System |
| `OS_SETUP_TRACKER.md` | Current stage, next action, logs | System |
| `00_system/` | Index, model routing, safety rules, changelog | System |
| `01_profile/` | Who the user is: profile, preferences, goals, decisions | Static context |
| `02_business/` | Overview, customers, offers, marketing, operations | Static context |
| `03_projects/` | active / paused / completed project folders | Working area |
| `04_knowledge/` | notes / transcripts / research / references | Static context |
| `05_connections/` | Registry + docs for live data sources. ⚠️ Safety rules apply | Live connections |
| `06_skills/` | One markdown file per reusable capability | Capability |
| `07_workflows/` | manual → ready_for_automation → automated | Capability → Cadence |
| `08_logs/` | session / decision / error / automation logs (append-only) | Logs |
| `09_outputs/` | drafts / reports / exports / deliverables | Outputs |
| `10_archive/` | old_versions / deprecated / raw_imports — nothing is deleted | Archive |

## Quick answers

- "What do you know about me?" → `01_profile/` + `02_business/`
- "What are we working on?" → `03_projects/active/`
- "Have we discussed this before?" → `04_knowledge/` + `08_logs/session_logs/`
- "Can you check my email/calendar/revenue?" → `05_connections/CONNECTIONS_INDEX.md` — if it's not registered there, the answer is "not connected yet."
- "Do that thing we always do" → `06_skills/`

## Hot files (most frequently needed)

1. `OS_SETUP_TRACKER.md`
2. `01_profile/USER_PROFILE.md`
3. `02_business/BUSINESS_OVERVIEW.md`
4. `00_system/SAFETY_RULES.md`

## Index maintenance

- If Claude searches noticeably long for something → add it here.
- If a folder's purpose changes → update its row AND its README.
- For pre-existing user folders that were indexed rather than moved, list them here with their real path:

### External / legacy locations

(None yet.)
