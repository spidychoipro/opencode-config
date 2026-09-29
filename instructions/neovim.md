# Neovim Config-Specific Rules

## Deprecated APIs = Bugs

When working on Neovim configuration (any `.lua` file under `lua/` or `init.lua`):

- **Deprecated functions/APIs** are treated as bugs. Replace with the documented successor.
- **Future-deprecated patterns**: APIs not yet deprecated but with a newer preferred alternative in latest Neovim stable should also be flagged and updated.
- **Version-gated removals**: Any API removed or changed in the latest Neovim stable that would break the config must be fixed.

Scope includes both the user's config AND third-party plugins managed by lazy.nvim.
Plugin-originated deprecation warnings are treated as bugs — fix by monkey-patching
the plugin in the plugin spec's `config` block (not by modifying plugin source directly).

Severity: 🔴 Critical = removed (crash), 🟡 Warning = deprecated (still works but warns), 🟢 Info = newer alternative exists.

## Post-Change Verification

After any modification to Neovim configuration:

1. Run `:checkhealth` in Neovim to verify the config loads without errors.
2. Fix immediately any problems reported by checkhealth — warnings and errors are both treated as bugs.
3. If checkhealth itself fails to load, investigate and fix the loading error first.

## Proactive Repo Management

The neovim-config repo (github.com/spidychoipro/neovim-config) is managed proactively.

- **Direct fix + commit + push** for small, clear changes (preferred for <50 lines).
- **PR** for larger changes or when review is beneficial.
- **Bug report** for issues that need tracking or are not immediately actionable.
- Choose the most effective action based on the situation — do not wait for user instructions on routine maintenance.
- Always verify after changes: `:checkhealth`, check for deprecated APIs, ensure WSL/Windows cross-platform compatibility.
- Keep both Windows (`C:\Users\<user>\AppData\Local\nvim\`) and WSL (`~/.config/nvim/`) in sync via git.
