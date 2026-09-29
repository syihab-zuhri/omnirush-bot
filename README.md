# OmniRush Bot 🤖

GitHub bot powered by **OmniRush AI** (GPT-6 Astra) — automated code review, issue fixing, and Q&A via GitHub Actions.

## Features

### 1. 🔍 Auto PR Review
Every pull request gets reviewed automatically by OmniRush AI.

- Triggered on: PR opened, updated, reopened
- Checks: bugs, security, style, edge cases
- Posts review as a comment

### 2. 🔧 Issue Fix
Comment `/omnirush fix` on any issue and the bot will:

1. Analyze the issue
2. Find and fix the relevant code
3. Create a new branch and PR with the fix

**Usage:**
```
/omnirush fix
/omnirush fix please also add error handling
```

### 3. 💬 Q&A
Ask technical questions about the codebase.

**Usage:**
```
/omnirush ask how does the auth module work?
/omnirush ask what does the main function do?
```

Or add the `omnirush-qa` label to an issue.

## Setup

### 1. Fork or use as template

### 2. Add secrets
Go to **Settings → Secrets and variables → Actions** and add:

| Secret | Value |
|--------|-------|
| `OMNIRUSH_AUTH` | Contents of `~/.omnirush/auth.json` after `omnirush login` |

### 3. Done!
The bot works on this repo automatically. To use on other repos, copy the `.github/workflows/` files.

## Commands Reference

| Command | Where | What it does |
|---------|-------|-------------|
| `/omnirush fix` | Issue comment | Analyzes issue, fixes code, opens PR |
| `/omnirush ask <question>` | Issue comment | Answers technical questions |
| Auto | PR opened | Reviews code changes |

## How It Works

```
GitHub Event → GitHub Actions Runner → Install OmniRush CLI → Run omnirush -p → Post Result
```

The bot uses OmniRush's print mode (`-p`) for non-interactive automation. Auth is injected via repository secrets.

## Limits

- OmniRush free tier: weekly token grant (check with `omnirush whoami`)
- GitHub Actions: 2000 minutes/month free for public repos
- Review timeout: 15 min | Fix timeout: 20 min | Q&A timeout: 10 min

## License

MIT
