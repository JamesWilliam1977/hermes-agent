---
name: desktop-installer-and-bootstrap-evolution
description: Workflow command scaffold for desktop-installer-and-bootstrap-evolution in hermes-agent.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /desktop-installer-and-bootstrap-evolution

Use this workflow when working on **desktop-installer-and-bootstrap-evolution** in `hermes-agent`.

## Goal

Refactors or evolves the desktop install/bootstrap process, including installer scripts, first-launch flows, and runtime layout. Typically involves coordinated changes to Electron main/bootstrap scripts, install.ps1/install.sh, and documentation.

## Common Files

- `apps/desktop/electron/*.cjs`
- `apps/desktop/scripts/*.cjs`
- `apps/desktop/scripts/*.mjs`
- `apps/desktop/src/components/desktop-install-overlay.tsx`
- `scripts/install.ps1`
- `scripts/install.sh`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit Electron bootstrap scripts in apps/desktop/electron/
- Edit or add installer scripts (install.ps1, install.sh, or NSIS scripts)
- Update install overlays/components in apps/desktop/src/components/
- Update documentation in apps/desktop/README.md
- Update or add test scripts in apps/desktop/scripts/

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.