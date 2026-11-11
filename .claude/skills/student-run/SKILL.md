---
name: student-run
description: Work through an AIAP course part (part0-part3) as a capable student, using the course website content, and do the work in a test fork of the part's starter repo. Logs every question, gap or friction point. Use when the teacher asks to "student-run", "play student", or test-run a part, e.g. /student-run part1.
---

# Student run

Purpose: test the course material by doing it. Find unclear, missing, outdated or broken parts of a course part before the students do. Argument: `part0`, `part1`, `part2` or `part3`. If none is given, ask.

In this course students are *required* to use AI to the fullest, and the learning goal is to generate, verify, test and validate. So play the student the same way: use AI (yourself) heavily to produce the work, but then verify and validate it as the material demands, and log how well the material supports that.

## Hard rules

- Work only in a test fork under `student/` (gitignored, create it if missing). Never edit course material or starter repos (`bth-aiap.github.io/`, `aiap-part*/`) as a side effect: log the problem instead and let the teacher decide.
- Work **locally only**: `git clone ~/git/aiap-teacher/<starter> student/<starter>` and remove its `origin` remote (`git remote remove origin`). Never create GitHub repos or push anywhere; never push to `bth-aiap/*`.
- Do not open PRs or issues against `bth-aiap/*`. Code review simulation happens inside the test fork only.
- Do not delete or weaken the starter's `AGENTS.md` / `CLAUDE.md`; let them guide the work, as they will for students. Log if they were unclear or counterproductive.
- Commit often in the fork. In this repo, commit the question logs. Attribution lines from the session's system reminder apply.

## Persona: capable student

- The website content is the source of truth: `bth-aiap.github.io/src/content/docs/` (`del0/*`, `del1|2|3.mdx`, linked `kunskap/` pages). Follow the order the page suggests.
- General knowledge may fill gaps, but every gap is still logged (the point is finding where a student would be stuck).
- Part 0: follow the setup instructions as written as far as the sandbox allows; log anything unclear. Do not install paid or account-bound tools without asking the teacher.
- Things a student does with other people or the teacher (seminars, code review assignments, grading) cannot be fully done: simulate preparation (e.g. write the notes/reflection the student would bring, or a review of a sample repo) and mark it clearly as *simulated* in the log.
- Parts 1-3: a new project of the student's own choice per part. Pick one that fits that part's stakes level, and say in the log why you chose it and whether the page gave enough guidance to choose.
- Keep a short verification record while working (what you generated, how you verified, tested and validated it, what failed). This is both the student's seminar preparation and evidence of whether the material works.

## Workflow

1. Read the part's page(s) top to bottom and the starter's `AGENTS.md`. Note: setup, reading, project, verification expectations, seminar, code review, hand-in.
2. Create `student-run/<part>-questions.md` (format below) before starting work and update it as you go, not at the end.
3. Set up the test fork and a branch `<part>`.
4. Do the work in the order given, using AI as the course requires. Run whatever verification the starter or your own project defines before committing.
5. Real hand-in is via GitHub, but runs are local only: commit on the branch and log the hand-in step as *simulated*.
6. Finish with a summary to the teacher: what was done, the top questions, suggested course-material fixes. Then stop. Update `TEACHER_TODO.md` (create if missing) with items derived from the log.

If `gh` is not authenticated, ask the teacher to run `! gh auth login`.

## Question log format

File: `student-run/<part>-questions.md`. Commit after each batch of new entries.

```markdown
# <part> student run: questions and friction

Run date: YYYY-MM-DD

## Open questions

### Q1. <short title>
- **Where:** <page/section, with file path>
- **Type:** unclear | missing | contradiction | outdated | broken-link | tooling | too-much-work | agent-file | other
- **What I wondered / got stuck on:** ...
- **What I did about it:** <assumption made, or "blocked">
- **Suggested fix:** ...

## Verification record
<what was generated, how it was verified/tested/validated>

## Things that worked well
```

Log an entry every time anything makes you pause: ambiguous wording, an assumption, a missing link or file, conflicting requirements, an instruction that does not work as written, a TODO marker you hit, or an `AGENTS.md` instruction that made the agent behave badly. Do not silently resolve them. If a question blocks progress and only the teacher can answer, ask in the conversation too.
