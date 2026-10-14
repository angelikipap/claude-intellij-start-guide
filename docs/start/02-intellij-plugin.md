# Step 2: Connect IntelliJ

The **Claude Code [Beta]** plugin connects the CLI to the IDE. With it, Claude can:

- show proposed changes in IntelliJ's **diff viewer** instead of the terminal
- see your **current selection and open file** automatically
- read IntelliJ's **inspection diagnostics** (compile errors, warnings)
- open from the editor with a shortcut

## 2.1 Install the plugin

1. In IntelliJ open **Settings → Plugins → Marketplace**.
2. Search for **Claude Code** and install **Claude Code [Beta]** (by Anthropic).
   Direct link: https://plugins.jetbrains.com/plugin/27310-claude-code-beta-
3. **Restart IntelliJ** completely.

## 2.2 Start Claude inside IntelliJ

Choose one:

- Press `Cmd+Esc` (Mac) or `Ctrl+Esc` (Windows/Linux), **or**
- Click the Claude Code icon in the toolbar, **or**
- Open IntelliJ's **Terminal** tool window and type `claude`.

Run it from the **project root** so Claude sees the same files as the IDE.

When you start `claude` from IntelliJ's terminal, the IDE connection happens automatically.

### Starting from an external terminal?

Run `claude`, then type:

```text
/ide
```

You should see `Connected to IntelliJ IDEA.`

## 2.3 Show diffs in IntelliJ

Inside Claude, run `/config` and set **Diff tool** to `auto`. Claude's proposed edits now open in IntelliJ's diff viewer, where you can review them side by side before accepting.

## 2.4 Fix the ESC key

By default IntelliJ's terminal uses `Esc` to jump back to the editor, so `Esc` doesn't stop Claude. To fix it:

1. **Settings → Tools → Terminal**
2. Uncheck **"Move focus to the editor with Escape"**
3. Apply

## 2.5 Plugin settings (optional)

**Settings → Tools → Claude Code [Beta]**:

- **Claude command**: set the full path if IntelliJ can't find `claude`, e.g. `/home/me/.local/bin/claude`.
- **WSL users**: set the command to `wsl -d Ubuntu -- bash -lic "claude"` (use your distribution's name).
- **Remote Development**: install the plugin on the **remote host** (**Settings → Plugins (Host)**), not on your local client.

## 2.6 Try it

1. Open any class and select a method.
2. Press `Cmd+Esc` / `Ctrl+Esc`.
3. Ask: `explain what the selected code does`

The transcript shows `⧉ Selected N lines from <file>`, which means Claude received your selection.

4. Put your cursor in the Claude prompt and press `Cmd+Option+K` / `Alt+Ctrl+K` to insert a reference such as `@src/main/java/com/acme/OrderService.java#L40-62`.

---

Previous: [Step 1](01-install.md) · Next: [Step 3: Your first session](03-first-session.md)
