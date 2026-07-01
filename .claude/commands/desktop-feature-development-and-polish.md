---
name: desktop-feature-development-and-polish
description: Workflow command scaffold for desktop-feature-development-and-polish in hermes-agent.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /desktop-feature-development-and-polish

Use this workflow when working on **desktop-feature-development-and-polish** in `hermes-agent`.

## Goal

Implements new features, UI/UX improvements, and bugfixes for the Hermes desktop app. This workflow often involves coordinated changes across React components, Electron main process, store logic, and supporting scripts, frequently with test and README updates.

## Common Files

- `apps/desktop/src/app/**/*.tsx`
- `apps/desktop/src/components/**/*.tsx`
- `apps/desktop/src/store/**/*.ts`
- `apps/desktop/src/hooks/**/*.ts`
- `apps/desktop/electron/*.cjs`
- `apps/desktop/scripts/*.cjs`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add React component(s) in apps/desktop/src/app/ or apps/desktop/src/components/
- Update supporting store logic in apps/desktop/src/store/ or hooks/
- Modify Electron main process or preload scripts in apps/desktop/electron/
- Update or add related scripts in apps/desktop/scripts/
- Update or add tests in apps/desktop/src/app/ or apps/desktop/src/components/

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.