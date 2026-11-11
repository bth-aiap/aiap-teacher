# part2 student run: questions and friction

Run date: 2026-11-11

Persona: capable student, played by Claude (Sonnet 5.5) in the sandbox. Fork: `student/aiap-part2-webapp`, branch `part2`, no remote.

## Open questions

### Q1. TODO markers visible to students on every page
- **Where:** `del0/harness.mdx`, `del0/llm-bakgrund.mdx`, `del0/setup.mdx`, `del2.mdx`, `uppgifter/del2.mdx`, `kunskap/verifiering.mdx`, `entreprenorskap.mdx`, `etik_och_hallbarhet.mdx`, `kodgranskning.mdx`
- **Type:** missing
- **What I wondered:** MDX comments `{/* TODO ... */}` are not rendered, but they show the material is a draft: no schedule/tidsplan, no grading criteria, no description of how deployment and code review are assessed (all are named in `uppgifter/del2.mdx` TODO), no reading material for ethics/entrepreneurship/verification depth.
- **What I did:** Proceeded using only what is written.
- **Suggested fix:** Resolve before release; the TODOs in uppgifter/del2 are exactly the things K1, K11 depend on.

### Q2. del2.mdx gives no link to the starter repo and no study-time estimate
- **Where:** `del2.mdx` ("Startrepo: Forka och klona startrepot för del 2.")
- **Type:** missing / broken-link
- **What I wondered:** Which repo? Only `uppgifter/del2.mdx` links `github.com/bth-aiap/aiap-part2-webapp`. del0 pages have `<p class="time">` hours; del2 has none, so no way to plan. Also "fork" is stated but the repo README says "Forka detta repo" (consistent), while the repo description says K-requirements are assessed via AGENTS.md (single file).
- **What I did:** Used the local starter.
- **Suggested fix:** Link the repo in del2.mdx; add hours per reading/assignment.

### Q3. Part 0 is not a prerequisite shown on part 2, and requires three paid, account-bound agents
- **Where:** `del0/setup.mdx`, `del2.mdx`, `uppgifter/del2.mdx` K7
- **Type:** tooling / unclear
- **What I wondered:** K7 requires "vad som skilde åt de agenter du provat". setup.mdx says "Det är ännu inte klart om skolan eller studenterna står för kostnaden." A student without all three subscriptions cannot meet K7 as written. I also may not install/run them in this run.
- **What I did:** Used the one agent I am (Claude Code-like harness) and marked the agent comparison as SIMULATED/impossible in AGENTS.md.
- **Suggested fix:** Decide on cost; say what to do if a tool is unavailable; state minimum number of agents for K7.

### Q4. AGENTS.md "do not decide for the student, ask" vs a student who wants the agent to run autonomously
- **Where:** `aiap-part2-webapp/AGENTS.md` "Keep this file up to date"
- **Type:** agent-file
- **What I wondered:** The agent is told to ask whenever project/stakes/requirements are unclear. In the starter all sections are empty, so a literal agent will stop and interview the student at once (reasonable, it matches the pedagogy), but a non-interactive run (CI agent, subagent) can only guess. Also "at the end of each session add to Decision log" is something agents routinely forget; nothing checks it.
- **What I did:** I acted as student and agent in one: chose project myself, recorded my choices as decisions.
- **Suggested fix:** Add a short "if you cannot ask (non-interactive), write assumptions as `ASSUMPTION:` lines and flag them". Consider a CI check that the headings are non-empty.

### Q5. AGENTS.md is both agent instructions and 10 long documentation sections; contradicts "keep short"
- **Where:** `del0/harness.mdx` ("håll dem korta, konkreta") vs `uppgifter/del2.mdx` ("Din AGENTS.md är din dokumentation och det vi bedömer utifrån")
- **Type:** contradiction
- **What I wondered:** The file is loaded into every session. Ethics, entrepreneurship, TCO and the full AI log are not useful to an agent adding a feature, and add context cost. Yet the assignment says AGENTS.md is the documentation assessed. My filled file became long (see Maintainability section).
- **What I did:** Put operational content (run/test/structure/conventions) first-ish, kept other sections compact, and linked to `docs/` was NOT done because assignment says AGENTS.md is the assessed doc.
- **Suggested fix:** Allow `docs/*.md` for the non-operational sections with AGENTS.md linking to them, or tell students to keep AGENTS.md operational and state that referenced files count.

