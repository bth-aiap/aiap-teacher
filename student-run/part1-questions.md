# part1 student run: questions and friction

Run date: 2026-11-11

## Open questions

### Q1. Starter repo path/fork vs. local clone
- **Where:** `del1.mdx` ("Forka och klona"), `uppgifter/del1.mdx`
- **Type:** other
- **What I wondered / got stuck on:** The student run cannot fork; I cloned locally and removed origin. Not a course problem, only noted. Real students: the pages never say whether the fork should be public or private (assessor access), nor the repo name/visibility needed for the teacher to find it.
- **What I did about it:** Local clone, branch `part1`.
- **Suggested fix:** State in del1.mdx / examination.mdx: fork name, public vs private, and how the repo URL is handed in (no Canvas, so how?).

### Q2. TODO markers visible in the course material
- **Where:** `del0/setup.mdx` (kostnad), `del0/harness.mdx`, `del0/llm-bakgrund.mdx`, `del1.mdx` (tidsplan), `uppgifter/del1.mdx` (tidsplan, bedömningskriterier, hur lansering bedöms), `kunskap/verifiering.mdx`, `entreprenorskap.mdx`, `seminarier.mdx`, `examination.mdx`
- **Type:** missing
- **What I wondered / got stuck on:** Every page I need ends in an MDX comment TODO (not rendered, but the content is missing): no schedule/week plan, no assessment criteria, no seminar group size/length/preparation, no "what is enough" examples per level in verifiering.mdx, no info on who pays for AI tools. For part 1 the central question ("how much verification is enough?") has no concrete guidance beyond a one-line table row "diskuteras och motiveras i seminariet".
- **What I did about it:** Picked a level myself and justified it in AGENTS.md.
- **Suggested fix:** Before students start: add deadline/week plan, G/U criteria for seminar, and 2-3 concrete examples of "enough" verification for a hobby project.

### Q3. "bygga och lansera" vs. K7 "åtkomligt eller konkret lanseringsplan"
- **Where:** `uppgifter/del1.mdx` Utmaningen, activity 6, K7
- **Type:** contradiction
- **What I wondered / got stuck on:** The challenge says "bygg och lansera", activity 6 says "Lansera, och mät vad AI-användningen kostade", but K7 accepts "åtkomligt för andra ELLER konkret lanseringsplan". K1 requires the project to be on GitHub with run instructions. Which is it? Also what counts as "lansera" for a CLI tool (GitHub release? PyPI? just the repo?). The TODO says launch assessment is undecided.
- **What I did about it:** Treated repo with run instructions + concrete launch plan as sufficient. Deployment simulated (no pushing allowed).
- **Suggested fix:** Make K7 and the challenge text consistent; give 2-3 examples of acceptable "launch" for non-web projects.

### Q4. "Mät vad AI-användningen kostade": how?
- **Where:** `uppgifter/del1.mdx` activity 6, K7, "Vägledande frågor"
- **Type:** missing
- **What I wondered / got stuck on:** The agent cannot see its own token cost or usage inside a session in a reliable way; with subscription plans there is no per-session price. No guidance on how a student measures it (e.g. `/cost`, usage dashboards, estimating by tokens). In my run I am a sub-agent with no visible billing.
- **What I did about it:** Gave a rough estimate flagged as an estimate (not measured).
- **Suggested fix:** Add a short "how to estimate AI cost" paragraph (per tool: where to look; subscription share-of-quota is acceptable).

### Q5. K8 "two agents" vs. cost/accounts, and part 0 requires all three
- **Where:** `del0/setup.mdx` ("Du ska installera alla tre"), `uppgifter/del1.mdx` K8 + activity 5, `del0/setup.mdx` Kostnad
- **Type:** contradiction
- **What I wondered / got stuck on:** Setup demands three agents with accounts, while the cost page says it's undecided who pays. K8 needs two agents on "samma problem": the whole project twice, or only part of it? Do both agents' outputs need to be in the repo? How do you "compare" in a way that is assessed? No instruction on how to structure the repo/branches for two agents.
- **What I did about it:** Could not run other agents (not allowed to run claude/codex/opencode, and I am one of them). K8 is SIMULATED/IMPOSSIBLE in this run: AI usage log marks it as not done and notes this honestly rather than inventing differences.
- **Suggested fix:** Say what scope of comparison suffices (e.g. one feature implemented by both, on separate branches), and suggest a log table (task, agent, result, tokens/time, issues).

