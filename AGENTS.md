# Repository Guidelines

## Project Structure & Module Organization
This repository is a lightweight Codex/Claude skill package for Grok-backed web research.
- `scripts/grok_search.py`: main Python CLI entrypoint and request/response handling.
- `SKILL.md`: skill metadata and usage contract consumed by agent tooling.
- `install.ps1`, `configure.ps1`: Windows installation and interactive configuration scripts.
- `config.json`: default template config committed to the repo.
- `config.example.json`: example values for local setup.
- `README.md`: bilingual user-facing docs.

## Build, Test, and Development Commands
There is no formal build system; use direct script validation.
- `python scripts/grok_search.py --query "latest Node.js version"`: run the tool end-to-end.
- `python -m py_compile scripts/grok_search.py`: quick syntax check.
- `powershell -ExecutionPolicy Bypass -File .\install.ps1`: install skill files to `~/.codex/skills/grok-search` (Windows).
- `powershell -ExecutionPolicy Bypass -File .\configure.ps1`: write/update config interactively.

## Coding Style & Naming Conventions
- Python: 4-space indentation, snake_case for functions/variables, type hints for new logic.
- Keep helper functions private with leading `_` when module-internal (existing pattern in `grok_search.py`).
- PowerShell: use descriptive Verb-Noun function names (for example, `Resolve-GrokConfigPath`).
- JSON config keys should remain stable (`base_url`, `api_key`, `model`, `timeout_seconds`, `extra_body`, `extra_headers`).

## Testing Guidelines
No dedicated test framework is configured yet. For changes:
- Run `python -m py_compile scripts/grok_search.py`.
- Run one successful query path and one failure path (for example, missing `--api-key`) to verify error JSON behavior.
- If you add tests, place them under a new `tests/` directory and use `test_*.py` naming.

## Commit & Pull Request Guidelines
Recent history favors short, imperative commit subjects (English or Chinese), such as `Add grok-search Codex skill`.
- Keep subject lines concise and focused on one change.
- Reference config/security impacts explicitly in the body.
- PRs should include: purpose, key changes, validation commands run, and any README/SKILL updates.

## Security & Configuration Tips
- Never commit real API keys; keep secrets in local overrides (`config.local.json`) or environment variables.
- Treat `config.example.json` as non-sensitive sample data only.
