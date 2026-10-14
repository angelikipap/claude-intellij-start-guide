# Step 7: Tips and troubleshooting

## Habits that pay off

1. **Plan before big changes.** Plan mode → review → implement.
2. **Give Claude a way to check its work**: a test, a build command, a curl call. "Run the tests after" is the most useful sentence you can add.
3. **One task per conversation.** `/clear` between unrelated tasks.
4. **Commit often.** Small commits make Claude's changes easy to review and undo.
5. **Review every diff.** You own the code Claude writes.
6. **Teach, don't repeat.** If you correct Claude twice on the same thing, put it in `CLAUDE.md`.
7. **Never paste secrets** into prompts. Add `Read` deny rules for `.env` and local config files.

## Troubleshooting

| Problem | Fix |
|---|---|
| `claude: command not found` | Open a new terminal; add `~/.local/bin` to `PATH`; run `claude doctor`. |
| Plugin says "Cannot launch Claude Code" | Set the full path in **Settings → Tools → Claude Code [Beta] → Claude command**. |
| `/ide` says "No available IDEs detected" | Check the plugin is installed and enabled, restart IntelliJ completely, start `claude` from the project root. |
| Diffs show in the terminal, not IntelliJ | `/config` → **Diff tool** → `auto` (only shown while connected to the IDE). |
| `Esc` doesn't interrupt Claude | **Settings → Tools → Terminal** → uncheck "Move focus to the editor with Escape". |
| WSL: IDE not detected | Allow WSL2 traffic through Windows Firewall, or set `networkingMode=mirrored` in `.wslconfig` (Windows 11 22H2+). |
| Remote Development: nothing works | Install the plugin on the **host** (**Settings → Plugins (Host)**). |
| Claude seems to "forget" things | The conversation got long: `/compact`, or `/clear` and restate the task. Put lasting facts in `CLAUDE.md`. |

Still stuck? Run `claude doctor`, and see the [official troubleshooting guide](https://code.claude.com/docs/en/jetbrains#troubleshooting).

---

Previous: [Step 6](06-customize.md) · Back to [README](README.md)
