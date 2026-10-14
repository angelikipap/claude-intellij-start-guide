# Claude Code + IntelliJ IDEA: a developer's getting-started guide

A step-by-step tutorial for developers who want to start using [Claude Code](https://code.claude.com/docs) as an AI pair programmer inside **IntelliJ IDEA** (the same steps work for PyCharm, WebStorm, GoLand, PhpStorm and Android Studio).

By the end you will have:

- Claude Code installed and logged in
- The Claude Code plugin connected to IntelliJ (diffs in the IDE diff viewer, selection sharing, IDE diagnostics)
- A `CLAUDE.md` that teaches Claude your project's conventions
- A set of everyday workflows: understand code, fix bugs, write tests, refactor, commit
- Your own reusable skills and agents, and a way to share them with your team

## Steps

| # | Step | Time |
|---|------|------|
| 1 | [Install Claude Code](01-install.md) | 5 min |
| 2 | [Connect IntelliJ](02-intellij-plugin.md) | 5 min |
| 3 | [Your first session](03-first-session.md) | 15 min |
| 4 | [Teach Claude your project with CLAUDE.md](04-claude-md.md) | 10 min |
| 5 | [Everyday workflows](05-workflows.md) | 20 min |
| 6 | [Customize: permissions, skills, agents, MCP](06-customize.md) | 20 min |
| 7 | [Tips and troubleshooting](07-troubleshooting.md) | reference |

## Prerequisites

- IntelliJ IDEA (Community or Ultimate), recent version
- A paid Claude plan (Pro, Max, Team or Enterprise) or a Claude Console account. The free claude.ai plan does not include Claude Code.
- macOS 13+, Windows 10 1809+, or Linux (Ubuntu 20.04+, Debian 10+)
- Git (on Windows, [Git for Windows](https://git-scm.com/downloads/win) is recommended)

## Cheat sheet

| Action | Mac | Windows / Linux |
|---|---|---|
| Open Claude Code from the editor | `Cmd+Esc` | `Ctrl+Esc` |
| Insert a file reference (`@File.java#L10-20`) | `Cmd+Option+K` | `Alt+Ctrl+K` |
| Cycle permission modes (normal / accept edits / plan) | `Shift+Tab` | `Shift+Tab` |
| Interrupt Claude | `Esc` | `Esc` |

| Command | What it does |
|---|---|
| `/init` | Generate a `CLAUDE.md` for the project |
| `/ide` | Connect a terminal session to IntelliJ |
| `/config` | Settings (e.g. diff tool) |
| `/clear` | Start a fresh conversation |
| `/compact` | Summarize the conversation to free up context |
| `/model` | Switch model |
| `/permissions` | View and edit allowed / denied tools |
| `/agents` | Create and manage subagents |
| `claude -c` | Continue the last conversation |
| `claude --resume` | Pick an older conversation to resume |

## Official documentation

- Claude Code docs: https://code.claude.com/docs
- JetBrains integration: https://code.claude.com/docs/en/jetbrains
- JetBrains plugin: https://plugins.jetbrains.com/plugin/27310-claude-code-beta-

## Contributing

Found something outdated or unclear? Open an issue or a pull request.
