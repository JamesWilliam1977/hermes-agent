```markdown
# hermes-agent Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute effectively to the `hermes-agent` codebase, a TypeScript project with a focus on desktop application development (React/Electron), CLI tooling, Dockerization, and robust documentation. You'll learn the project's coding conventions, commit patterns, and the main workflows for adding features, evolving installers, updating model picker logic, refreshing documentation, and hardening Docker containers.

## Coding Conventions

- **File Naming:**  
  Use `kebab-case` for file names.  
  _Example:_  
  ```
  model-picker-provider.ts
  desktop-install-overlay.tsx
  ```

- **Import Style:**  
  Use alias imports for modules.  
  _Example:_  
  ```typescript
  import { fetchModels } from '@/services/model-service';
  ```

- **Export Style:**  
  Use named exports.  
  _Example:_  
  ```typescript
  export function startAgent() { ... }
  export const AGENT_VERSION = '1.0.0';
  ```

- **Commit Messages:**  
  Follow [Conventional Commits](https://www.conventionalcommits.org/):  
  - Prefixes: `fix`, `feat`, `chore`, `docs`
  - Example:  
    ```
    feat: add grouping for model providers in picker UI
    fix: correct UID/GID mapping in Docker bootstrap script
    ```

## Workflows

### Desktop Feature Development and Polish
**Trigger:** When adding a new feature, polishing UI, or fixing bugs in the desktop app  
**Command:** `/desktop-feature`

1. Edit or add React component(s) in `apps/desktop/src/app/` or `apps/desktop/src/components/`
2. Update supporting store logic in `apps/desktop/src/store/` or `apps/desktop/src/hooks/`
3. Modify Electron main process or preload scripts in `apps/desktop/electron/`
4. Update or add related scripts in `apps/desktop/scripts/`
5. Update or add tests in `apps/desktop/src/app/` or `apps/desktop/src/components/`
6. Update `apps/desktop/README.md` if user-facing behaviour changes
7. Update `package.json` or other config files if dependencies or build steps change

_Example:_  
```typescript
// apps/desktop/src/components/model-picker.tsx
export function ModelPicker() {
  // ...component logic
}
```

### Desktop Installer and Bootstrap Evolution
**Trigger:** When changing how the desktop app is installed or bootstrapped  
**Command:** `/desktop-installer`

1. Edit Electron bootstrap scripts in `apps/desktop/electron/`
2. Edit or add installer scripts (`install.ps1`, `install.sh`, or NSIS scripts)
3. Update install overlays/components in `apps/desktop/src/components/`
4. Update documentation in `apps/desktop/README.md`
5. Update or add test scripts in `apps/desktop/scripts/`
6. Update build/config files as needed

_Example:_  
```bash
# scripts/install.sh
echo "Installing Hermes Desktop dependencies..."
```

### Model Picker Provider Grouping and Description Update
**Trigger:** When changing how model providers are grouped or described in the picker UI  
**Command:** `/model-picker-update`

1. Edit `hermes_cli/models.py` to update `PROVIDER_GROUPS` or provider descriptions
2. Edit `hermes_cli/main.py` to change picker rendering logic
3. Edit `gateway/platforms/telegram.py` if Telegram picker is affected
4. Edit or add tests in `tests/hermes_cli/`
5. Edit provider plugin `__init__.py` if provider-specific description changes

_Example:_  
```python
# hermes_cli/models.py
PROVIDER_GROUPS = {
    "OpenAI": ["gpt-3.5", "gpt-4"],
    "Claude": ["claude-v1", "claude-v2"]
}
```

### Documentation Refresh or Cross-Platform Doc Update
**Trigger:** When updating documentation for new platform support, install instructions, or removing outdated warnings  
**Command:** `/docs-refresh`

1. Edit `README.md`
2. Edit docs in `website/docs/` (may include EN and zh-Hans)
3. Edit `i18n/zh-Hans/` files for translated docs
4. Update cross-links and anchors as needed

_Example:_  
```markdown
## Windows Native Support
Hermes Agent now supports Windows natively. See [installation instructions](./docs/windows.md).
```

### Docker Bootstrap and Permission Hardening
**Trigger:** When fixing or hardening Docker container startup, user mapping, or volume permissions  
**Command:** `/docker-bootstrap`

1. Edit `docker/stage2-hook.sh` to adjust UID/GID logic or `chown` behaviour
2. Edit `hermes_cli/container_boot.py` for Python-side container boot logic
3. Edit or add tests in `tests/hermes_cli/test_container_boot.py`

_Example:_  
```bash
# docker/stage2-hook.sh
chown -R $APP_UID:$APP_GID /data
```

## Testing Patterns

- **Framework:** [Vitest](https://vitest.dev/)
- **Test File Pattern:** `*.test.ts` (or `*.test.tsx` for React components)
- **Location:** Tests are typically colocated with source files.

_Example:_  
```typescript
// apps/desktop/src/components/model-picker.test.tsx
import { describe, it, expect } from 'vitest';
import { ModelPicker } from './model-picker';

describe('ModelPicker', () => {
  it('renders provider groups', () => {
    // ...test logic
  });
});
```

## Commands

| Command              | Purpose                                                        |
|----------------------|----------------------------------------------------------------|
| /desktop-feature     | Start a desktop feature, UI/UX, or bugfix workflow            |
| /desktop-installer   | Evolve installer/bootstrap scripts and flows                   |
| /model-picker-update | Update model provider grouping/description in picker UI        |
| /docs-refresh        | Refresh documentation or update cross-platform docs            |
| /docker-bootstrap    | Harden Docker bootstrap, UID/GID, or permissions              |
```
