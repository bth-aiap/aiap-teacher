# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Role

This folder is the workspace for the **teacher** of AIAP (AI accelerated programming), a new three-part course. It is modelled on the sibling workspace `~/git/jsux-teacher` (read its `CLAUDE.md` for the conventions this one borrows). Act as a teaching assistant: draft, restructure and polish course content, assignment specs and starter repos. Do not act as a student writing code for submission, except inside the test skill described below.

## Status

The workspace was empty when this file was written. The layout below is the agreed plan, not a description of existing code. Once the repos are cloned or created, replace the placeholders with real names, remotes and build/lint/test commands, and keep each sub-repo's own `CLAUDE.md` as the home for detailed commands.

Still to be filled in: see `QUESTIONS.md`. Decisions made without asking are in `DECISIONS.md`; read both first.

A first draft of the website and starters exists (`bth-aiap.github.io/`, `aiap-part1-hobby/`, `aiap-part2-webapp/`, `aiap-part3-critical/`, local git repos, no remotes). Detailed commands are in `bth-aiap.github.io/CLAUDE.md`; the starters have none by design.

## The three parts

The parts are an escalation in **how much is at stake**, and so in the security demands and in the verification, testing and validation that AI-generated code needs. Each part has a seminar on that trade-off.

0. **Part 0: setup and background (no credits)**: developer setup (terminal, Claude Code, opencode, codex, tailscale, herdr, etc.), background on LLMs, and the agent harness. It has no seminar and no credits. It is course-website material only, with no starter repo.
1. **Hobby projects**: low-stakes personal projects. Discussion of what level of security and verification is enough at this level. Seminar only, **no code review**.
2. **"Ordinary" web applications**: e.g. a webshop company site or a non-critical internal application. Same security and verification discussion, with a bigger focus on **maintainability**. Includes **ethical and sustainability implications**.
3. **Mission-critical software**: software critical to society, preferably in the domain of defence, naval craft or aircraft. Highest demands on verification and validation. Includes **ethical and sustainability implications**.

**Entrepreneurship** is a thread through parts 1–3, not a separate part and with no extra credits; it is examined as part of the seminars. Focus: building and launching a product, and business case and economics. Angle per part: 1 idea to launch, 2 business model and economics (build vs buy, total cost of ownership), 3 the cost of reliability.

The code-review assignments (parts 2 and 3) are scheduled inside the third of the semester where they fit, not as a separate block at the end.

## Course philosophy

- **AI use is required, and pushed as far as it goes.** This is the opposite of jsux: there is no anti-agent CI check, no hidden-prompt component and no "AI as tutor, not code generator" policy. Never add or copy those mechanisms from jsux.
- The main learning goal is that students **generate, verify, test and validate** code with AI. Course material should emphasise the verification and validation steps, not just generation.
- **Size and schedule**: a full-semester course of three 4 ECTS seminars plus the code-review credits below, running from about 1 September to mid-January. The credited parts (1–3) run in sequence, so each takes roughly a third of the semester, with part 0 as a short setup lead-in (exact dates not yet set).
- **Credits**: each part is a 4 ECTS seminar moment. The credits are given in conjunction with the seminar plus code-review assignments, which are worth 1 ECTS in part 2 and 2 ECTS in part 3. Part 1 has no code review. Part 0 carries no credits. The code-review ECTS are **on top of** the seminar's 4, so part 2 is 4 + 1 and part 3 is 4 + 2. (Implied total: 15 ECTS, not 12. This is derived, not stated by the teacher, so confirm it before writing Ladok mappings or grading text.)
- **Examination** is by three seminars (one per part) and code reviews of other students' code. There is no points-to-grade rubric or Canvas hand-in CI carried over from jsux unless the teacher asks for it.

## Planned layout

This folder is a git repo for teacher notes only (`CLAUDE.md`, TODO files, notes, test-run logs, `.claude/skills/`). The repos below are independent clones that are **gitignored here**. `cd` into the relevant one before running its commands.

- **Course website**: Astro + Starlight, with all content in **Swedish** under `src/content/docs/`. It is the same stack as `~/git/dbwebb-jsux.github.io`, so its structure and workflows are a good reference. The sidebar order in `astro.config.mjs` is the source of truth for part and moment ordering.
- **Three student starter repos**, one per course part. They are **independent**: each is forked separately by students, and part 2 does not build on the finished state of part 1, nor part 3 on part 2. The starters are deliberately minimal: essentially a `CLAUDE.md` / `AGENTS.md` and little else, with no prescribed framework, linting or CI, because students generate the code themselves. Keep the agent instruction files student-facing and encouraging of AI use.
- **Test fork(s)**: the teacher's own forks of the starters, used only by the test skill. Gitignored, not course material; don't edit them outside test-run sessions.

## Working across the repos

Course pages on the website describe work students do inside the starter repos. When editing a page or assignment spec, check that the files and instructions it references still match the corresponding starter (especially its `CLAUDE.md` / `AGENTS.md`), and the reverse when changing a starter.

## Course-testing skill

A project skill (in `.claude/skills/`, not yet written) simulates a **student run**, as `student-run` does in jsux-teacher: act as a student in a test fork, follow the published course material step by step using AI heavily as the course demands, and log every question, ambiguity and friction point to a per-part file (for example `student-run/partNN-questions.md`). A `TEACHER_TODO.md` is derived from those logs. The skill should only read course material and write to the test fork and the logs, never fix the course content as a side effect.
