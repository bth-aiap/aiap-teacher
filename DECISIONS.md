# Decisions

Decisions taken without asking, to review with the teacher. Reverse any of them freely.

1. **Repo names**: org `bth-aiap` (public). Site `bth-aiap.github.io` (user/org Pages site, so no `base`), starters `aiap-part1-hobby`, `aiap-part2-webapp`, `aiap-part3-critical` (English names as requested), teacher repo `aiap-teacher`.
2. **Site stack**: Astro + Starlight copied from the jsux site (same dependency versions, deploy workflow to GitHub Pages), Swedish only (`lang: sv`). No `astro-embed` and no `astro-hidden-prompt`.
3. **Site structure**: `index` (overview), `del0/` (index, setup, llm-bakgrund, harness), `del1`–`del3`, `kunskap/` (examination, seminarier, kodgranskning, verifiering, etik_och_hallbarhet). Named `del` rather than jsux's `kmom`, since the course is described in parts.
4. **Content depth**: pages are framework and framing only. Anything needing facts I don't have (tool install steps, assignment briefs, schedules, rubrics) is a `TODO` marker plus an entry in `QUESTIONS.md`. I did not invent tool details (e.g. herdr).
5. **Starter repos**: contain only `AGENTS.md`, `CLAUDE.md`, `README.md`, `.gitignore`. `AGENTS.md` is the source of truth; `CLAUDE.md` is just `@AGENTS.md` (import) so there is one file to maintain and no symlink problems on Windows.
6. **Agent instructions** are in English (agents read it well and the other course repos do so), README and site in Swedish. Each tells the agent to use AI fully and always to say how to verify, write requirement-based tests, state assumptions, and keep changes reviewable, plus a per-part "stakes" paragraph. Easy to translate if you want Swedish.
7. **No lint/CI/test tooling** in the starters, per "not much more than CLAUDE.md/AGENTS.md". Students choose their stack. The agent-policy and canvas-hand-in workflows from jsux were not copied.
8. **Credits** shown as 4 hp per seminar, +1 hp (del 2) and +2 hp (del 3) for code review, total 15 hp, per your confirmation.
9. **Student-run test skill** is *not* written yet; the course material has too many gaps to simulate a run. Next step once the questions are answered.
10. The teacher repo has `git init` and a `.gitignore` for the four sibling repos, no commits.

## Answered by the teacher (Q&A round)

11. Grading is pass/fail (G/U) for seminars and code reviews.
12. No course literature: website plus linked sources only.
13. Seminars are oral and in groups.
14. Code reviews: the teacher assigns reviewers; done on GitHub.
15. Hand-in is only via GitHub (the student's fork). No Canvas hand-in.
16. Tools in part 0: Claude Code, Codex, OpenCode (expected to change next year), herdr (https://herdr.dev/, an app for running coding agents), Tailscale (used mainly to show distributing agent execution across machines through herdr). Supported platforms: Linux, macOS, Windows via WSL. Who pays is undecided (school or students).
17. LLM and harness background in part 0 is technical.
18. Parts 1-3: a new project each part, chosen by the student. Part 3: student picks a system within defence, naval or aviation.
19. Starters contain nothing beyond instruction files, README and .gitignore.
20. Agent instruction files stay in English.
21. The student-run skill is written (`.claude/skills/student-run/SKILL.md`): test forks in `test-forks/` (gitignored) on the teacher's personal GitHub, logs in `student-run/`. Adapted from the jsux skill; never touches `bth-aiap/*` repos.
22. Sidebar-less splash front page, with the old front-page content condensed to cards.
23. Entrepreneurship is a thread through parts 1-3 (no new part or credits), examined inside the seminars. Meaning: building/launching a product and business case/economics (not intrapreneurship or legal/IP, which you did not select). Page `kunskap/entreprenorskap`, linked from parts 1-3, seminarier, front page. Per-part angles are my draft.