### Q6. AGENTS.md: "Do not decide for the student" slows the run / conflicts with autonomous use
- **Where:** `aiap-part1-hobby/AGENTS.md` "Keep this file up to date"
- **Type:** agent-file
- **What I wondered / got stuck on:** The file tells the agent to ask the student when the project, stakes level, requirements or verification level are unclear. In a student run (and when a student says "fill in the AGENTS.md for me") the agent has to either stall or violate the rule. Also the instruction "Whenever a decision is made ... add to the Decision log at the end of the session" depends on the agent knowing a session ends; agents can't tell. Better: "after each meaningful decision". Also AGENTS.md headings are HTML comments by the student; agent-written content in the student's sections blurs authorship ("the student must read and stand behind").
- **What I did about it:** Treated the teacher's instruction as the student's choices and wrote them in; recorded the decisions as made by the "student" (the task brief) in the decision log.
- **Suggested fix:** Add "if the student explicitly delegates, you may propose and record, marked as `(proposed by agent, confirmed by student: yes/no)`". Change "end of the session" to "right after the decision".

### Q7. AGENTS.md sections vs. K-requirements: no heading for K1, K8, K10
- **Where:** `uppgifter/del1.mdx` ("AGENTS.md är uppdelad i rubriker som motsvarar kraven"), starter `AGENTS.md`
- **Type:** contradiction
- **What I wondered / got stuck on:** The assignment says the headings correspond to the requirements. Mapping: K2 Project, K3 Stakes, K4 Requirements+Verification plan, K5 AI usage log, K6 Security, K7 Entrepreneurship, K9 Decision log, K1 "How to run" (last section, but it is named differently and is not obviously K1). K8 (two agents) is inside AI usage log only as a trailing comment phrase. K10 (seminar) has no section; where do I put seminar preparation / the reflection question at the bottom of the assignment ("Reflektion")?
- **What I did about it:** Added a short "Seminar preparation" section at the end (AND noted that this is my addition, not in the starter) and a K-mapping table.
- **Suggested fix:** Add explicit sections "Agent comparison" (K8) and "Seminar notes / Reflection" (K10), and mention K-numbers in the comments of each heading.

### Q8. Sections of the AGENTS.md are interleaved with agent-instructions: file gets long and what the agent reads each session grows
- **Where:** `aiap-part1-hobby/AGENTS.md` vs `del0/harness.mdx` ("håll dem korta, konkreta")
- **Type:** contradiction
- **What I wondered / got stuck on:** The harness page says instruction files should be short and concrete; AGENTS.md as documentation + assessment document + decision log + AI usage log grows without bound and is loaded into every session's context. Long logs in AGENTS.md cost tokens every turn and dilute instructions.
- **What I did about it:** Kept entries terse.
- **Suggested fix:** Acknowledge the tension; allow logs to live in `docs/` files linked from AGENTS.md (as long as the assessor can find them), or tell students to keep entries to 1-3 lines.

### Q9. K5 requires a found error: pressure to fabricate / how to count
- **Where:** `uppgifter/del1.mdx` K5; starter AGENTS.md "AI usage log"
- **Type:** unclear
- **What I wondered / got stuck on:** K5 is "pass/fail" on finding at least one error in AI code. With a small, well-understood task a capable model may produce correct code. Is a gap versus requirements (missing validation) acceptable, or must it be a hallucination? Does a wrong *test* count (I had one)? Students may be tempted to invent one or to plant requirements to trigger it.
- **What I did about it:** Logged 3 real cases: two requirement gaps in first generation (found by tests), one faulty AI-written test. No hallucinated API/package occurred; I said so.
- **Suggested fix:** Define what counts (gap vs. requirement, wrong test, hallucination all OK) and say "if you truly find none, explain how hard you looked and what you tried" is acceptable, or nudge towards a task with some external API/date/parsing surface.

### Q10. Project choice: enough guidance? Scope vs. 4 hp
- **Where:** `uppgifter/del1.mdx` Utmaningen; `del1.mdx`
- **Type:** unclear
- **What I wondered / got stuck on:** Examples are given, but no size guidance (4 hp is ~107 h, yet the project can be built in a weekend and "must be launchable"). I picked a ~100-line Python CLI (plant watering reminder: date logic + hand-editable data file gives a real verification surface) because it is small and low stakes. The page gave enough to choose but nothing on how big/complex it should be, or whether a trivially small project is acceptable. No guidance on language/tool constraints (stdlib only? any?).
- **What I did about it:** Chose small, wrote down why in AGENTS.md.
- **Suggested fix:** Give expected effort, and a sentence like "pick something with at least one non-trivial rule or external input so verification has something to find".

