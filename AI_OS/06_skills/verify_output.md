# Skill: Verify Output

## Purpose
Check work before trusting it. Turns "70% right on the first pass" into "92% right," and catches confident errors before they spread.

## When to use
- Before any deliverable is called done
- Before anything is sent, published, or shown externally (mandatory)
- After a worker model returns results
- Whenever an answer cites facts about the user's life/business

## Required inputs
- The output to verify
- Its purpose and audience

## Instructions (the prompt)
1. **Source check:** for every factual claim, name the exact source file (or live source). No source → mark it `[UNVERIFIED]`.
2. **Freshness check:** is any cited static data old? Check "Last updated" dates. Flag anything that may have changed.
3. **Path check:** every file path, link, and reference actually exists. Test them.
4. **Audience pass:** re-read as the intended audience would (a beginner, a customer, an engineer). Note what confuses or breaks.
5. **Functional check:** if it's runnable/clickable, run/click it. Verify the way a careful human reviewer would.
6. Output a verdict: PASS / PASS WITH FIXES (listed) / FAIL (reasons).
7. If verification catches a real error, log it in `08_logs/error_logs/` with the fix made so it can't recur.

## Output format
Short verification report: verdict, issues found, fixes applied, remaining `[UNVERIFIED]` items.

## Recommended model
Sonnet for routine work. **Fable (or Opus) for high-stakes outputs** — external, financial, or architectural. Ideally verify in a fresh session so the verifier isn't grading its own homework.

## Safety notes
Verification is read/test only. It never "fixes" by taking external actions. A failed verification blocks send/publish gates.

## Improving this skill
Every error that slips past verification becomes a new check above.

## Log after use
Error log entries for real catches; nothing otherwise.

## Teaching Mode explanation
"I'm checking the work the way you'd check an intern's: where did each fact come from, is it current, does it actually work? AI states wrong things confidently — verification is how the system earns trust."
