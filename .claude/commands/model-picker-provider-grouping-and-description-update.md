---
name: model-picker-provider-grouping-and-description-update
description: Workflow command scaffold for model-picker-provider-grouping-and-description-update in hermes-agent.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /model-picker-provider-grouping-and-description-update

Use this workflow when working on **model-picker-provider-grouping-and-description-update** in `hermes-agent`.

## Goal

Updates the grouping, description, or display logic for model providers in the model picker UI, affecting both CLI and GUI. Involves changes to models.py, main.py, and sometimes platform-specific files and tests.

## Common Files

- `hermes_cli/models.py`
- `hermes_cli/main.py`
- `gateway/platforms/telegram.py`
- `tests/hermes_cli/test_provider_groups.py`
- `plugins/model-providers/*/__init__.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit hermes_cli/models.py to update PROVIDER_GROUPS or provider descriptions
- Edit hermes_cli/main.py to change picker rendering logic
- Edit gateway/platforms/telegram.py if Telegram picker is affected
- Edit or add tests in tests/hermes_cli/
- Edit provider plugin __init__.py if provider-specific description changes

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.