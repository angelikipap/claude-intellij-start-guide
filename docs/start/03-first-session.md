# Step 3: Your first session

Claude Code is an **agent**: you describe a goal, and it reads files, runs commands and edits code to get there. You stay in control through permissions.

## 3.1 Talk to it like a colleague

Good prompts are specific about **what**, **where** and **how you'll know it's done**:

| Weak | Better |
|---|---|
| `fix the bug` | `OrderServiceTest.shouldApplyDiscount fails with NPE. Find the cause and fix it, then run the test.` |
| `add logging` | `Add SLF4J debug logging to the public methods of PaymentClient, same style as UserClient.` |
| `make it better` | `Refactor CsvImporter.parse into smaller methods. Behavior must not change; run mvn test after.` |

Reference files with `@`:

```text
Compare @src/main/java/com/acme/UserMapper.java with @src/main/java/com/acme/OrderMapper.java and make OrderMapper follow the same pattern.
```

## 3.2 Permissions: you approve actions

The first time Claude wants to edit a file or run a command, it asks you. You can:

- **Yes**: allow once
- **Yes, and don't ask again**: allow this command/tool for the project
- **No**: refuse, and tell Claude what to do instead

Press `Shift+Tab` to cycle through **permission modes**:

| Mode | Behavior | Use when |
|---|---|---|
| Normal | Asks before edits and commands | Default, learning |
| Accept edits | Edits files without asking, still asks for commands | You trust the direction and review diffs afterwards |
| Plan | Read-only: Claude researches and proposes a plan, changes nothing | Big or unclear tasks |

> **Tip:** start with **Plan mode** for anything non-trivial. Read the plan, correct it, then let Claude implement it.

> **Security note:** in JetBrains IDEs, accept-edits mode can also edit IDE config files that the IDE may run on its own. Stick to normal mode on untrusted code.

## 3.3 Stay in control while it works

- `Esc` interrupts Claude (see [Step 2.4](02-intellij-plugin.md#24-fix-the-esc-key) if it doesn't).
- While Claude works, you can type a message. It's queued and Claude reads it next.
- Review every diff in the IntelliJ diff viewer before accepting.
- Use Git as your safety net: commit before big changes, so `git diff` and `git restore` are always available.

## 3.4 Manage context

Claude remembers the whole conversation, which costs context and money.

- `/clear` starts fresh. Do it when you switch tasks.
- `/compact` summarizes a long conversation and keeps going.
- `claude -c` continues your last conversation. `claude --resume` lets you pick an older one.

## 3.5 Exercise

In a small Java project:

1. `Shift+Tab` into **Plan mode**.
2. Ask: `Give me an overview of this project: modules, main entry points, how it's built and tested.`
3. Switch back to normal mode and ask: `Add a unit test for <some class> covering the edge cases you think are missing. Run it.`
4. Review the diff in IntelliJ, accept it, and run the test from the IDE yourself.

---

Previous: [Step 2](02-intellij-plugin.md) · Next: [Step 4: CLAUDE.md](04-claude-md.md)
