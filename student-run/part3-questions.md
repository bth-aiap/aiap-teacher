# part3 student run: questions and friction

Run date: 2026-11-11

Run by: one Claude agent (Sonnet 5.5) as "student", plus one fresh subagent used as the independent test author (see K6). Hand-in, code review, seminar are simulated or impossible and marked so.

## Open questions

### Q1. Page says "see QUESTIONS.md" in many TODO markers; students cannot see it
- **Where:** `del3.mdx` (2 TODOs), `uppgifter/del3.mdx` (1), `kunskap/verifiering.mdx`, `kunskap/kodgranskning.mdx`, `kunskap/seminarier.mdx`, `kunskap/examination.mdx`, `kunskap/entreprenorskap.mdx`, `kunskap/etik_och_hallbarhet.mdx`, `del0/*` (3). All are JSX comments `{/* TODO ... */}`.
- **Type:** other
- **What I wondered / got stuck on:** The markers are invisible in the rendered site but present in source, and refer to a QUESTIONS.md that is not in the student-facing repos. If a student (or their agent) reads the .mdx source, it sees unresolved TODOs for exactly the things the student needs: standards to reference, limits on project content, schedule, assessment criteria.
- **What I did about it:** Treated them as "undecided by the teacher", logged the consequences below (Q2-Q6).
- **Suggested fix:** Resolve before course start, or ensure the rendered text states plainly "not decided yet" where a student is affected.

### Q2. No standards or guidance for what the project may contain (TODO hit)
- **Where:** `del3.mdx` "Projekt" TODO; `uppgifter/del3.mdx` bottom TODO.
- **Type:** missing
- **What I wondered:** Which standards to reference (only DO-178C is named, as "inspiration")? What counts as "öppen information"? E.g. may I use real COLREG rule numbers, real IMO/ICAO values, public AIS formats? May the system be a real weapon-related function (dual use)? Is a fictional "naval" function using public formulas (CPA/TCPA is textbook) fine?
- **What I did about it:** Chose a collision-avoidance advisory core using textbook CPA/TCPA geometry and invented thresholds, explicitly advisory-only, no weapon function. Wrote the open-information claim myself.
- **Suggested fix:** Give a short allowed/not-allowed list, and 3-4 example projects with suggested size. Mention a lightweight standard-inspired structure (e.g. DO-178C objectives, IEC 61508 SIL idea, IEC 61162/NMEA for sea) as optional reading with links.

### Q3. Project size/time budget not stated for part 3
- **Where:** `del3.mdx`, `uppgifter/del3.mdx`
- **Type:** missing / too-much-work
- **What I wondered:** Part 0 and the reading pages give hours (e.g. "5 studietimmar") but part 3 gives no study hours, no timeline ("veckoplanering" TODO) and no expected size of the "kärna". K1-K14 are 14 requirements incl. 10 documentation sections; how big should the code be? A student could spend 5 hours or 150 on this.
- **What I did about it:** Scoped to roughly 150 lines of code and a similar amount of tests, aimed at "defensible, with honest gaps" rather than big.
- **Suggested fix:** State expected hours and a size guide ("a few hundred lines of core is enough; depth of argument matters more than size").

