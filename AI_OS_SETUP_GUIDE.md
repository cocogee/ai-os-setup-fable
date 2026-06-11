# The AI OS Setup Guide

*A square-one implementation manual for building a second brain + AI operating system out of folders, markdown files, skills, and routing logic — using Claude Code (or any harness), with the expensive model designing the system and cheap models running it.*

This guide ships with a working starter kit: the `AI_OS/` folder next to this file contains every template described here, ready to use. You can copy that folder anywhere and start — or, if you already have a partial system, **start with the audit (§3) instead and let the audit decide what to keep.**

---

## 1. Overview — what you're building and how

You are building two layers:

1. **A second brain** — folders and markdown files that hold your knowledge: who you are, your business, your projects, your notes. This is the knowledge layer.
2. **An AI operating system** — the rules, skills, and (eventually) connections and automations that let an AI *act* on that knowledge. This is the action layer.

The build order matters and follows the **four Cs**:

| C | What it means | Layer |
|---|---|---|
| **Context** | Who you are, your business, your knowledge — in files | Second brain |
| **Connections** | Live data the system can reach (email, calendar, revenue) | Second brain |
| **Capabilities** | Repeatable things the system can do (skills, workflows) | AI OS |
| **Cadence** | Things that run on a schedule/trigger, without you watching | AI OS |

**Rules of the road:**

- **Audit before building.** Never assume a blank slate. If anything exists, preserve it.
- **Strongest model designs; cheapest model runs.** Use Fable for the audit, architecture, routing rules, and safety. Once the system is stable, Sonnet does daily work and Haiku does grunt work.
- **Static before live.** Markdown files can't send a discount code to 150,000 people. Live connections come late and one at a time.
- **Automation comes last.** It must be earned by workflows that worked manually, repeatedly.
- **Permissions, not prompts.** A prompt is not a permission layer. Safety comes from what keys can physically do.
- **Tool-agnostic core.** The asset is folders, markdown, skills, logs, and routing logic. Claude Code is the current engine; the system survives any engine swap.
- **Teaching Mode on.** The AI explains major steps in plain language as it works, so you learn how the system works instead of watching it silently rearrange your digital life.

**Time to set up:** a focused day for Stages 0–9. Stages 10–12 happen over weeks, deliberately.

---

## 2. The concepts, in plain English

**Second brain** — Your knowledge, written down in files an AI can read. The test: ask the AI about your business. If the answer sounds like a stranger wrote it, the second brain is thin. If it sounds like a co-founder, it's working.

**AI operating system (AI OS)** — Everything that lets an AI *act* on the second brain: routing rules, skills, model strategy, safety rules, and eventually live connections and automations. Second brain = knows things. AI OS = does things.

**Context** — Everything the AI can see when answering you. In this system, context lives in files, so it's permanent, inspectable, and editable — unlike chat memory.

**Static knowledge vs. live data** — Static: your background, past decisions, transcripts — write once, read often. Live: email, calendar, revenue — changes constantly and must be fetched fresh. The OS keeps them physically separated (static in `01`–`04`, live registered in `05_connections/`) because live data requires keys, and keys carry risk.

**Connections** — Registered, approved channels to live data (an API, a CLI, an MCP server). Riskier than notes because a connection might be able to *do* things, not just read things.

**Capabilities** — Repeatable things the system can do. Mostly **skills**: a skill is just a markdown file containing instructions for a task you do repeatedly. If you write the same prompt twice, that's a skill waiting to be saved.

**Subagents / worker models** — Cheaper AI sessions you delegate narrow jobs to ("summarize these ten transcripts"), which return concise results to the main session. Like an assembly line: each worker does one thing well; the main session integrates.

**Cadence** — Workflows that run on a schedule or trigger, without you watching. Powerful, and the riskiest layer: cost, risk, and maintenance all go up. That's why it comes last and must be earned.

**`CLAUDE.md` as the router** — The file Claude reads first. It's not an encyclopedia; it's a *router*: "user info lives here, projects live there, check the safety rules before doing X." It makes the AI look things up instead of guessing.