### Q6. K1 deployment, K4 CI: no guidance, no starter workflow, cannot run in sandbox
- **Where:** `uppgifter/del2.mdx` K1, K4, activity 4
- **Type:** missing / tooling
- **What I wondered:** "driftsatt eller dokumenterad driftsättning" - where? Free hosting? Is GitHub Actions expected? Starter has no `.github/workflows` example, no lint/dependency-check suggestion beyond "lint, tester, beroendekontroll".
- **What I did:** Wrote `.github/workflows/ci.yml` (cannot run it here; validated YAML syntax and ran the same commands locally). Deployment documented only (Dockerfile + run instructions), SIMULATED, not deployed.
- **Suggested fix:** Provide a minimal CI example or say students write their own; list acceptable deployment targets and what is graded.

### Q7. "Vald nivå" / verification level is undefined
- **Where:** K3, `kunskap/verifiering.mdx` table ("Högre krav, med fokus på underhållbarhet")
- **Type:** unclear
- **What I wondered:** K3 asks for "vald nivå" but the only levels are the three part labels; "Högre krav" for part 2 is not defined (coverage %? which test types? SAST?). I could not tell what is "enough".
- **What I did:** Defined my own level (unit + HTTP integration tests per requirement, lint, npm audit, manual attack attempts) and justified it.
- **Suggested fix:** Give a concrete menu (test types, thresholds, checklist) per part.

### Q8. K7 "at least two cases where verification found errors" invites fabrication / is order-dependent
- **Where:** K7, AGENTS.md AI usage log
- **Type:** unclear
- **What I wondered:** If the agent writes correct code, there may be no two failures. Students will be tempted to invent or to plant bugs. I only logged ones that really occurred (see verification record); if fewer than two occur I would say so. Also no definition of a "case".
- **What I did:** Recorded only real catches; honest count in AGENTS.md.
- **Suggested fix:** Say explicitly that real catches are expected and reasonable to find with a deliberate review step (e.g. mutation testing or a second reviewer agent), and that "none found" must be argued.

### Q9. Project choice guidance: enough to choose, but not to size it
- **Where:** `del2.mdx` "Projekt", `uppgifter/del2.mdx` "Utmaningen"
- **Type:** unclear
- **What I wondered:** Examples (webshop, company site, internal system) were enough to pick something. I chose an internal equipment-loan desk because it has roles, state and a real security surface yet fits ~1 h. But nothing says how big a "medium stakes" project must be, or whether a trivially small one satisfies "realistic web application with real users or realistic scenario". K2 wants a customer: I had none (SIMULATED customer).
- **What I did:** Fictional customer, labelled as simulated in AGENTS.md.
- **Suggested fix:** State expected size (hours/features/roles), and whether a fictional customer is OK.

### Q10. Language of deliverable and of AGENTS.md
- **Where:** site is Swedish, `AGENTS.md`/starter instructions are English, README Swedish
- **Type:** unclear
- **What I wondered:** Should the filled-in sections be Swedish or English? The seminar/grader language? The agent prompts are English.
- **What I did:** English (matches the file and the agent).
- **Suggested fix:** Say which is accepted.

### Q11. Requirements K1-K12 map to sections only loosely
- **Where:** `uppgifter/del2.mdx` "AGENTS.md har rubriker som motsvarar kraven"
- **Type:** unclear
- **What I wondered:** K1 (app runs/deployed) and K2 (project) both land in "Project" (deployment is in the Project comment, not its own heading); K10/K11/K12 are partly not in AGENTS.md (K11 review, K12 seminar have no section). Where do I record the code reviews I wrote? Where do I put seminar preparation? "How to run, test and lint" is not named by any K but K1 needs it.
- **What I did:** Deployment in Project; reviews and seminar notes noted in this log only.
- **Suggested fix:** Add a mapping table K -> heading, and sections for Code review and Deployment.

### Q12. Verification-heavy AGENTS.md instruction "Point out where tests and code could share the same misunderstanding" works, but nothing says how to produce independent tests
- **Where:** `AGENTS.md` agent instructions, `kunskap/verifiering.mdx` ("tester som är oberoende av genereringen")
- **Type:** unclear
- **What I wondered:** The same agent wrote code and tests (the course itself, `llm-bakgrund` reflection Q3, warns about this). The material gives no technique. What helped in practice: writing tests from the numbered requirements first, mutation checks by hand (change one line, suite must fail), and re-reading tests asking "can this fail?". Three real test defects were found that way (see AI usage log in AGENTS.md).
- **What I did:** Used those techniques and recorded them.
- **Suggested fix:** Add 2-3 concrete techniques to `verifiering.mdx` (mutation by hand, requirement-first tests, a second agent as reviewer of the tests only, deliberately broken code).