### Q4. "Reading" list is thin for the highest stakes part (TODO hit)
- **Where:** `kunskap/verifiering.mdx` ("fördjupning och konkreta exempel/tekniker per nivå" TODO), `kunskap/etik_och_hallbarhet.mdx`, `kunskap/entreprenorskap.mdx`.
- **Type:** missing
- **What I wondered:** The assignment demands "egenskapsbaserade tester, statisk analys, modellkontroll", "assurance-argument", "oberoende", but `verifiering.mdx` explains none of them (about 25 lines in total). A student with no background has no definition of an assurance case (claims-argument-evidence, GSN), property-based testing, hazard analysis (FMEA, FHA, STPA), or independence. I used general knowledge.
- **What I did about it:** Used general knowledge (claims/evidence/gaps structure; FMEA-ish table; property tests; exhaustive grid check; mutation testing).
- **Suggested fix:** Add per-level concrete technique list with a tiny worked example for each (hazard table template, assurance claim example, how to do property tests in the student's language).

### Q5. Tooling for verification is not specified; sandbox had no pytest/hypothesis
- **Where:** `uppgifter/del3.mdx` ("till exempel egenskapsbaserade tester, statisk analys, modellkontroll"); starter AGENTS.md "How to run, test and lint" is empty.
- **Type:** tooling
- **What I wondered:** Which tools may/should I use and install? Course says nothing about language or toolchain, and the starter has no language scaffolding (no .gitignore for build artefacts, no test runner). In my environment only Python 3.14 stdlib and gcc existed (no pytest, hypothesis, mypy, ruff, cppcheck).
- **What I did about it:** Stdlib only: `unittest`, a hand-written seeded random property tester, exhaustive grid enumeration as bounded model check, `python -X dev -W error`, an AST-based static check script, and a hand-made mutation-testing script.
- **Suggested fix:** Offer a per-language recommended toolbox (Python: pytest+hypothesis+mypy+ruff; C: cppcheck, frama-c; Rust: kani/proptest; ...) and state that students install these (and that the sandbox may not allow it). Add Python/other `.gitignore` guidance, or tell the agent to add one.

### Q6. Who decides things the AGENTS.md says the agent must not decide? (agent-file)
- **Where:** starter `AGENTS.md`, "Do not decide for the student ... ask the student, propose options".
- **Type:** agent-file
- **What I wondered:** I am simultaneously the agent and the student. The instruction to ask the student about project, stakes level, requirements and verification level means an agent in a headless/autonomous run has nobody to ask. For real students, it is a good rule, but the AGENTS.md gives no fallback ("if the student is not available, propose and mark as 'proposed, not confirmed'").
- **What I did about it:** Recorded the choices as the student's decisions (the teacher's task text told me to pick), and flagged in the Decision log that they were made by the agent on the student's behalf in a simulated run.
- **Suggested fix:** Add a fallback rule, and a marker convention such as "[proposed by agent, not yet confirmed by student]".




### Q7. Starter AGENTS.md: spec extraction bug by me (not course material) but shows independence workflow cost
- **Where:** K6, `uppgifter/del3.mdx` activity 5 ("låt en annan agent ... skriva testerna utifrån kraven").
- **Type:** other
- **What happened:** I handed the independent test-writing subagent a spec extracted from AGENTS.md; my extraction missed the Requirements section. The subagent correctly refused to guess and asked for the requirements. Fixed and resent.
- **Note for the teacher:** a concrete recipe for "independent test session" (what to hand over, what not to, how to prevent the agent from reading the code, that it should refuse on missing info) is missing. Students will likely just open a second chat in the same repo where the agent sees the code; the page does not warn that this is weak independence. Suggested fix: add a short recipe (separate worktree without src/, or a separate branch; give only requirements + interface; tests committed before the implementation).

### Q8. Starter .gitignore has no entries for generated artefacts; AGENTS.md has no language guidance
- **Where:** starter `.gitignore` (only `node_modules/ .env .DS_Store`)
- **Type:** tooling
- **What I did:** appended `__pycache__/` and `*.pyc` in my fork.
- **Suggested fix:** Mention in AGENTS.md "set up the toolchain, .gitignore and the How-to-run section in the first session".

