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
