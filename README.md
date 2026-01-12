# grok-search (Codex skill)

This repo is a Codex CLI skill that lets Codex run aggressive web research via your OpenAI-compatible Grok 2api endpoint.

## Install

Copy this folder to your Codex skills directory:

- `C:\Users\<you>\.codex\skills\grok-search\`

Or run:

```powershell
powershell -ExecutionPolicy Bypass -File .\install.ps1
```

## Configure

### Recommended: config file

Run once:

```powershell
powershell -ExecutionPolicy Bypass -File "$env:USERPROFILE\.codex\skills\grok-search\configure.ps1"
```

Default path: `C:\Users\<you>\.codex\skills\grok-search\config.json` (override with `--config` or `GROK_CONFIG_PATH`).

Write to user-level config instead (optional):

```powershell
powershell -ExecutionPolicy Bypass -File "$env:USERPROFILE\.codex\skills\grok-search\configure.ps1" -Global
```

### Alternative: env vars

```powershell
$env:GROK_BASE_URL="https://grok.lvli.de"
$env:GROK_API_KEY="YOUR_API_KEY"
$env:GROK_MODEL="grok-2-latest"
```

## Use

```bash
python scripts/grok_search.py --query "Search the web: latest stable version of <package> and release notes."
```