### Q9. Section order in AGENTS.md vs. requirements K1-K14 vs. assignment text
- **Where:** starter AGENTS.md headings; `uppgifter/del3.mdx` K-list
- **Type:** unclear
- **What I wondered:** K3 says requirements go under "Requirements" and traceability under "Verification plan". But the AGENTS.md has "Stakes and risk assessment" AND "Hazards and failure modes", which overlap heavily (both ask what can go wrong). K1/K13/K14 have no heading (K1 in "How to run"?). Where does K6 independence go? (Verification plan comment says so; K6 itself does not name a heading.) Also the "Stakes" heading name ("Stakes for this part") is fixed text, while "Stakes and risk assessment" is student text.
- **What I did:** Stakes and risk = verification level chosen and accepted risks, Hazards = the table.
- **Suggested fix:** State in each K item which heading, and say how Stakes/risk and Hazards differ.

### Q10. Order of sections in AGENTS.md doesn't match the work order
- **Where:** starter AGENTS.md
- **Type:** unclear
- **What I wondered:** Activities say: requirements, then risk analysis, then plan verification before generating. The file has Verification plan before Hazards. Hazard analysis should drive requirements (R3, R4 here come from hazards), so I did hazards first in practice and had to backfill.
- **Suggested fix:** Reorder headings or note the iteration.

### Q11. K7 "minst tre fall där verifieringen hittade fel" can be unmet or fabricated for a small, easy project
- **Where:** `uppgifter/del3.mdx` K7; starter AGENTS.md AI usage log comment.
- **Type:** unclear / other
- **What I wondered:** On a deliberately small, well-specified core the generated code passed 126 of 127 independent tests on the first run, and the one failure was a wrong test expectation. Strictly, "verification found errors in generated code" happened for me only 2 times (both found by my own probing, not by the planned tests) plus 3 test/process catches. The requirement pushes students to hunt for findings or (worse) invent them. The task here also said not to fabricate.
- **What I did about it:** Logged 5 real catches and classified them honestly (2 code/requirement defects, 2 test/process, 1 test gap), and stated that the code passing the independent suite is weak evidence.
- **Suggested fix:** Reword K7 to "document every case where review/verification found an error, including in tests, requirements or process, and explain what you did to look for errors if none were found". Suggest exploratory probing and mutation testing as ways to look.

### Q12. K6 independence: what counts, and what can one student actually do?
- **Where:** `uppgifter/del3.mdx` K6 and activity 5.
- **Type:** unclear
- **What I did:** a fresh subagent got only the spec and wrote tests; it also wrote its own throwaway stub implementation (not asked for, but it raised the quality of the tests: it caught its own bad expectation). Same model family as the code author, and the spec author is the code author. I reported this as limited independence.
- **What I wondered:** Is "another agent session" enough for G? Is a different vendor (Codex vs Claude) expected, given the course makes students install all three? The page does not say how strong independence has to be or whether independent *requirements review* counts.
- **Suggested fix:** define levels (same session / separate session / separate model vendor / human) and say what is required for G in part 3; show the hand-off recipe (see Q7).

### Q13. Requirement changes after independent tests exist: what is the rule?
- **Where:** K6 vs K12/AGENTS.md "Keep this file up to date"
- **Type:** missing
- **What happened:** exploratory probing found overflow-to-"safe" with extreme configs, I tightened R8 (added caps), which invalidated two independent tests. I edited them myself (marked EDITED) which weakens independence. Nothing in the materials says how to do that properly (re-run the tester session with the changed spec?).
- **Suggested fix:** Add a sentence on change control: a requirement change goes back to the independent author.

### Q14. AGENTS.md "ask the student" rule collides with autonomous subagent workflow
- **Where:** starter AGENTS.md ("Do not decide for the student")
- **Type:** agent-file
- **What happened:** The independent test-writing session loads no AGENTS.md rules (separate dir) but if a student runs it in the repo it would read AGENTS.md and the implementation, defeating independence. The agent-file has no instruction like "when acting as the independent tester, do not read src/". 
- **Suggested fix:** Add an "independent tester role" paragraph to AGENTS.md: read only Requirements and Interface; refuse to read `src/`.

