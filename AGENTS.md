# OpenCode Session Rules

## Pre-Session: On Start
1. **Read `opencode.jsonc`** — project-level rules take priority over AGENTS.md
2. **Load relevant skills** (e.g., `$code-review`, `$pdca`) when task matches
3. **Check git status** — if repo exists with origin, commit/push expected

## During Work: Do-Validate Loop
1. **Define success criteria** before making any change (what and how to verify)
2. **Surgical changes only** — smallest possible diff, no scope creep
3. **Surface assumptions** — note any assumption that could silently fail (e.g., "this function runs at config load time")

## After Every Change: Verify → Commit → Push
1. **Verify it works** — not just "no error", but confirm the intended effect:
   - `:checkhealth` for Neovim config changes
   - `--dry-run` or test commands for scripts
   - Print/log the actual value that changed
2. **Fix problems immediately** — checkhealth warnings/errors = bugs
3. **Audit deprecated APIs** — check if changed code uses any API deprecated in latest stable
4. **Commit** with descriptive message
5. **Push** if origin exists — never leave unpushed commits at session end

## Commit Discipline
- Check `git status` + `git diff` before staging
- Never commit secrets, config tokens, or personal paths
- One logical change per commit

## Session End: Handoff
- Update AGENTS.md with completed/incomplete/blocked work state
- Push all commits
- If blocked, document the blocker and attempted solutions
