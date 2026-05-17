---
note_type: durable-branch
area: deployments
updated: 2026-05-18
tags:
  - agent-knowledge
  - memory
  - deployments
update_when: >
  A new version is tagged and released; the CI matrix changes; the PyPI
  publication process changes; new release steps are added.
  Check `git tag --list` for the latest tag.
---

# 🚀 Deployments

Release, CI, and distribution strategy.

## 🏷️ Version

**0.4.12** (tagged `v0.4.12`). See [[packaging]].

## 🔁 CI Pipeline

[[testing|GitHub Actions]] (`.github/workflows/ci.yml`):
- Triggered on push/PR to `main`
- Matrix: `ubuntu-latest` + `macos-latest`, Python 3.10/3.12/3.13
- **test** job: pytest with editable install
- **build** job: wheel build + installed [[cli|CLI]] smoke test

## 📦 Distribution

- `pip install project-bedrock` (published to PyPI)
- Build: `python -m build` produces wheel and sdist
- Local dev: `pip install -e ".[dev]"` inside a venv (see [[gotchas]])

## 🚫 No Server Components

No Docker, no container deployment, no API server. See [[stack]].

## 🕓 Recent Changes

- 2026-05-18: Released v0.4.12 — active `bedrock/` vault cleanup, smaller tracked cockpit, and release/tag alignment restored after the untagged v0.4.8-v0.4.11 sequence.
- 2026-05-18: Released v0.4.11 — remaining `read_text()` calls updated to explicit UTF-8 handling.
- 2026-05-06: Released v0.4.10 — leftover test path fix for the `agent-knowledge/` → `bedrock/` vault rename.

## 🔗 See Also

- [[packaging]] -- build system details
- [[testing]] -- what CI runs
- [[stack]] -- runtime requirements
