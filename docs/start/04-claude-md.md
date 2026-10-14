# Step 4: Teach Claude your project with CLAUDE.md

Every session starts without memory of the previous one. `CLAUDE.md` is a Markdown file Claude reads **automatically at the start of every session**. Use it for things a new team member would need to know.

## 4.1 Generate one

From the project root:

```text
/init
```

Claude studies the codebase and writes a `CLAUDE.md`. Review it, fix anything wrong, and **commit it** so the whole team shares it.

## 4.2 What to put in it

Keep it short and concrete. Example for a Spring Boot service:

```markdown
# CLAUDE.md

## Build and test
- Build: `./mvnw clean verify`
- Single test: `./mvnw test -Dtest=OrderServiceTest#shouldApplyDiscount`
- Run locally: `./mvnw spring-boot:run -Dspring-boot.run.profiles=local`

## Conventions
- Java 21, Spring Boot 3. Constructor injection only, no field `@Autowired`.
- DTOs are Java records in `api/dto`. Never expose JPA entities from controllers.
- Tests: JUnit 5 + AssertJ + Mockito. Test names: `should<Behavior>When<Condition>`.
- Logging: SLF4J, no `System.out`.

## Don't
- Don't edit files under `src/main/resources/db/migration/` that are already released. Add a new Flyway migration instead.
- Don't commit `application-local.yml`.
```

Things that **don't** belong there: anything Claude can easily see from the code, long tutorials, and secrets.

## 4.3 Where CLAUDE.md files live

| File | Scope | Commit to Git? |
|---|---|---|
| `./CLAUDE.md` | This project, whole team | Yes |
| `./CLAUDE.local.md` | This project, only you | No (add to `.gitignore`) |
| `~/.claude/CLAUDE.md` | All your projects | n/a |
| `some/module/CLAUDE.md` | Read when Claude works in that folder | Yes |

Use `/memory` to open and edit these files.

## 4.4 Keep it alive

When Claude makes the same mistake twice, add a rule:

```text
Add to CLAUDE.md: integration tests need the `it` Maven profile: ./mvnw verify -Pit
```

---

Previous: [Step 3](03-first-session.md) · Next: [Step 5: Everyday workflows](05-workflows.md)
