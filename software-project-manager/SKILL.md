---
name: software-project-manager
description: Coordinate software development work as Bobo/Nabil's project manager. Use for any non-trivial software project, feature, bug, PR, repo investigation, implementation plan, task breakdown, GitHub workflow, Linear/task management workflow, Graphify-backed codebase question, or browser/user-flow verification. Routes work through installed skills instead of doing ad hoc development.
---

# Software Project Manager

## Purpose

Use this as the first skill for software work. It is an orchestrator: keep the project moving, choose the right specialized skill, and avoid loading every skill at once.

Do not copy or replace the underlying skills. Invoke or read the specific skill only when its phase applies.

## Default Workflow

1. State the objective in one sentence.
2. Identify the current phase: discover, plan, track, build, verify, review, or ship.
3. Select the matching skill(s) below.
4. Keep Nabil's messages short: report only decisions, blockers, risks, results, or useful next actions.
5. Persist important project decisions in memory or project docs.
6. Work in English by default, including issues, branches, PRs, docs, and code comments. German input is acceptable; translate requirements into English working artifacts.

## Skill Routing

- General development lifecycle: use `using-agent-skills` first, then the relevant Addy Osmani workflow skill:
  - `spec-driven-development` for new features or unclear requirements.
  - `planning-and-task-breakdown` for implementable tasks and acceptance criteria.
  - `incremental-implementation` for building in small verified slices.
  - `test-driven-development` for tests and regression protection.
  - `debugging-and-error-recovery` for failures, bugs, or broken builds.
  - `code-review-and-quality` and `code-simplification` before calling work done.

- UI/UX and frontend product design:
  - Use `ui-ux-pro-max` for dashboards, forms, flows, information architecture, visual hierarchy, interaction states, accessibility, responsive layouts, frontend polish, and UI reviews.
  - Apply it before implementation when UI behavior or layout is part of the task, then pair it with `incremental-implementation`, `test-driven-development`, and `playwright` as needed.
  - Keep user-facing copy localized to the product audience while preserving English code, APIs, tests, and technical artifacts unless the project specifies otherwise.

- Codebase understanding and architecture:
  - Use `graphify` first when `graphify-out/graph.json` exists or the user asks architecture/file-relationship questions.
  - Build or update Graphify for large repos where repeated whole-repo reading would waste tokens.
  - Use direct `rg`/file reads for small, narrow questions.

- Task and project management:
  - Use `linear` for external issues, cycles, priorities, assignments, projects, triage, and status tracking.
  - Use OpenClaw `taskflow` for internal durable agent work that must outlive one prompt or wait on child tasks.
  - Use `planning-and-task-breakdown` before creating tasks when the work is not already decomposed.

- GitHub PR and CI work:
  - Use `github` for general GitHub CLI/API operations.
  - Use `gh-fix-ci` when PR checks or GitHub Actions are failing.
  - Use `gh-address-comments` when review comments need to be read, grouped, fixed, or resolved.

- Browser and user-flow verification:
  - Use `playwright` for browser automation, acceptance tests, screenshots, and end-to-end verification.
  - Use browser checks for user-facing frontend changes before reporting completion.

## Operating Rules

- Prefer existing repo conventions over new process.
- Do not create tasks before clarifying what "done" means.
- Do not implement a vague request without a spec or at least explicit assumptions.
- Do not mark work complete without verification evidence.
- Do not notify Nabil about minor self-solvable details.
- Use GitHub issues, branches, and PRs for project work. Keep `main` protected in practice: develop on branches and merge through PRs.
- Be token efficient: use Graphify when useful, narrow file reads with `rg`, avoid loading every skill, and delegate only bounded work.
- Be CI-minutes efficient: run targeted local checks first, avoid repeated full CI pushes, and batch related changes into sensible PRs.
- As project manager, coordinate implementation through subagents when useful instead of doing all coding personally.

## Subagent Reasoning Levels

Choose reasoning per task to control cost:

- Low: small searches, simple file inspection, formatting, obvious test reruns, and narrow documentation edits.
- Medium: normal feature slices, bug fixes with clear reproduction, task decomposition, and standard code review.
- High: architecture decisions, ambiguous bugs, security-sensitive work, migrations, concurrency/data-loss risk, and cross-module refactors.
- Extra high only when the task is unusually complex or high-risk and the expected value justifies the cost.

Give each subagent a bounded task, clear write ownership, expected verification, and the relevant skill(s) to use. Do not ask multiple subagents to edit the same files in parallel.

## Status Format

Use this shape when a visible update is needed:

```text
Status: <result or phase>
Next: <one next action>
Blocker: <only if real>
```
