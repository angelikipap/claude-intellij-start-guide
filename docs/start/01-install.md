# Step 1: Install Claude Code

Claude Code is a command-line tool (`claude`). The IntelliJ plugin does **not** include it, so install the CLI first.

## 1.1 Install

Pick the command for your system.

**macOS, Linux, WSL (recommended, auto-updates):**

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows PowerShell:**

```powershell
irm https://claude.ai/install.ps1 | iex
```

**Windows CMD:**

```batch
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

Alternatives:

| Method | Command | Auto-updates? |
|---|---|---|
| Homebrew | `brew install --cask claude-code` | No (`brew upgrade claude-code`) |
| WinGet | `winget install Anthropic.ClaudeCode` | No (`winget upgrade Anthropic.ClaudeCode`) |
| npm (Node.js 22+) | `npm install -g @anthropic-ai/claude-code` | Yes, if npm's global dir is writable |

> Never use `sudo npm install -g`.

## 1.2 Verify

Open a **new** terminal and run:

```bash
claude --version
```

You should see something like `2.1.x (Claude Code)`. If you get `command not found`, the install folder (`~/.local/bin` on macOS/Linux) is not on your `PATH`. Add it to your shell profile and open a new terminal.

For a full health check:

```bash
claude doctor
```

## 1.3 Log in

Go to any project folder and start Claude:

```bash
cd ~/projects/my-app
claude
```

The first time, a browser window opens so you can log in with your Claude account. Once logged in, you are in an interactive session. Type `/exit` (or press `Ctrl+C` twice) to quit.

> **Company setups:** if your organization uses the Claude Console, Amazon Bedrock, Google Vertex AI or Microsoft Foundry instead of claude.ai accounts, ask your admin which login to use.

---

Next: [Step 2: Connect IntelliJ](02-intellij-plugin.md)
