<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/spidychoipro/spidychoipro/main/assets/logo-dark.svg">
    <img src="https://opencode.ai/opencode.svg" width="120" alt="opencode logo"/>
  </picture>
</p>

<h1 align="center">🕷️ opencode-config</h1>

<p align="center">
  <strong>Production-grade Opencode AI CLI configuration</strong><br>
  <em>bkit PDCA · NSP · Karpathy Guidelines · Custom agents · Cross-platform</em>
</p>

<p align="center">
  <a href="#-features"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Fspidychoipro%2Fopencode-config&query=%24.stargazers_count&style=flat-square&label=%E2%AD%90%20stars&color=yellow" alt="Stars"></a>
  <a href="https://github.com/spidychoipro/opencode-config/blob/main/README.md"><img src="https://img.shields.io/badge/platform-windows%20%7C%20macos%20%7C%20linux-2f81f7?style=flat-square" alt="Platform"></a>
  <a href="https://opencode.ai"><img src="https://img.shields.io/badge/opencode-1.0%2B-6c5ce7?style=flat-square" alt="opencode"></a>
  <a href="https://github.com/spidychoipro/opencode-config/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square" alt="License"></a>
  <a href="README.ko.md"><img src="https://img.shields.io/badge/lang-한국어-orange?style=flat-square" alt="Korean"></a>
</p>

<br>

## 📋 Table of Contents