### Q15. Assignment is large: 10 documentation sections + code + tests + review + seminar
- **Where:** `uppgifter/del3.mdx`
- **Type:** too-much-work
- **What I did:** about 2-3 hours of agent time for a ~140-line core and ~1500 lines of tests/tools/docs. AGENTS.md ended up ~200 lines with a lot of prose which the grader must read. Docs duplicated: Stakes/risk vs Hazards (Q9), Security vs Hazards, Verification plan vs Assurance argument vs AI usage log (verification evidence appears three times).
- **Suggested fix:** merge or give explicit page-length guidance; provide a template with required tables (hazard table, traceability table, claim-evidence-gap table). Say K1 has no heading.

### Q16. Mixed languages and unspecified words
- **Where:** pages are Swedish; AGENTS.md and starter are English; K-items refer to AGENTS.md headings in English ("Project", "Requirements") from Swedish text. Student writes AGENTS.md in which language? Unstated.
- **Type:** unclear
- **What I did:** English (agent-facing). Suggested fix: state language policy for AGENTS.md (the teacher assesses it).

### Q17. Requirements "Requirements R1" in AGENTS.md comment says "e.g. R1, R2" while K3 says "identifierare" - fine. But "K13/K14" are not repository content; K1 has no heading
- **Where:** K1, K13, K14
- **Type:** unclear
- **What I did:** K1 documented in "How to run"; K13/K14 simulated (below). Suggested fix: a "Coursework status" heading, or say that K13/K14 are assessed elsewhere.

