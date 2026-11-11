# Teacher TODO

Derived from the student runs of parts 1-3 (`student-run/part{1,2,3}-questions.md`, run 2026-11-11, local only, single AI agent as student). Items are grouped by theme and show which part(s) raised them. Full detail is in the logs.

## Blocking: TODO markers students will see
- Many `{/* TODO ... */}` markers live in pages students need (schedule, assessment criteria, seminar format, standards, reading, project limits, who pays). `QUESTIONS.md` is not visible to students, so either decide them or write "not decided yet" in the rendered text. (1, 2, 3)

## Verification material (`kunskap/verifiering`)
- Define what "higher requirements" means with a menu of test types and thresholds per part. (2)
- Explain and give a tiny worked example of: property-based testing, static analysis, mutation testing/hand mutation, model checking, hazard analysis, assurance cases. Recommend a toolbox per language. (2, 3)
- Define independence levels (same session, separate session, different vendor, human), what counts for G, and a hand-off recipe (spec only, tests committed before the code, tester must not read `src/`). Add a change-control rule: requirement changes go back to the independent test author. (1, 3)
- Say whether a wrong AI-written test or a requirement gap counts as a "found error" (K5). Reword part 3 K7 ("at least three catches") so it does not push students to invent findings: document all catches and argue if none. (1, 3)
- Audit policy for dev-only dependency advisories. (2)

## Assignment requirements
- Part 1: K7 vs challenge text ("lansera" vs "launch plan OK"); define what a launch is for non-web projects. K8: structure of the two-agent comparison (suggest one feature on two branches with a log table). (1)
- Part 2: define the maintainability test protocol (who picks the feature, what the agent may read, what counts as pass). Give deployment targets and a CI example. Review materials for K11: sample repo, checklist, number of reviews, deadline. (2)
- Part 3: review checklist and timing for K13; is failing K13 failing the part? Open-information boundary examples. Sources for DO-178C and economics. (3)
- Time budgets: part 0 is about 15 h alone; give hours per requirement and a weekly plan for each part. Project size guidance. (1, 2, 3)

## `AGENTS.md` in the starters
- Headings do not cover all requirements (K1, K8, K10 in part 1; K1, K11, K12 in part 2; K1, K13, K14 in part 3). Add sections or map requirements to headings explicitly. (1, 2, 3)
- It is both the short always-loaded agent file and the long assessed documentation; this contradicts the harness page ("keep it short"). Allow linked `docs/*.md` or state the trade-off. (1, 2)
- "Do not decide for the student, ask" stalls delegation and headless runs; add a fallback. "At the end of each session" is something an agent cannot detect, so say "right after the decision". (1, 2, 3)
- Add an "independent tester" paragraph (read only requirements and interface). (3)
- Language policy for deliverables (README is Swedish, AGENTS.md English). (1, 2, 3)
- `.gitignore` has no language entries (e.g. `__pycache__`); template HTML comments are left behind. (1, 3)

## Site pages
- `del2.mdx` lacks a link to the starter repo, seminars and examination. Check `del1.mdx` and `del3.mdx` too. (2)
- Setup page: Tailscale and herdr are required but unused in part 1; `curl | sh` installs conflict with the harness page's advice about untrusted input; install URLs are unverified. Who pays for the tools is undecided. (1, 2)
- How to estimate AI cost inside a session. (1)

## Decide
- Is it OK that K7-style "compare agents" needs all three paid tools? Set a minimum number of agents. (1, 2)
- Hand-in: fork visibility, issues enabled on forks (needed for review), submission route. (3)