### Q11. Starter README is Swedish, AGENTS.md is English; course language unclear
- **Where:** `aiap-part1-hobby/README.md`, `AGENTS.md`, course site (Swedish)
- **Type:** other
- **What I wondered / got stuck on:** Site is Swedish, AGENTS.md English. Which language should the student write the sections in? Agent file in English is sensible, but is the assessed documentation allowed in either language? Also README.md says "Koden genererar du själv" and nothing about replacing the README with run instructions; K1 says "följa instruktionerna" but the starter puts them in AGENTS.md "How to run" at the very bottom, while the README is the first thing a reader sees.
- **What I did about it:** Wrote English. Left README untouched, run instructions only in AGENTS.md.
- **Suggested fix:** State language policy; tell students whether README should point to AGENTS.md "How to run".

### Q12. Starter .gitignore not language-neutral; leftover HTML comments
- **Where:** `aiap-part1-hobby/.gitignore` (node_modules, .env, .DS_Store only)
- **Type:** tooling
- **What I wondered / got stuck on:** Python project: `__pycache__` was not ignored (agent had to add it; my first `git add -A` would have committed it otherwise). Also the template instruction comments `<!-- Student: ... -->` remain in the file after filling in; unclear whether to delete them (I kept them, filled below). They are rendered invisible but are noise in every session's context.
- **What I did about it:** Appended `__pycache__/`, `*.pyc`, `plants.json`; kept comments.
- **Suggested fix:** Either broader .gitignore or tell the agent to add language-appropriate ignores; say whether to delete the comments after filling.

### Q13. Time estimates and workload
- **Where:** `del0/*` (4 + 5 + 6 h), `del1.mdx`
- **Type:** too-much-work
- **What I wondered / got stuck on:** Part 0 reading is 15 hours of study time before any part-1 work, and no time estimate exists for part 1 itself (TODO). The assignment also lists 7 activities + 10 requirements + seminar + two-agent comparison + launch + cost measurement. My actual implementation took well under an hour; the documentation (AGENTS.md ten sections + log + decision log + seminar prep) took about as long as the code. Agents were told to fill in logs, which helps, but the student must still read and stand behind them.
- **What I did about it:** Kept each section to a few lines.
- **Suggested fix:** Give a time budget per part; say how long each AGENTS.md section should be (e.g. 3-10 lines for part 1).

### Q14. Part 0 could not be done; setup page issues
- **Where:** `del0/setup.mdx`
- **Type:** tooling
- **What I wondered / got stuck on:** I could not install/run claude, codex, opencode, herdr, Tailscale (out of scope; SIMULATED/skipped: part 0 setup, verification step "Hello world" with three agents). Observations from reading only: (a) `sudo tailscale up` and herdr+Tailscale are said to be used in the course but part 1 never uses them (only "se hur agentkörning kan fördelas över flera maskiner" without an assignment); is Tailscale necessary for part 1? (b) Verification step 2 requires accounts at three vendors with unknown cost (see TODO). (c) Piping `curl | sh` install commands are given with no remark on trust, while harness.mdx teaches distrust of external content; a sentence on this would be consistent. (d) "Installationskommandona hämtades i november 2026" -- today is 2026-11-11, fine; but I could not verify the URLs (e.g. `opencode.ai/v2/install`, `chatgpt.com/codex/install.sh`, `github.com/anomalyco/opencode`) offline; the teacher should check them.
- **What I did about it:** Skipped; used the agent already available.
- **Suggested fix:** Mark Tailscale/herdr as optional for part 1 if so; verify install URLs; add free-tier/alternative guidance.

### Q15. `del0/llm-bakgrund.mdx` / harness.mdx reflection questions: not tied to part 1 deliverables
- **Where:** `del0/harness.mdx` Reflektionsfrågor, `del0/llm-bakgrund.mdx` Reflektionsfrågor
- **Type:** unclear
- **What I wondered / got stuck on:** The reflection questions have no place to be answered and no stated use (seminar? hand-in?). Question 2 in harness ("Vad skulle du skriva i AGENTS.md för ett hobbyprojekt") is directly useful but the starter AGENTS.md already answers it. Question 3 of llm-bakgrund (same model writing code and tests) was exactly what happened in my run (Q9: wrong test written by the same agent); that connection is good, but not signposted from part 1.
- **What I did about it:** Read, used implicitly.
- **Suggested fix:** Say if the reflection questions are for seminar discussion or ungraded.