### Q18. K13 code review of assigned repos on GitHub: impossible in this run (SIMULATED/IMPOSSIBLE)
- **Where:** K13, `kunskap/kodgranskning.mdx`
- **Type:** missing
- **What I did:** Did not do the review, no assigned repos exist, no GitHub. Simulated preparation: I made my own repo reviewable (AGENTS.md, `./verify.sh`, traceability table). I did NOT review a sample repo (task said to simulate; I judged reviewing my own work meaningless).
- **Gaps in material:** `kodgranskning.mdx` has no checklist, number of reviews, timing, or how to give feedback (comments vs issues vs PRs in the other fork: needs write access to others' forks? The page says "comments on code, issues or PRs in the reviewed fork", but forks may have issues disabled by default!). Also the review in part 3 cannot be a *safety* review without a rubric: what to look for (traceability gaps, tests that mirror code, claims without evidence).
- **Suggested fix:** Add a review checklist drawn from K1-K12, a worked example of a review comment, and mention that fork issues must be enabled.

### Q19. K14 seminar: simulated preparation (SIMULATED)
- **Where:** K14, `kunskap/seminarier.mdx`, `uppgifter/del3.mdx` "Reflektion"
- **Type:** missing
- **Notes the student would bring (simulated):**
  1. Generated vs decided: the agent wrote spec, code, tools; I (as student) would decide thresholds and scope. Open question to the group: is "the agent proposed, the student approved" meaningful decision-making?
  2. Verification: independent suite + oracle + properties + mutation; the code passed first time, found defects were by exploration; honest gap list in Assurance argument (C3, C6, H8-H12, common-mode).
  3. Risk accepted: invented thresholds, no real-world validation.
  4. Value/cost: verification ~5x code size; a certified supplier sells evidence.
  5. Reflection question: would I let it be used for real? No (see AGENTS.md).
- **Gaps in material:** seminar form, group size, length, grading criteria are all TODOs; nothing says whether to bring the AGENTS.md, slides or just discuss; "oral and in groups" but K14 says each student must be able to defend own assurance argument: how, in a group?
- **Suggested fix:** state format and what to bring.

### Q20. Hand-in (SIMULATED)
- **Where:** `kunskap/examination.mdx` ("Allt arbete lämnas in via GitHub ... fork")
- **Type:** missing
- **What I did:** commits on local branch `part3` in `student/aiap-part3-critical`, no remote. Not pushed.
- **Gaps:** how is the fork submitted (URL on Canvas? Not Canvas, says the page; then where)? Which branch (main)? Deadline? Is the fork private (it contains safety analysis) or public (the teacher/reviewers must see it)? Reviewers are other students: a private fork needs invitations. Also "Forka" does not say whether the fork may be renamed or must remain a fork (GitHub: one fork per account per repo, but part 3 repo is separate, fine).

### Q21. "Öppen information": no guidance on what to do if a student's chosen domain has export-control or dual-use concerns
- **Where:** `uppgifter/del3.mdx` Aside "Öppen information", Etik section
- **Type:** missing
- **What I wondered:** CPA/TCPA geometry is also used in fire-control/intercept. I chose to say so in Ethics and stay in a defensive scope. A student working on e.g. a missile guidance filter would be in a grey zone; the page just says "open sources and own assumptions".
- **Suggested fix:** give an example of a boundary and say who to ask (the teacher) before starting. Note that publishing in a (possibly public) GitHub fork is an act of release.

### Q22. K9 "Security" vs a pure-function core: little to say; wording "leveranskedjan för AI-genererad kod"
- **Where:** K9
- **Type:** unclear
- **What I did:** covered input spoofing, config tampering, prompt injection, no dependencies; flagged that the supply chain for AI-generated code consists of the model/harness itself, which I cannot audit. The materials give no example of what an acceptable treatment is (SBOM? lockfiles? provenance statements?).

### Q23. K11 Economy: no numbers or sources available
- **Where:** K11, `kunskap/entreprenorskap.mdx`
- **Type:** missing
- **What I did:** gave illustrative, unresearched figures and labelled them as such. The page offers no data on certification cost (e.g. DO-178C DAL costs) or sources; I used general knowledge only (not verified), which is exactly what the course warns about.
- **Suggested fix:** supply 2-3 citable sources, or relax K11 to qualitative reasoning.

### Q24. Contradiction/mismatch check between pages
- `uppgifter/del3.mdx` says "Alla krav ska vara uppfyllda för godkänt" and K13 (2 hp code review) is graded separately per `examination.mdx` (seminarium 4 hp and kodgranskning 2 hp, each G/U). So K13/K14 appear in a single K-list, but are different examination moments: unclear if failing K13 fails the whole part or only the 2 hp.
- `del3.mdx` says "Startrepo: Forka och klona" while the student-run rules (and a student without a GitHub account) need local clone; fine for real students.
- `del0/setup.mdx` says all three agents should be installed and "compared" and `harness.mdx` says "Under kursen kommer du att prova alla tre", but the part 3 page/AGENTS.md has no requirement to use more than one: the "differences between agents" in the AI usage log comment is the only place. Is using all three mandatory in part 3?
- `del0/setup.mdx` says installation commands were fetched "i november 2026"; harness TODO says details unverified against docs (TODO hit).
- Dates: `examination.mdx` says reviews happen "inom den tredjedel av terminen där respektive del ligger" but part 3 has no dates anywhere.
- **Type:** contradiction / missing

### Q25. Reading list for part 3 is only 3 pages with TODO-level content; "DO-178C" named but no link
- **Where:** `del3.mdx` "Läsa", `uppgifter/del3.mdx` activity 8
- **Type:** missing / broken-link (no link)
- **What I did:** from memory: DO-178C (objectives, independence, traceability), STPA/FMEA (hazard tables), assurance cases (claims-arguments-evidence). No source read, so labelled as general knowledge.
- **Suggested fix:** link a public summary (e.g. FAA/EASA overviews, GSN community standard, NASA assurance-case pages) and a short glossary of "assurance case", "independence", "hazard", "property-based test", "mutation testing".

### Q26. Starter file layout: nothing prescribes where code/tests go
- **Where:** starter README/AGENTS.md
- **Type:** unclear
- **What I did:** `src/`, `tests/`, `tools/`, `verify.sh`. The starter says "almost empty on purpose". Fine, but the "How to run" section is the only place the grader learns how to run it: the teacher assessing 100 forks needs a uniform entry point. Suggest requiring a single command (e.g. `./verify.sh`) as K1 evidence.

### Q27. The AGENTS.md instruction file as work document: placeholder HTML comments
- **Where:** starter AGENTS.md
- **Type:** agent-file
- **What happened:** The `<!-- Student: ... -->` comments contain the actual instructions for each section (e.g. the verification plan comment contains the K5/K6 requirements). When filling the sections I kept the comments below my text; unclear whether students should delete them. The agent mostly obeyed them well. Also the "Stakes for this part" and "Instructions" are long; the agent did not hold back (good) but "Do not hold back" conflicts a bit with "Keep changes small" (not a real problem).

## Verification record

- **Project:** `cpa_core`, a fictional ship-to-ship CPA/TCPA collision-alert decision core (Python 3.14 stdlib), 140 lines. Chosen because: small, pure, numerically hazardous, naval; the page gave only examples ("flygkontrollsystem, kollisionsundvikande till sjöss"), which was just enough to choose, but nothing on size (Q3) or dual-use limits (Q21).
- **Generated (by me as the AI):** requirements R1-R10 and interface, implementation, `tools/static_check.py`, `tools/mutate.py`, `verify.sh`, regression tests, all AGENTS.md sections. A separate fresh subagent generated `tests/test_requirements.py` (127 tests, 1229 lines) from the spec only.
- **Verification run (all via `./verify.sh`, passes, ~22 s):** py_compile, AST static check, 131 unittest tests with `-X dev -W error` (explicit failure cases, ~22k-case grid vs independent oracle, seeded random/property tests for symmetry and invariance), mutation testing: 32/33 mutants killed + 1 reasoned equivalent.
- **What failed / was found:** (1) first spec hand-off to the tester was incomplete (my bug, caught by the tester); (2) tester's own wrong expectation for the 45-degree scenario (TCPA 707 s < 720 s caution), caught when it ran against its own stub; (3) `Config(10**400)` raised OverflowError not ValueError (real defect, missed by the independent suite, found by my probing); (4) overflow to inf made far-apart ships "CPA_SAFE" under an extreme config: fixed by caps in R8; (5) mutation testing showed 4 mutants (overflow, two caps, internal-error-as-safe) survive the independent suite; killed by my own non-independent regression and fault-injection tests.
- **Not verified:** see AGENTS.md Assurance argument (H8-H12, real-world validation, common-mode between same-model agents).
- **Tools not available:** pytest, hypothesis, mypy, ruff, cppcheck; stdlib substitutes used and described (Q5).
- **Not done or simulated:** Codex/OpenCode not used (not allowed to launch other agents/harnesses), no human review (agent review stands in; K7 formally unmet in a real sense), K13 and K14 simulated/impossible, hand-in simulated.
- **Time/effort:** roughly 2.5 hours of agent time, ~40% of it on documentation. Waiting for the test-writing subagent took about 10 minutes (it was slow; a student would wait similarly).

## Things that worked well

- The starter AGENTS.md produced the right behaviour: the agent stated assumptions, wrote tests from requirements rather than code, kept changes small, and recorded decisions/AI-log entries. The "ask, do not decide" rule made the role split visible (Q6 aside).
- The K1-K14 list is concrete and each maps to a section; the "Vägledande aktiviteter" order (requirements, hazards, plan verification before generating) is a good workflow, and "låt en annan agent skriva testerna utifrån kraven" is actionable and genuinely paid off: an independent session refused to proceed on an incomplete spec and caught its own errors.
- The assignment's emphasis on "what you have NOT proven" produced a more honest assurance argument than a coverage number would.
- Mutation testing as a way to evaluate the independent tests is not in the course but is cheap and informative; worth mentioning in `verifiering.mdx`.