### Q13. Hurried honesty pressure around K7 and the AGENTS.md "AI usage log" definition
- **Where:** K7; AGENTS.md "AI usage log"
- **Type:** unclear
- **What I wondered:** "Whenever generated code is found to be wrong ... add an entry" is good, but the agent that wrote the bug also writes the log entry. In my run all 5 serious catches came from me/the owner-role reviewing, not from the generating pass. The log entry is only as honest as the agent. Teacher cannot verify.
- **What I did:** Logged only real catches with how they were found.
- **Suggested fix:** Ask students to link a commit for each catch (the fixing commit), so entries are checkable.

### Q14. Time: this part is far more than an hour if everything required is done for real
- **Where:** `uppgifter/del2.mdx` whole page; no time estimate anywhere
- **Type:** too-much-work
- **What I wondered:** The app took little time; the 12 requirements are mostly writing (TCO, ethics, decision log, maintainability test, three agents, deployment, reviews, seminar). A student without hours stated cannot plan. AGENTS.md ended up about 200 lines.
- **What I did:** Kept answers short and concrete.
- **Suggested fix:** Give hours per K and a weekly plan (TODO already listed).

### Q15. K5 "dependency check" and eslint advisory: the starter's own recommended tooling produced an audit failure
- **Where:** `uppgifter/del2.mdx` activity 4 ("lint, tester, beroendekontroll"), K5
- **Type:** tooling
- **What I wondered:** `npm i -D eslint` (latest, Nov 2026) gives `npm audit` = 4 moderate (minimatch via eslint). A student who runs CI audit on all deps gets a red build from the start; is a red audit a failure of K5 or something to document? Not stated what severity threshold is acceptable.
- **What I did:** CI audits production deps only, advisory recorded as accepted risk in AGENTS.md.
- **Suggested fix:** State the policy (e.g. "fail on high/critical in production deps; document the rest").

### Q16. Sandbox/tooling limits (this run)
- **Type:** tooling
- Docker was installed but not usable (`permission denied ... docker.sock`), so the Dockerfile is unverified. GitHub Actions cannot run; the workflow YAML was only parsed and each command run locally. Real deployment, two other agents, real code review, seminar: impossible/simulated. The course does not say what a student should do if they lack docker permissions (Linux docker group) - part 0 setup doesn't mention docker at all although K1 deployment implies containers or hosting.
- **Suggested fix:** Add docker (or a hosting recommendation) to part 0 or to the part 2 page.

### Q17. Maintainability test (K6): worked, but it checks only what the activity says; findings
- **Where:** `uppgifter/del2.mdx` activity 5 and K6
- **Type:** unclear / other
- **What happened:** I spawned a real fresh sub-agent (Agent tool, general-purpose, clean context) with only the repo copy and AGENTS.md, task "Overdue page". It succeeded in ~30 s, 16/16 tests. It reported 7 gaps (time zone/"today", overdue boundary, GET route placement, how to create overdue test data, hard-coded test count going stale, dangling reference to a not-yet-written result section, scope-list ambiguity); I fixed AGENTS.md accordingly (see its Maintainability section). Honest limits: same model family as author (same blind spots), it read source files when AGENTS.md was silent (which the assignment permits? unclear: "bara din dokumentation"), feature was easy, no mutation/server run by it.
- **Wondered:** "ge en ny agentsession bara din dokumentation" - does the agent get the code too? It must (to edit). Is it only AGENTS.md as instruction? Which feature size counts? How many rounds? What if it succeeds immediately (is that a pass, with nothing to report)?
- **Suggested fix:** Define the protocol (agent gets repo + AGENTS.md only, feature chosen by a classmate/teacher, not the author, ~1 round, record gaps). Author-chosen features are biased.

