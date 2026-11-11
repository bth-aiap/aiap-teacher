# Open questions

Each matches a `TODO` marker in the site or starter repos.

## Course
1. Course code, institution (BTH?), name in Ladok, and the exact run dates per part (1 Sept to mid-January)?
2. Grading scale (A–F, U/G, or pass/fail?) and criteria for seminars and code reviews. Are seminars graded individually?
3. Is 15 hp total correct for the Ladok registration, and how are the moments split in Ladok?
4. Is there a literature list (like Designing Interfaces in jsux)?

## Seminars and code review
5. Seminar format: oral or written, individual or group, length, what must students prepare/hand in?
6. Code review: how are pairs assigned, how many reviews per student, what is assessed (the review or the reviewed code), what platform (GitHub PRs?)?
7. Where is student work handed in (GitHub, Canvas)? jsux used a Canvas hand-in workflow; I did not copy it.

## Part 0
8. Which tools exactly, and what is "herdr"? What do students need to pay for or get licences for (Claude Code, codex, ...)? Are API keys or subscriptions provided?
9. Platforms to support (Linux/macOS/Windows/WSL)? tailscale: for what purpose in the course?
10. How deep should the LLM and harness background go, and is there a preferred reading list?

## Parts 1–3
11. Concrete assignments for each part: what do students build? Single project or several? Same project evolved or new each part?
12. Part 3: which concrete domain/scenario (defence, naval, aircraft)? Standards to reference (DO-178C, etc.)? Is there any security/clearance concern with the topic or student projects?
13. Starter repos: should they hold anything besides instruction files (e.g. a requirements template, a verification-log template, a CI skeleton)? Which stack, if any, do you want to prescribe in part 3?
14. Which AI tools/models are students expected to use per part, and who pays for them?

## Ethics and sustainability
15. Reading material and sources for parts 2 and 3? Is the BTH five-perspectives sustainability framing used as in jsux?

## Infrastructure
16. GitHub org and repo names, and the site URL (`site` in `astro.config.mjs` is a placeholder)? Should starters be GitHub template repos?
17. Language of agent files: English now, Swedish OK?

## Tooling
18. Should I write the student-run test skill now (needs answers to 11 first)?