### Q16. "Skriv tester som utgår från kraven" vs. one agent doing everything
- **Where:** `uppgifter/del1.mdx` activity 4; `verifiering.mdx` ("oberoende av genereringen"); AGENTS.md "Write tests that check the requirements"
- **Type:** unclear
- **What I wondered / got stuck on:** `verifiering.mdx` says tests should be independent of the generation, but the AGENTS.md has the same agent write code and tests in one session; llm-bakgrund warns against exactly that. No instruction on *how* to get independence in practice (separate session? other agent? write tests first? student writes the expected values?). I wrote the tests from the requirement list after the code (the order was my choice, the code came first), so the independence was weak; in practice the test expectation error was in my own arithmetic.
- **What I did about it:** Wrote requirements first in the log, tests per requirement; flagged the weakness in AGENTS.md.
- **Suggested fix:** Recommend a concrete practice: tests from requirements in a fresh context/another agent, or student-written expected values.

### Q17. `del1.mdx` "Startrepo ... innehåller i huvudsak AGENTS.md och CLAUDE.md" and "Forka"
- **Where:** `del1.mdx`
- **Type:** other
- **What I wondered / got stuck on:** The page says fork the starter, but the starter has no CI, no license and no `.gitignore` for the chosen language. A hand-in fork keeps the starter's history; does the first commit need to be by hand? Minor. Also the starter AGENTS.md "Stakes for this part" and the part page are consistent (low stakes, no code review): no contradiction found there. `kunskap/examination.mdx` says part 1 has no code review, consistent with `del1.mdx`.
- **What I did about it:** none.
- **Suggested fix:** none needed beyond Q1/Q12.

## Verification record

Generated by the AI agent (me): `plantwater/core.py`, `plantwater/cli.py`, `tests/test_plantwater.py`, the AGENTS.md sections. Location: `/home/efo/git/aiap-teacher/student/aiap-part1-hobby` branch `part1`, commit "plantwater: CLI, tests, filled-in AGENTS.md".

| Step | What happened |
|------|---------------|
| First generation | Core + CLI written in one go (about 100 lines). |
| Tests written from requirements R1-R9 | First run: 6 passed, 2 failed, 1 error (see below). |
| Failure 1 (R6) | Real code gap: `[1, 2]` as data file crashed with TypeError traceback; entries missing keys would too. Fixed with load-time record validation. |
| Failure 2 (R9) | Real code gap: future dates accepted. Fixed with `check_not_future`. |
| Failure 3 (R2) | Test bug: wrong expected value (9 vs 10 days), code was right. Fixed test after hand-checking the date arithmetic. |
| After fixes | `python3 -m unittest discover -s tests -t .` gives 9 tests OK. |
| Manual run | add / due / water / invalid interval, in a temp dir; behaved as expected (exit 1 and `error:` on bad input). |
| Not verified | Real-world usefulness (validation step), Windows, Python versions other than 3.14 (an initial "3.9+" claim in AGENTS.md was an UNTESTED assumption, since removed; f-string `!r` etc. are fine, but `date.fromisoformat` accepts more formats on 3.11+ than on 3.9; e.g. "20260101" is valid on 3.11+, rejected on 3.9. The requirement says YYYY-MM-DD only; not tested.) |

Real verification catches: yes, two (both requirement gaps in first generation, found by automated tests) plus one wrong test. No hallucinated APIs. Test-run note: `python -m unittest discover -s tests` failed first with "Start directory is not importable" until an `__init__.py`/`-t .` was added: tooling friction an agent must know; nothing in the starter's AGENTS.md says how to run tests, which is expected but worth noting since `pytest` was not installed on the machine.

Simulated / not done: part 0 setup (all three agents, herdr, Tailscale), K8 second agent, K7 launch/deployment (plan only), K10 seminar (prep notes only), hand-in (committed locally on branch `part1`, nothing pushed), validation week of real use, AI cost measurement (estimate only).

## Things that worked well

- AGENTS.md "Instructions for AI agents" are short and effective: the agent ran tests itself, wrote tests per requirement, and flagged shared-misunderstanding risk (and in fact one occurred).
- The AGENTS.md section headings map well to K2-K7 and K9; filling the template top-down gave a natural order (requirements before tests).
- The pages for part 1 are consistent on stakes (low, no code review, seminar 4 hp) across `del1.mdx`, `examination.mdx` and AGENTS.md.
- "Challenge-based, no facit" framing plus guiding questions made project choice easy.
- The `CLAUDE.md` containing `@AGENTS.md` is a clean pattern and explained in harness.mdx.
