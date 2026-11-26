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

## Shell/alias Preferences
- **Do NOT add beginner-convenience aliases that the user would later delete as unnecessary**
  (e.g., overriding core commands like `cat`→`bat`, `vim`→`nvim`, etc.)
- Overriding a standard command is allowed only if it clearly stays useful long-term
  (e.g., `ls`→`eza`). When in doubt, don't add it; ask instead.

## Session End: Handoff
- Update AGENTS.md with completed/incomplete/blocked work state
- Push all commits
- If blocked, document the blocker and attempted solutions

### Current handoff (2026-11-22)
- Completed: portability (`76b654d`), doc alignment (`a50898e`), diagnose fix (`de8fb79`), free-form workspace policy + keybind inventory (`bfeb1b9`), and exact Dell media-key/gesture documentation (`9f55a4e`), and README personal-config disclaimer (`2163aed`) all committed and pushed on `agent/publish-hyprland-dotfiles`, then merged into `main` as `d6aa98a` so GitHub default branch shows the updated README. `diagnose.sh` reports 68 pass / 0 warn / 0 fail. User confirmed 한/영 key works. Decisions: no workspace role labels, no new window-switcher binds. No actual keybind/appearance/autostart changes.
- Also fixed swipe wrapping (`workspace_swipe_create_new=false`, `forever=true`) and 2% volume steps in `ee06f79`, merged to `main` as `599f7c7`. Dell Tech Guidebook Table 66 confirms Latitude 7390 has NO media track keys, so binds 56-59 are unreachable; documented in `docs/keybind-inventory.md`. `diagnose.sh` still 68 pass / 0 warn / 0 fail after commit.
- Trackpad 2-finger scroll does NOT switch workspaces: Hyprland 0.56.2 keybind manager only handles `WL_POINTER_AXIS_SOURCE_WHEEL` (physical mouse wheel). Verified in source (`src/managers/KeybindManager.cpp:459`) and by user test (mouse 1->2->1 works, trackpad 2-finger does nothing). A speculative `binds.scroll_event_delay` 300->100 change was made then reverted as irrelevant. Instead added `Super+Left`/`Super+Right` workspace cycle binds (60/61) in `65c6915`, merged to `main` as `7c998f2`; total 61 binds, diagnose 68 pass / 0 warn / 0 fail. Docs updated: trackpad limitation + new fallback in `README.md` and `docs/keybind-inventory.md`.
- Workflow audit 2026-11-23: verified live (gesture opts false/true, scroll_event_delay back to 300, 61 binds, no configerrors, diagnose 68/0/0; volume 10%->12%->10% via `swayosd-client --output-volume +/-2`; no workspace auto-placement rules; autostart is swayosd/hyprpaper/waybar/swaync/hypridle/cliphist/fcitx5, no Quickshell). Fixed stale README count 59->61 in `4805c61`, merged to `main` as `bfc5c51`. `~/HYPRLAND.md` updated in place with wheel/trackpad limitation, Super+arrow fallback, 2% volume, and dead media-key note (outside git).
- Workflow-doc gap analysis 2026-11-23 against `docs/workflow.md` §1-§7: actual config already matches all decisions (free ws 1-10, no auto-placement, Pavucontrol floating rule present, no grave/special/magic, ws animation speed 6, fadeLayersIn/Out off, blur size 3/passes 1, wallpaper symlink + `~/.cache/hypr-wallpaper-idx`, hyprlock path via symlink, no "Status word" block). Only the doc was stale; synced in `dbfffd2`, merged to `main` as `279456a` (68/0/0). Root cause of earlier user prompt: they wanted comparison against `docs/workflow.md`, not a generic audit — read that file first for workflow questions.
- Personal-workflow doc 2026-11-23: user wants workflow built for **the person talking now**, not generic `docs/workflow.md`. Created `docs/personal-workflow.md` (`36912d1`, main `9a009d5`). Asked 3 targeted questions; user confirmed: (1) opens many terminals in **ws 2** (my "starts with kitty" guess was wrong), (2) **Spotify shares the active workspace** (my guess right), (3) biggest gap is **sound/media control**. Doc updated with those facts.
- Media control fix 2026-11-23: `swayosd-client --playerctl` shows OSD and exits rc=0 with no player (plain `playerctl next` gives rc=1 + error). Added `Super+Shift+Left/Right/Space` = prev/next/play-pause (binds 62-64) in `c850885`, merged to main `3d85607`. Kept dead XF86Audio track binds 56-59 for external Dell keyboard/dock; total 64 binds, diagnose 68/0/0, configerrors clean. Docs + `~/HYPRLAND.md` updated.
- Media target decision 2026-11-23: user asked what player the media keys control. Verified from swayosd 0.3.2 source (`src/actions/mpris.rs`): with `playerctld` running (it is), `auto` uses playerctld's first player = most recently activated. So Spotify playback → Spotify, Brave YouTube → Brave. Kept `auto` (NOT `--player spotify`, which would block Brave). User accepted `Super+Shift+←/→` ergonomics as-is. Doc note in `a5db834`, main `6aeb9a2`.
- OpenCode plugin startup fix 2026-11-26: removed V1-only `opencode-notify`, `opencode-vibeguard`, `opencode-websearch-cited` from `opencode.jsonc` (latest npm versions still V1; OpenCode 2.4.2 requires a `Plugin.define` default export, so they failed on every launch and showed "3 plugins failed"). Preserved remote's file-based `instructions/*.md` and local Ollama provider/model config. Verified after `opencode service restart`: `opencode plugin list` = "No plugins found", `opencode plugin check` = "No package plugins found", zero new `failed to load plugin` log entries. Committed `28a31a5`, pushed.
- Incomplete: user to confirm `Super+Left/Right` wrap and new `Super+Shift+←/→/Space` + OSD with real keypresses; mark which of the 64 binds to keep/change/remove; real second-machine install still untested. If plugin features are wanted back, port the three packages to the V2 plugin API first. `~/QUICKSHELL.md` updated in place under `~` (outside git, not pushed).
- Blocked: none. `Super+Shift+Left/Right` still free if needed as another fallback.