**Process tracker** — `OS_SETUP_TRACKER.md`, a visible checklist the AI opens at session start, so it always knows what stage you're in, what's done, what's next, and what not to touch. Without it, every session starts amnesiac.

**Architecture vs. automation** — Architecture is *where things live and how they're found* (folders, names, indexes). Automation is *things happening by themselves*. Beginners reach for automation first; architecture first makes everything later cheap and safe.

---

## 3. The audit-first setup process (Stage 0)

**Never build until you've audited.** The audit determines whether you start at Stage 0 or skip ahead, and what must be preserved.

### Audit questions

System existence: Does an AI OS folder already exist? A `CLAUDE.md`? Existing folders, notes, projects, skills, logs, scripts, automations, knowledge bases?

Navigability: Is the structure intuitive to a human (could you drill to any file by hand)? Could an AI navigate it without long searches? Are important files scattered, duplicated, outdated, or unclear?

**Safety (most important):** Are there live connections, API keys, MCP servers, CLIs, or automations? Can anything **send, publish, delete, charge, edit, or message** without a human? Are any keys broader than needed?

Stage: Which pieces of Stages 0–12 already exist? Where should the process actually start?

Disposition: What gets preserved as-is? Archived (to `10_archive/`, never deleted)? Renamed? Restructured? **What must not be touched without explicit approval?**

### Audit report template

```markdown
# AI OS Audit — YYYY-MM-DD
## Current state summary        (3–6 sentences, plain language)
## Detected stage               (Stage N, and why)
## Existing assets              (what exists and is worth keeping)
## Missing assets               (what the OS needs that isn't there)
## Architecture problems        (duplication, scatter, unclear names, dead files)
## Safety / permission concerns (keys, write access, automations — flag everything)
## Recommended starting point   (which stage to begin at)
## Recommended changes          (preserve / archive / rename / restructure — itemized)
## Do-not-touch-yet list        (requires explicit user approval)
## Next three actions           (concrete, ordered, with recommended model)
```

If nothing exists, the report says so in one line and setup proceeds from square one.

**Model: Fable.** This is the single highest-leverage use of the expensive model — it shapes everything after.

---

## 4. The adaptive stage checklist

Each stage works whether you're starting blank or improving a messy existing system. "Next prompt" = what to paste into Claude Code to run the stage.

---

### Stage 0 — Audit the current system
- **Goal:** Know what exists before changing anything.
- **Inspect first:** Everything. That's the point.
- **You create/change:** Nothing yet.
- **Claude does:** Runs the bootstrap prompt (§5), produces the audit report.
- **Model:** Fable.
- **Done when:** Audit report exists; starting stage agreed; do-not-touch list written.
- **Common mistakes:** Skipping straight to building; letting the AI "clean up" during the audit.
- **Next prompt:** the full bootstrap prompt in §5.
- **Teaching Mode:** "I'm taking inventory before touching anything — like a contractor inspecting a house before renovating. Demolition before inspection destroys things you wanted to keep."

