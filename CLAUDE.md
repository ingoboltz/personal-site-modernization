# CLAUDE.md — Project Rules

## Branch Rules
- ALL work for this project lives on the `claude-rebuild` branch — never work from `main`
- At the start of every session, before doing anything else, run: `git fetch origin && git checkout claude-rebuild && git pull origin claude-rebuild`
- Always verify you are on `claude-rebuild` and fully up to date before making any changes or running any scripts
- Never commit to `main`

## Script Execution Rules
- When running Python or bash scripts to modify files, always target the main repo directory directly, NOT the Claude worktree path
- The worktree path (`.claude/worktrees/...`) will NOT have the latest changes from `claude-rebuild` — always use the actual repo root
- Before running any bulk script, verify the target files exist at the expected path and show the expected content
