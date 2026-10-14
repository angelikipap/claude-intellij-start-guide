# Step 5: Everyday workflows

Prompts you can copy and adapt. Tip: select code in IntelliJ before asking, and Claude will get it as context.

## 5.1 Understand unfamiliar code

```text
How does a request to POST /orders flow through this service? List the classes involved in order and point out where validation and persistence happen.
```

```text
Explain the selected code. What could go wrong with it under concurrent access?
```

## 5.2 Fix a compile error or failing test

IntelliJ shows red squiggles? Claude can read the same diagnostics:

```text
Fix the compile errors in the current file. Use the IDE diagnostics.
```

For a failing test, paste the stack trace or just name the test:

```text
./mvnw test -Dtest=InvoiceServiceTest fails. Find the root cause (don't just change the assertion), fix it and rerun the test.
```

## 5.3 Write tests

```text
Write JUnit 5 tests for @src/main/java/com/acme/pricing/DiscountCalculator.java. Cover boundaries, null inputs and rounding. Follow the style of the existing tests in src/test. Run them.
```

## 5.4 Implement a feature: plan first

1. `Shift+Tab` to **Plan mode**.
2. Describe the feature:
   ```text
   Add pagination (page, size, sort) to GET /customers. Keep backwards compatibility: no params = current behavior.
   ```
3. Read the plan and correct it ("use Spring's Pageable", "no new dependencies").
4. Approve, and review each diff in IntelliJ as it comes.
5. Ask Claude to run the build and tests at the end.

## 5.5 Refactor safely

```text
Extract the retry logic duplicated in PaymentClient and ShippingClient into a shared helper. Behavior must not change. Run the full test suite before and after.
```

> Tip: for renames and moves, IntelliJ's own refactorings (`Shift+F6`, `F6`) are faster and safer. Use Claude for refactors that need judgment.

## 5.6 Review your changes before a PR

```text
Review my uncommitted changes (git diff) for bugs, missing tests and anything that breaks the conventions in CLAUDE.md.
```

## 5.7 Commit and PR

```text
Commit these changes with a clear message.
```

If the GitHub CLI (`gh`) is installed and logged in:

```text
Create a branch, commit, push and open a PR with a summary and test notes.
```

## 5.8 Work with the outside world

Claude can run any CLI tool you allow: `git`, `mvn`/`gradle`, `docker`, `kubectl`, `curl`, `psql`, and more.

```text
Run the app with docker compose, call GET /health with curl and tell me if anything fails to start.
```

---

Previous: [Step 4](04-claude-md.md) · Next: [Step 6: Customize](06-customize.md)
