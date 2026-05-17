<!--
Copyright 2026 The Dapr Authors
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
    http://www.apache.org/licenses/LICENSE-2.0
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# Fix: Wrong Directory Paths in Examples (#583)

## Issue Description
Several documentation files referenced incorrect directory paths for example projects. Specifically:
- The agents-as-tools example was referenced as `examples/09-agents-as-tools` when the actual directory is `examples/08-agents-as-tools`
- The agents-as-activities-observability example had an incorrect project name

## Changes Made

### 1. **examples/08-agents-as-tools/README.md**
   - Fixed title from `# 09 — Agents as Tools` to `# 08 — Agents as Tools`
   - Updated in-process scenario command: `cd examples/09-agents-as-tools` → `cd examples/08-agents-as-tools`
   - Updated cross-app scenario command: `cd examples/09-agents-as-tools` → `cd examples/08-agents-as-tools`

### 2. **examples/08-agents-as-tools/pyproject.toml**
   - Fixed project name: `name = "09-agents-as-tools"` → `name = "08-agents-as-tools"`

### 3. **examples/07-agents-as-activities-observability/pyproject.toml**
   - Fixed project name: `name = "09-agents-as-activities-observability"` → `name = "07-agents-as-activities-observability"`

### 4. **pyproject.toml** (root)
   - Updated examples list reference: `"examples/09-agents-as-tools"` → `"examples/08-agents-as-tools"`

## Impact
- Documentation now correctly reflects the actual directory structure
- Users following the examples will use the correct file paths
- Project metadata is now consistent with the directory organization

## Testing
Before merging, please run:
```bash
uv run ruff format && uv run flake8 dapr_agents tests --ignore=E501,F401,W503,E203,E704 && uv run mypy --config-file mypy.ini && uv run pytest tests -m "not integration"
```

## Files Modified
- `examples/08-agents-as-tools/README.md` (3 lines changed)
- `examples/08-agents-as-tools/pyproject.toml` (1 line changed)
- `examples/07-agents-as-activities-observability/pyproject.toml` (1 line changed)
- `pyproject.toml` (1 line changed)

**Total: 4 files, 6 lines modified**