### Stage 1 — Decide the default workflow
- **Goal:** Commit to doing daily AI work in ONE place (Claude Code, in the AI_OS folder) instead of scattered tabs and tools.
- **Inspect first:** Where you currently do AI work; which subscriptions/tabs you'd be replacing.
- **You create/change:** A habit, plus a note in `01_profile/PREFERENCES.md` naming your default harness.
- **Claude does:** Records the decision in the tracker.
- **Model:** Fable (it's a design decision) — but it's a 10-minute conversation, not a build.
- **Done when:** You can say "when I want AI help, I open ___" without hesitation.
- **Common mistakes:** Building the OS but continuing to live in other tools — then the brain never accumulates context.
- **Next prompt:** "Record in the tracker and my preferences that my default workflow is Claude Code opened in my AI_OS folder. Then tell me what Stage 2 involves."
- **Teaching Mode:** "An OS doesn't start with architecture; it starts with a default. Every conversation here adds context to your files. Conversations elsewhere evaporate."

### Stage 2 — Create or clean up the root AI OS folder
- **Goal:** One root folder that contains (or indexes) everything.
- **Inspect first:** Existing candidate folders; where current work lives.
- **You create/change:** The `AI_OS/` root (or adopt your existing root). Existing related projects can move inside (the "other worlds" pattern: keeping sibling projects inside the root so one session can reach all of them and syncing is one push) — or stay put and be indexed.
- **Claude does:** Creates/confirms root; moves nothing without approval.
- **Model:** Sonnet (design was settled in the audit).
- **Done when:** Root exists; you know what's inside vs. indexed-from-outside.
- **Common mistakes:** Six scattered "AI" folders; moving big existing projects before deciding whether indexing would do.
- **Next prompt:** "Per the audit, set up my AI_OS root folder. List what you propose to move into it vs. index in place, and wait for my approval before moving anything."
- **Teaching Mode:** "One root means one place to open, one thing to back up, one tree the AI can search. For existing folders we can either move them in or leave a signpost — moving is tidier, signposts are safer."

### Stage 3 — Create or revise the folder structure
- **Goal:** The numbered folder tree (§6 / the starter kit) exists, or your existing structure is mapped onto it.
- **Inspect first:** Existing folders and their contents; the audit's rename/restructure recommendations.
- **You create/change:** Folders + README in each explaining what belongs there.
- **Claude does:** Builds missing folders; proposes mappings for existing ones; archives confusing material to `10_archive/raw_imports/` rather than deleting.
- **Model:** Fable to approve the mapping if the existing system is messy; Sonnet to execute.
- **Done when:** Every existing file has a home or an index entry; every folder has a README.
- **Common mistakes:** Renaming everything at once (breaks your own muscle memory and any existing links); creating 40 empty folders "for later."
- **Next prompt:** "Create the standard folder structure per the starter kit. For each of my existing folders, propose: keep in place + index, move, or archive. Show me the full plan before executing."
- **Teaching Mode:** "Folder structure is how both you and the AI find things. The numbers force a stable order; the READMEs mean the AI never has to guess what a folder is for."

### Stage 4 — Build or consolidate the static second brain
- **Goal:** `01_profile/` and `02_business/` filled in; existing notes/transcripts landed in `04_knowledge/`.
- **Inspect first:** Existing bios, about pages, old plans, anything already written about you/your business — consolidate, don't re-create.
- **You create/change:** Answer interview questions; review what Claude drafts.
- **Claude does:** Runs the **Grill Me** skill; extracts from existing documents (delegating extraction to Haiku); drafts the static files; flags contradictions instead of resolving them silently.
- **Model:** Sonnet, with Haiku workers for extraction.
- **Done when:** The gut check passes — "ask it about your business; does the answer sound like a teammate or a stranger?"
- **Common mistakes:** Pasting in 200 pages without distillation; perfectionism (these files improve forever — "last updated" dates handle staleness).
- **Next prompt:** "Use the grill_me skill to fill in my profile and business files. First check 04_knowledge and my existing docs for answers you can extract instead of asking me."
- **Teaching Mode:** "This is the brain part of the second brain. Everything you put here is something you'll never have to repeat to an AI again."

### Stage 5 — Create or revise the root CLAUDE.md router
- **Goal:** A `CLAUDE.md` that routes: identity, where things live, session-start ritual, the binding rules.
- **Inspect first:** Any existing CLAUDE.md — merge, don't discard.
- **You create/change:** Review the draft; confirm it reflects YOUR system.
- **Claude does:** Writes/revises it (the starter kit version is the base).
- **Model:** Fable — this file steers every future session.
- **Done when:** A brand-new session, given only CLAUDE.md, correctly answers "where would you look for X?" for five test questions.
- **Common mistakes:** Stuffing all knowledge into CLAUDE.md (it's a router, not a wiki); writing rules no one maintains.
- **Next prompt:** "Adapt the starter CLAUDE.md to my actual system: correct the folder map, reference my real project locations, and keep it under ~200 lines. Then quiz yourself: where would you look for [5 things]?"
- **Teaching Mode:** "I'm creating the instructions that tell Claude where to look before answering, so it doesn't rely on memory or guesswork. Think of it as the receptionist who knows which room everything is in."

### Stage 6 — Add the process tracker
- **Goal:** `OS_SETUP_TRACKER.md` live and accurate.
- **Inspect first:** Any existing TODO/status files to merge.
- **You create/change:** Confirm current stage and next action.
- **Claude does:** Instantiates the tracker (starter kit version), fills in actual status.
- **Model:** Sonnet.
- **Done when:** A fresh session reading only the tracker can state your stage, next action, and what not to touch.
- **Common mistakes:** Treating it as write-once; not updating "last updated."
- **Next prompt:** "Set up OS_SETUP_TRACKER.md to reflect where we actually are: mark completed stages, set the next action, and list any do-not-touch items from the audit."
- **Teaching Mode:** "The tracker is the system's short-term memory between sessions. Without it, every new session starts by guessing where we left off."

### Stage 7 — Add model-routing rules
- **Goal:** `00_system/MODEL_ROUTING.md` in place (§7 of this guide; starter kit includes it).
- **Inspect first:** Your actual plan/budget; which models you have access to.
- **You create/change:** Confirm the tiers match your reality.
- **Claude does:** Adapts the routing file; adds the summary to CLAUDE.md.
- **Model:** Fable (routing decisions shape all future costs).
- **Done when:** For any task you name, Claude states the model and a one-line reason.
- **Common mistakes:** Using the expensive model for everything "to be safe"; never delegating to Haiku.
- **Next prompt:** "Review MODEL_ROUTING.md against my subscription and usage. Adjust the rules, then tell me — for my five most common tasks — which model you'd use and why."
- **Teaching Mode:** "I'm writing the rules for which AI brain handles which work. The expensive model designs; the cheap models execute. It's a senior architect with junior staff — you don't pay architect rates for data entry."

### Stage 8 — Add verification and safety rules
- **Goal:** `00_system/SAFETY_RULES.md` (with gates) and the verify_output habit in place.
- **Inspect first:** ANY existing keys, scripts, or automations found in the audit — these get registered or disabled first.
- **You create/change:** Read the safety file fully (it's short). This one you actually read.
- **Claude does:** Instantiates safety rules; inventories anything that can currently touch the outside world.
- **Model:** Fable.
- **Done when:** You can answer "what can my system physically do right now without me?" — and the answer is "nothing external."
- **Common mistakes:** Treating safety as paranoia ("it's just my email"); trusting instructions instead of scopes.
- **Next prompt:** "Instantiate SAFETY_RULES.md. Then inventory everything in my current setup that could possibly send, publish, delete, charge, or message, and tell me what each thing can physically do."
- **Teaching Mode:** "I'm making sure Claude cannot accidentally send, delete, publish, or change important things without your approval. The rule is keys, not prompts: if the AI doesn't hold the key to the email room, no misunderstanding can send an email."

### Stage 9 — Create first skills
- **Goal:** The five starter skills (§9) exist in `06_skills/` and have each been run once.
- **Inspect first:** Saved prompts or routines you already reuse — those are skills in disguise.
- **You create/change:** Run each skill once; give feedback.
- **Claude does:** Instantiates the five skills; converts your existing reusable prompts into skills too.
- **Model:** Sonnet.
- **Done when:** All five run successfully; at least one improved from your feedback.
- **Common mistakes:** Building 20 speculative skills nobody runs; expecting a skill to be perfect on the first try (every run is data — "here's what I liked, here's what I didn't, update the skill").
- **Next prompt:** "Run the grill_me skill now. Afterwards I'll give feedback — apply it to the skill file so next time is better."
- **Teaching Mode:** "A skill is just a saved set of instructions for something you do repeatedly. Writing the same prompt every Monday means Monday should be a file."

### Stage 10 — Add live connections, carefully ⚠️ GATE
- **Goal:** First read-only connection(s), one at a time, each tested and registered.
- **Inspect first:** Your tier-one list — what do you reach for weekly? (Revenue, customers, calendar, comms, tasks, meetings, knowledge.) Which has the cleanest read-only access (API or CLI)?
- **You create/change:** Approve each connection; create keys yourself with the narrowest scope.
- **Claude does:** Researches the API/CLI docs into `05_connections/api_docs/`; proposes the narrowest scope; tests manually; logs the test; registers the connection in CONNECTIONS_INDEX with what it can *physically* do.
- **Model:** Fable for permission/safety design per connection; Sonnet for implementation.
- **Done when:** Connection works read-only, tested, registered. THEN consider the next one.
- **Common mistakes:** Connecting five tools in one afternoon; using a full-access key "temporarily"; skipping the index entry.
- **Next prompt:** "I want to connect [tool], read-only. Research its API/CLI options, propose the narrowest possible key scope, and walk me through creating the key myself. Do not proceed past planning until I approve."
- **Teaching Mode:** "I'm separating information that rarely changes, like your background, from information that changes often, like email or revenue — and for the live kind, we're installing a window, not a door. Read-only means the system can look but never touch."

### Stage 11 — Convert workflows into cadence/automation ⚠️ GATE
- **Goal:** Only battle-tested workflows get automated, each with owner, logs, rollback, and review cadence.
- **Inspect first:** `07_workflows/manual/` — what has run successfully 3+ times unchanged? What's the trigger type (manual / event / schedule)?
- **You create/change:** Approve each automation explicitly; own it (or assign an owner).
- **Claude does:** Moves the workflow through `ready_for_automation/`; builds it (script, scheduled routine, etc.); sets up `08_logs/automation_logs/`; documents rollback.
- **Model:** Fable reviews the safety case; Sonnet builds.
- **Done when:** It runs on its trigger, logs every run, and you review it on schedule. More autonomy ≠ forget about it.
- **Common mistakes:** Automating something run once; no logs; no owner; automation quietly drifting after an upstream tool changes.
- **Next prompt:** "Workflow [X] has run manually [N] times — its runs are logged in 07_workflows/manual/. Assess whether it's ready for automation: trigger, failure modes, rollback plan, and what could go wrong. Recommendation only — don't build yet."
- **Teaching Mode:** "Automation means this will happen while you sleep. That's the whole appeal and the whole risk, which is why it's earned: cost, risk, and maintenance all rise with autonomy."

### Stage 12 — Review, prune, improve (ongoing)
- **Goal:** The OS gets better with use instead of rotting.
- **Inspect first:** The weekly review report.
- **You create/change:** 20 minutes weekly; decisions on archive/skill/promotion candidates.
- **Claude does:** Runs weekly_review (Sonnet); quarterly full re-audit (Fable).
- **Model:** Sonnet weekly, Fable quarterly.
- **Done when:** Never. That's the point — there's no such thing as a finished system, only a maintained one.
- **Common mistakes:** Skipping reviews once the novelty fades; deleting instead of archiving; never re-running the audit.
- **Next prompt:** "Run the weekly_review skill."
- **Teaching Mode:** "Every use of the system is data. Mistakes become instructions, repeated tasks become skills, stale files become archives. The loop is the product."

---

## 5. The first-run bootstrap prompt (run this in Claude Code with Fable)

Copy/paste everything below as your first message, with Claude Code opened in the folder where your AI OS should live (or already partially lives):

```text
You are setting up (or improving) my AI operating system — a second brain made of
folders and markdown files, plus routing logic, skills, and a process tracker.
I may be starting from zero, or I may already have a partial or messy system.
DO NOT assume a blank slate.

Work through this, in order:

1. AUDIT FIRST. Inspect the current folder/repo. Identify whether an AI OS already
   exists in any form: look for any CLAUDE.md or equivalent, skills, trackers, logs,
   knowledge folders, project folders, scripts, API references, credentials, MCP
   configs, or automations.

2. Write an audit report (save as AI_OS_AUDIT_YYYY-MM-DD.md) containing:
   current state summary, detected stage, existing assets, missing assets,
   architecture problems, safety/permission concerns (flag ANYTHING that can send,
   publish, delete, charge, edit, or message), recommended starting point,
   recommended changes (preserve / archive / rename / restructure), a
   do-not-touch-yet list, and the next three actions.
   If no existing system is found, say so clearly and proceed with square-one setup.

3. Based on the audit, propose what to preserve, restructure, archive, or create.
   Preserve and index existing work rather than deleting or overwriting it.
   Archive confusing material to 10_archive/ — never delete anything.
   WAIT FOR MY APPROVAL before moving or restructuring anything that already exists.

4. Create the starter folder structure (00_system through 10_archive, with READMEs)
   only where appropriate — fill gaps, don't duplicate what exists.

5. Create or revise the root CLAUDE.md as a ROUTER: session-start ritual, where
   things live, stage detection, Teaching Mode, model-routing summary, operating
   rules, and safety rules. Merge with any existing CLAUDE.md rather than replacing it.

6. Create or revise OS_SETUP_TRACKER.md, mark the actual current stage, check off
   anything that already exists, and set the next action.

7. Interview me ONLY for truly necessary missing information — one question at a
   time, and check my existing files for the answer before asking.

8. Finish by telling me: my current stage, the next three actions, and which model
   (Fable / Opus / Sonnet / Haiku) each action should use.

Hard constraints:
- Do not set up any live connections, API keys, scripts with external side effects,
  or automations in this session. Static system first; I will explicitly approve
  that step later.
- Anything that can send, publish, delete, charge, modify databases, or message
  people requires my explicit approval. A prompt is not a permission layer.
- Prefer preserving and indexing over moving; prefer archiving over deleting.

As you work, use Teaching Mode. Explain each major step in plain language so I
understand what you are doing, why it matters, and what I should check. Keep
explanations short unless I ask for more detail.
```

---

## 6. Folder architecture

The starter tree (shipped ready-made in the `AI_OS/` kit — every folder has a README explaining what belongs, what doesn't, what to check before modifying, and which layer it is):

```text
AI_OS/
  CLAUDE.md                  # the router — read first, every session
  OS_SETUP_TRACKER.md        # current stage, next action, logs

  00_system/                 # SYSTEM — rules about the OS itself
    README.md
    MASTER_INDEX.md          # the map; update when anything is hard to find
    MODEL_ROUTING.md         # which model for which work
    SAFETY_RULES.md          # binding; keys-not-prompts; the gates
    CHANGELOG.md             # one line per system change

  01_profile/                # STATIC CONTEXT — who you are
    USER_PROFILE.md  PREFERENCES.md  GOALS.md  DECISIONS.md

  02_business/               # STATIC CONTEXT — what your business is
    BUSINESS_OVERVIEW.md  CUSTOMERS.md  OFFERS.md  MARKETING.md  OPERATIONS.md

  03_projects/               # WORKING AREA — one folder per project, BRIEF.md each
    README.md  active/  paused/  completed/

  04_knowledge/              # STATIC CONTEXT — the library (mostly append-only)
    README.md  notes/  transcripts/  research/  references/

  05_connections/            # LIVE CONNECTIONS ⚠️ — registry of live data sources
    README.md  CONNECTIONS_INDEX.md  api_docs/  credentials_notes/  test_logs/
                             # never actual keys/secrets — only notes about them

  06_skills/                 # CAPABILITY — one markdown file per reusable skill
    README.md  grill_me.md  update_context.md  create_project_brief.md
    weekly_review.md  verify_output.md

  07_workflows/              # CAPABILITY → CADENCE — trust ladder, left to right
    README.md  manual/  ready_for_automation/  automated/

  08_logs/                   # LOGS — append-only; never edit past entries
    README.md  session_logs/  decision_logs/  error_logs/  automation_logs/

  09_outputs/                # OUTPUTS — results, never sources
    README.md  drafts/  reports/  exports/  deliverables/

  10_archive/                # ARCHIVE — nothing is deleted, things are retired
    README.md  old_versions/  deprecated/  raw_imports/
```

### If you already have a system: mapping rules

- **Map, don't migrate, by default.** For each existing folder, ask: does it correspond to one of the numbered folders? If yes and moving is cheap, move it. If moving would break links, habits, or tools, **leave it in place and add it to `MASTER_INDEX.md → External/legacy locations`** — an index entry is a signpost; it gives the AI navigation without disturbing anything.
- **Don't rename folders that** other tools reference, that sync services watch, that teammates use, or whose names you've memorized. A README inside the oddly-named folder ("this is effectively 04_knowledge") costs nothing.
- **Create an index instead of moving when**: the folder is large, actively used, shared, or you're unsure. Moving is forever-ish; indexing is reversible in one line.
- **Archive, don't delete.** Confusing, outdated, or duplicate material goes to `10_archive/` (`raw_imports/` for whole messy folders, kept as-is until sorted). Log every archive move in `CHANGELOG.md` so it's findable later.
- **Preserve while improving:** the goal of restructuring is that *navigation* improves. If after the change you can't find something you could find before, the change failed — roll it back.

---

## 7. Model-routing guide

Full rules ship in `AI_OS/00_system/MODEL_ROUTING.md`. The essence:

> **Use the strongest model to design the system, then use cheaper models to run the system.**

| Model | Role | Use for |
|---|---|---|
| **Fable** | Architect | Initial audit, architecture, system design, major refactors, root instructions, safety design, complex stage detection, high-stakes verification |
| **Opus** | Second opinion | Architecture critique, deep reasoning if Fable unavailable, refining complex systems |
| **Sonnet** | Builder (default) | Day-to-day implementation, writing, coding, project work, editing files, creating skills, running established workflows |
| **Haiku** | Worker | Extraction, summarization, tagging, classification, formatting, batch cleanup, low-risk parallel tasks |

**When NOT to use Fable:** routine writing, repetitive formatting, simple summaries, file cleanup, daily execution once the architecture is stable. Fable is roughly 2× Opus pricing and eats session limits fast — spend it only on decisions that affect the future shape of the system.

**Switching:** Fable → Sonnet the moment design becomes execution. Sonnet → Haiku when a subtask is mechanical and batchable. Back up to Fable only for hard-to-reverse decisions.

**Delegation contract:** workers get one narrow job plus exact inputs; workers return concise structured output (summary, facts, table — never raw dumps); the main session integrates; workers never touch system files.

**Logging:** notable model choices go in the tracker's "Model usage notes" — especially anywhere Fable was spent, so you can see your design budget.

**Explaining (Teaching Mode):** one sentence per choice — "this shapes the whole system → Fable"; "routine writing → Sonnet"; "mechanical extraction → Haiku, summary comes back to me."

---

## 8. Safety and permission guide

Full binding rules ship in `AI_OS/00_system/SAFETY_RULES.md`. The non-negotiables:

1. **A prompt is not a permission layer.** Assume: if it *can*, someday it *will*. (Origin story: an agent misread a task list and emailed a discount code to ~150,000 people. The prompt wasn't the failure — holding the email key was.)
2. **No write/send/delete/payment permissions by default.** Read-only keys wherever possible; narrowest scope always.
3. **One connection at a time**, manually tested and logged before anything relies on it.
4. **Explicit human approval** for anything that can send emails, message people, charge money, delete data, modify databases, publish content, or trigger external actions.
5. **Every automation** gets an owner, logs, a rollback plan, and a review cadence — or it doesn't ship.
6. **Before any integration,** Claude proposes permission boundaries and lists what the tool/key can *physically* do — not just what it's told to do.
7. **Risky task? Stage it.** Draft-then-human-sends beats auto-send. Read-then-propose beats write.
8. Safety decisions get explained in plain language, every time.

**The ten gates** (each requires explicit approval to pass): adding live data · creating/storing API keys · scripts with side effects · write access · sending email/messages · publishing · modifying customer data · payments · deleting/archiving files · scheduling automations.

---

## 9. The five starter skills

All five ship as complete files in `AI_OS/06_skills/` — each with purpose, when-to-use, inputs, exact instructions, output format, model, safety notes, improvement plan, logging, and a Teaching Mode explanation. Summary:

| Skill | What it does | Model | Teaching Mode, in one line |
|---|---|---|---|
| **grill_me** | Interviews you, one question at a time (15–30 questions), saves the Q&A, proposes updates to your static files | Sonnet | "Moving knowledge from your head into files, so no future session has to ask again" |
| **update_context** | Routes new facts to the right file; checks for existing/conflicting info first; archives before big rewrites | Sonnet (+Haiku extraction) | "Filing information where future sessions will look for it, without creating contradictions" |
| **create_project_brief** | One-page BRIEF.md per project: goal, done-when, context links, deliverables, model plan, safety flags | Sonnet | "Writing the project's memory so a cheaper model can continue the work next week" |
| **weekly_review** | Reads tracker, projects, and logs; reports wins/stuck/system health/skill candidates/next-3; updates tracker | Sonnet (+Haiku; Fable quarterly) | "The maintenance heartbeat — catches rot early, turns repeated work into skills" |
| **verify_output** | Source-checks every claim, tests every path, reviews as the audience would; PASS/FIX/FAIL verdict; errors become new checks | Sonnet; **Fable/Opus for high-stakes** | "Checking work like you'd check an intern's: where did each fact come from, and does it actually work?" |

**The skill mindset:** a skill is never finished. Every run is data — say what you liked and didn't, have Claude update the skill file, and next week's run is better. When you catch yourself writing the same prompt twice, that's a new skill.

---

## 10. The architecture improvement loop

The system compounds because every use generates data:

- Claude **struggles to find** something → update `MASTER_INDEX.md` or the folder map.
- Claude **makes a mistake** → update `CLAUDE.md`, the relevant skill, or the tracker, and log it in `error_logs/` — "fix the instruction so it never happens again."
- A task **repeats** → turn it into a skill.
- A skill is **reliable** → consider documenting it as a workflow (`07_workflows/manual/`).
- A workflow is **reliable AND safe** → consider promotion toward cadence/automation (gated, approved).
- Files go **stale** → archive them, never delete.
- The OS feels **confusing** → run another Fable audit.
- The user gives **feedback** → convert it into a system improvement where appropriate.

In plain language: mistakes aren't failures, they're patches waiting to be written. A slip-up that becomes a rule makes the system permanently better; a slip-up that's merely forgiven will happen again. This loop — use, notice, fold back in — is the difference between a system that compounds and a folder of markdown that rots.

---

## 11. Verification checklist (run before calling setup complete)

Claude should verify, with file paths as evidence:

- [ ] Folder structure exists (00–10, with READMEs)
- [ ] `CLAUDE.md` exists and contains routing instructions (where-to-look table, session-start ritual)
- [ ] `OS_SETUP_TRACKER.md` exists and shows the current stage accurately
- [ ] The system knows where to look for: user profile, business context, projects, knowledge, skills, logs, outputs (test: ask 7 "where would you look for…" questions in a fresh session)
- [ ] Live connections are clearly separated from static context (`05_connections/` + index)
- [ ] Unsafe permissions are blocked or explicitly marked as requiring approval (`SAFETY_RULES.md` gates; nothing external currently possible without a human)
- [ ] Model-routing rules exist (`MODEL_ROUTING.md`) and CLAUDE.md summarizes them
- [ ] All five starter skills exist and have each run at least once
- [ ] Teaching Mode is present in both this guide and `CLAUDE.md`, and is On in the tracker
- [ ] A fresh session, reading only the tracker + CLAUDE.md, can state where the user is in the process
- [ ] A beginner reading the tracker can tell what to do next

### Done when

Setup (Stages 0–9) is done when: the audit report exists; the gut check passes (answers sound like a teammate); a fresh session orients itself from the tracker in under a minute; nothing in the system can touch the outside world without you; and you know which model you'd use for tomorrow's first task — and why.

Stages 10–12 are never "done." They're how the system lives.

---

*Starter kit: the complete `AI_OS/` folder ships alongside this guide. Copy it, open Claude Code inside it, paste the bootstrap prompt from §5, and begin.*