### Q18. K11 code review: no sample repo exists; simulated review below
- **Where:** K11, `kunskap/kodgranskning.mdx`; `student/aiap-part1-hobby` only contains the starter files (no student attempt)
- **Type:** missing
- **What I wondered:** No number of repos, no review checklist, no template, no deadline, no definition of what is graded (review or reviewed code). Also "på GitHub" so it cannot be done locally.
- **What I did:** **SIMULATED.** I reviewed my own part2 repo as an outsider (sample), listing findings I would post as issues:
  1. (medium) `fails` Map in `src/auth.js` grows without bound for random usernames and is never pruned: memory-exhaustion DoS with unauthenticated requests. Same for expired sessions never accessed.
  2. (medium) Login POST has no CSRF/origin protection (login CSRF); AGENTS.md does not list it as accepted.
  3. (low) "today" uses UTC, near midnight local time lending checks are off by a day; documented only after the maintainability test.
  4. (low) Lock-out is per username, so anyone can lock a known user out; accepted in AGENTS.md (good), but no alert/log is emitted on lockout.
  5. (low) No test for 404 on unknown paths/methods, nor for `X-Content-Type-Options` etc. beyond CSP.
  6. (low) AGENTS.md claims "attacks tried" mostly via the author's own tests, so not independent; the claim "sessions fixation not applicable" is reasoned, not tested.
  7. (info) Dockerfile never built; CI never run; deployment simulated, so K1/K4 evidence is partly absent. A reviewer on GitHub could not verify green CI anyway.
  Reviewing was easier with the requirements table and test names in AGENTS.md; harder because the doc is long and several claims ("reviewed", "mutation-checked") are not linkable to commits (see Q13).
- **Suggested fix:** Provide review checklist/template and number of reviews; require author to list verification evidence links.

### Q19. K12 seminar: prepared notes (SIMULATED, not delivered)
- **Where:** K12, `kunskap/seminarier.mdx` (not linked from del2/uppgift but exists)
- **Type:** missing
- **What I wondered:** `kunskap/seminarier.mdx` and `examination.mdx` exist but del2.mdx does not link them in "Läsa" (only verifiering/entreprenorskap/etik). I only found them by listing the directory (the task did not list them); seminarier.mdx lists what to be able to show, but group size, length and criteria are TODO. Link them from the part page.
- **Notes I would bring:** decisions (stdlib-only; role model; audit scoping); verification: 16 tests plus 14 hand mutations (2 first-time survivors, 1 equivalent/invalid mutant discarded); maintainability: 7 gaps found by fresh agent; economics: ~3-year TCO about 200 USD, buy (Snipe-IT) if scope grows; ethics: tokens estimate, responsibility, GDPR for borrower names. Difference between proven and assumed: proven = R1-R10 by tests on this code path with in-memory DB; assumed = reverse proxy/TLS, Docker image, GitHub CI, real users, UTC vs local time, token/energy figures.

## Verification record
- **Generated:** app (~400 lines, Node built-ins only), 16 requirement-named HTTP tests, CI YAML, Dockerfile, AGENTS.md sections, review.
- **Verified:** `npm test` 16/16 (first run 13/13 passed on the first try, which was itself suspicious); `npm run lint` clean after fixing `fetch` global; `npm run audit:prod` 0 vulns; `npm audit` (dev) 4 moderate; YAML parsed; real server started and curl-tested (login 303, cookie flags, headers, home page with admin form).
- **Hand mutation testing** (one-line breakage, suite must fail): killed: CSRF check removed, admin check removed, lock threshold 5->6, due-today boundary, max range removed, 30->31 days, HttpOnly removed, SameSite changed, logout no-op, unknown-user message differs, esc() removed. Survived first time: dummy-hash guard (added test). Two of my first mutations were invalid (no-op replacements); reported honestly.
- **Real defects found in generated work:** vacuous test setup (missing `.run()`), vacuous logout test, untested dummy-hash guard, Docker bind address, missing session expiry, ESLint globals, dev audit advisories. All found by review/mutation, none by the first test run.
- **Not verified:** GitHub Actions run, Docker build, deployment, browser rendering, agents comparison, real code review, seminar.

## Things that worked well
- AGENTS.md headings map to K2-K10 and the agent preamble ("say how it can be verified", "point out shared misunderstanding", "do not decide for the student") produced useful behaviour: requirement-first tests, an explicit accepted-risk list, decision log entries.
- The challenge framing (prove it, not just build it) pushed me into mutation checks and a threat table; that is the right learning outcome.
- The fresh-agent maintainability test is cheap and found 7 real documentation gaps in 30 seconds. Keep it.
- The starter being nearly empty leaves free tech choice; Node built-ins worked offline except `npm install eslint`.
