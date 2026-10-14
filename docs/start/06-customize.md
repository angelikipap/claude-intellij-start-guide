# Step 6: Customize: permissions, skills, agents, MCP

## 6.1 Stop approving the same commands

Use `/permissions`, or edit `.claude/settings.json` in the project (shared via Git):

```json
{
  "permissions": {
    "allow": [
      "Bash(./mvnw test:*)",
      "Bash(./mvnw verify:*)",
      "Bash(git status)",
      "Bash(git diff:*)"
    ],
    "deny": [
      "Read(./.env)",
      "Read(./src/main/resources/application-local.yml)"
    ]
  }
}
```

`deny` rules on `Read` also stop IntelliJ from sending those files' contents as selection context.

Personal, uncommitted overrides go in `.claude/settings.local.json`. Settings for all your projects go in `~/.claude/settings.json`.

## 6.2 Skills: reusable workflows

A skill is a folder with a `SKILL.md` that teaches Claude a repeatable task. Claude loads it when your request matches its description, or when you type `/<skill-name>`.

`.claude/skills/new-endpoint/SKILL.md`:

```markdown
---
name: new-endpoint
description: Scaffold a new REST endpoint following team conventions. Use when the user asks to add an endpoint/API.
---

1. Create a request/response record in `api/dto`.
2. Add the controller method with validation (`@Valid`).
3. Add the service method; keep business logic out of the controller.
4. Write a `@WebMvcTest` for the controller and a unit test for the service.
5. Run `./mvnw test` and report results.
```

Location: `.claude/skills/` (project, shared) or `~/.claude/skills/` (you, all projects).

## 6.3 Agents (subagents): specialists with their own context

An agent runs in its **own context window** with its own tools and instructions, and returns only a summary. Use agents for noisy or long tasks so your main conversation stays clean.

Create one with `/agents`, or by hand in `.claude/agents/test-runner.md`:

```markdown
---
name: test-runner
description: Runs the test suite and diagnoses failures. Use after code changes or when tests fail.
tools: Read, Grep, Glob, Bash
model: sonnet
---

Run `./mvnw test`. For each failure, find the root cause in the code under test
(not the assertion). Return: failing test | root cause | suggested fix.
Do not edit files.
```

Then: `use the test-runner agent to check my changes`.

**Orchestrating:** your main session coordinates agents. Ask for independent work in parallel (`run the test-runner and a code review agent in parallel`), and dependent steps in sequence.

## 6.4 MCP: connect external tools

MCP servers give Claude access to systems such as Jira, GitHub, databases and browsers.

```bash
# example: add an MCP server for this project
claude mcp add <name> -- <command to start the server>
claude mcp list
```

Check the server's own docs for the exact command and credentials. Keep tokens in environment variables, never in committed files.

## 6.5 Hooks: automate around Claude

Hooks run your scripts on events, for example formatting a file after every edit. Configure them in `settings.json` or ask Claude: `add a hook that runs google-java-format on Java files after each edit`.

## 6.6 Share with your team

| What | How |
|---|---|
| Conventions | Commit `CLAUDE.md` |
| Permissions, hooks | Commit `.claude/settings.json` |
| Skills, agents for one repo | Commit `.claude/skills/` and `.claude/agents/` |
| Skills/agents for many repos | Package them as a **plugin** in a Git repo (a "marketplace"); teammates run `/plugin marketplace add <repo>` and `/plugin install <plugin>@<marketplace>` |

---

Previous: [Step 5](05-workflows.md) · Next: [Step 7: Tips and troubleshooting](07-troubleshooting.md)