- [Features](#-features)
- [Quick Start](#-quick-start)
- [What's Included](#-whats-included)
- [Usage](#-usage)
- [Custom Agents](#-custom-agents)
- [Skills Reference](#-skills-reference)
- [Project Structure](#-project-structure)
- [Customization](#-customization)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)

<br>

## ✨ Features

<table>
  <tr>
    <td width="50%">
      <h3>🧠 bkit PDCA + NSP</h3>
      <p>Document-driven development with Plan-Design-Do-Analyze-Report cycle. Every phase enforces Negative Space Programming to define what NOT to do.</p>
    </td>
    <td width="50%">
      <h3>🎯 Karpathy Guidelines</h3>
      <p>Surgical code changes, no unnecessary refactoring, minimal diffs, read-before-edit discipline. Smallest possible change for every task.</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>🤖 Custom Agents</h3>
      <p>Pre-configured <code>bkit-pdca</code> and <code>bkit-analyzer</code> subagents for automated workflow management and gap analysis.</p>
    </td>
    <td width="50%">
      <h3>🔒 Safety First</h3>
      <p>VibeGuard protection, permission rules, conflict resolution priority — explicit user request > safety > NSP > PDCA > Karpathy.</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>🖥️ Cross-Platform</h3>
      <p>Works identically on Windows, macOS, and Linux. No platform-specific hacks — all instructions are path-agnostic.</p>
    </td>
    <td width="50%">
      <h3>📦 10+ Built-in Skills</h3>
      <p>PDCA, code review, full-stack development, enterprise architecture, mobile apps, desktop apps, deployment, SEO, and more.</p>
    </td>
  </tr>
</table>

<br>

## 🚀 Quick Start

### 1. Install Opencode

Choose your platform:

<table>
  <tr>
    <th>Platform</th>
    <th>Command</th>
  </tr>
  <tr>
    <td><b>macOS</b></td>
    <td><code>brew install opencode</code></td>
  </tr>
  <tr>
    <td><b>Linux</b></td>
    <td><code>npm install -g @opencode/cli</code></td>
  </tr>
  <tr>
    <td><b>Windows</b></td>
    <td><code>winget install opencode</code> or <code>npm install -g @opencode/cli</code></td>
  </tr>
  <tr>
    <td><b>Any (npm)</b></td>
    <td><code>npm install -g @opencode/cli</code></td>
  </tr>
</table>

### 2. Clone this config

> **Note:** If you already have a config at `~/.config/opencode/opencode.jsonc`, back it up first.

<details>
<summary><b>macOS / Linux</b></summary>

```bash
# Clone directly to opencode config directory
git clone https://github.com/spidychoipro/opencode-config.git ~/.config/opencode

# Or keep it separate and symlink
git clone https://github.com/spidychoipro/opencode-config.git ~/opencode-config
ln -sf ~/opencode-config/opencode.jsonc ~/.config/opencode/opencode.jsonc
```
</details>

<details>
<summary><b>Windows (PowerShell 7+)</b></summary>

```powershell
# Clone to your home directory
git clone https://github.com/spidychoipro/opencode-config.git "$env:USERPROFILE\opencode-config"

# Copy the config file
Copy-Item -Path "$env:USERPROFILE\opencode-config\opencode.jsonc" -Destination "$env:USERPROFILE\.config\opencode\opencode.jsonc"
```
</details>

<details>
<summary><b>Windows (CMD)</b></summary>

```cmd
git clone https://github.com/spidychoipro/opencode-config.git %USERPROFILE%\opencode-config
copy %USERPROFILE%\opencode-config\opencode.jsonc %USERPROFILE%\.config\opencode\opencode.jsonc
```
</details>

### 3. Install plugins

```bash
cd ~/.config/opencode
npm install
```

This installs the required opencode plugins (notify, vibeguard, websearch-cited).

### 4. Verify

```bash
opencode --version
# You should see the opencode CLI version
```

That's it. All agents, skills, plugins, and workflows are configured.

<br>

## 📦 What's Included

### 🧭 Workflow System (PDCA + NSP)

| Phase | Description |
|-------|-------------|
| 📋 **Plan** | Create a plan document with NSP constraints |
| 🎨 **Design** | Design architecture with explicit boundaries |
| ⚡ **Do** | Implement with Karpathy surgical precision |
| 🔍 **Analyze** | Gap analysis against design + NSP compliance |
| 📝 **Report** | Completion report with match rate |

Every phase enforces **Negative Space Programming**: define what NOT to do, anti-patterns to avoid, tech NOT to use, out-of-scope items, boundaries, and deferred edge cases.

### 🛡️ Karpathy Coding Standards

| Rule | Description |
|------|-------------|
| 📖 Read first | Inspect existing code before making changes |
| 🏗️ Preserve architecture | Don't restructure unless explicitly told |
| ✂️ Minimal diff | Smallest possible change — no cleanup |
| 🔬 No guessing | Inspect APIs, never assume behavior |
| ❓ Clarify ambiguity | Ask before making irreversible decisions |
| 🎯 Stay focused | Only what was asked, nothing more |

<br>

## 🎮 Usage

```bash
# Start a PDCA session
opencode

# Then use PDCA commands inside the session:
# $pdca plan     — Create a plan document
# $pdca design   — Create a design document
# $pdca do       — Start implementation
# $pdca analyze  — Run gap analysis
# $pdca report   — Generate completion report

# Use skills directly:
# $skill bkit-rules   — Reference bkit detailed rules
# $skill code-review  — Run automated code review
```

<br>

## 🤖 Custom Agents

This config includes two pre-configured subagents:

### `bkit-pdca`
- **Mode:** Subagent
- **Role:** Full PDCA cycle manager
- **Capabilities:** Plan, design, implement, analyze, and report features
- **NSP enforcement:** Every phase includes Negative Space Programming

### `bkit-analyzer`
- **Mode:** Subagent (read-only)
- **Role:** Gap analysis specialist
- **Capabilities:** Compares design docs against implementation, detects NSP violations
- **Permission:** Edit access denied — analysis only

<br>

## 🧩 Skills Reference

| Skill | Purpose | Trigger |
|-------|---------|---------|
| `$pdca` | PDCA cycle management | `$pdca plan`, `$pdca analyze` |
| `$bkit-rules` | bkit detailed rules | `$bkit-rules` |
| `$bkit-templates` | PDCA document templates | `$bkit-templates` |
| `$code-review` | Code quality & security audit | `$code-review` |
| `$development-pipeline` | 9-phase dev pipeline | `$development-pipeline` |
| `$plan-plus` | Brainstorming-enhanced planning | `$plan-plus` |
| `$starter` | Static web development | `$starter` |
| `$dynamic` | Fullstack BaaS development | `$dynamic` |
| `$enterprise` | Enterprise microservices | `$enterprise` |
| `$desktop-app` | Electron/Tauri desktop apps | `$desktop-app` |
| `$mobile-app` | React Native/Flutter apps | `$mobile-app` |
| `$phase-*` | 9-phase pipeline skills | `$phase-1-schema` ... |

<br>

## 📁 Project Structure

```
~/.config/opencode/
├── opencode.jsonc          # Main configuration with inline instructions
├── vibeguard.config.json   # Security guard — secret scanning & masking
├── package.json            # Plugin dependencies (npm)
└── node_modules/           # Installed plugins (gitignored)
```

The configuration is self-contained in just three files. The `node_modules/` directory is gitignored — run `npm install` after cloning.

<br>

## 🎨 Customization

Edit `~/.config/opencode/opencode.jsonc` to:

- **Add plugins**: Modify the `"plugin"` array
- **Create new agents**: Add entries to the `"agent"` object
- **Change permissions**: Update the `"permission"` section
- **Modify instructions**: Edit the `"instructions"` array

After editing, restart opencode for changes to take effect.

<br>

## 🔧 Troubleshooting

| Problem | Solution |
|---------|----------|
| Config not loading | Verify the file is at the correct path for your OS |
| Agents not found | Check `"agent"` section in `opencode.jsonc` |
| Skills not working | Run `$skill code-review` as a test |
| Permission denied | Check `"permission"` section in config |

<br>

## 📄 License

MIT © [spidychoipro](https://github.com/spidychoipro)

---

<p align="center">
  <sub>Made with ❤️ and 🕷️ by <a href="https://github.com/spidychoipro">spidychoipro</a></sub>
</p>
