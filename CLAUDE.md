# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A content-only repository: a step-by-step Markdown tutorial teaching developers to use Claude Code inside IntelliJ IDEA (and other JetBrains IDEs). There is no application code, no build system, and no test suite — the "source" is the prose in `docs/start/`. Changes are edits to Markdown.

## Structure

- `docs/README.md` — index of the documentation sections; each section is its own folder.
- `docs/start/` — the getting-started guide (the only section written so far).
  - `README.md` — the section landing page and table of contents.
  - `NN-*.md` — the seven sequential tutorial steps (`01-install` … `07-troubleshooting`), meant to be read in order. They live in the same directory as the section README, so all cross-links are same-directory relative links.
- `docs/add_skills/`, `docs/add_mcp/` — planned future sections (not yet created). When adding a section, add a row to `docs/README.md`.

## Conventions that span files

These invariants are easy to break because they're maintained by hand across multiple files. When adding, removing, or reordering steps, keep all three in sync:

1. **README steps table** (`src/README.md`) maps `# → step title (link) → time`. Every `docs/NN-*.md` has exactly one row; the link text and estimated time live only here.
2. **Nav footer** at the bottom of each `docs/NN-*.md`: a `---` rule followed by `Previous: [...](NN-*.md) · Next: [...](NN-*.md)` with relative links to the adjacent steps. The first and last steps omit the missing direction.
3. **Filename numbering** (`NN-`) defines reading order and must match the table and footers. Renumbering a file means updating every relative link that points to it.

Other conventions:

- Headings follow `# Step N: Title` then `## N.1`, `## N.2` sub-sections.
- Cross-references between docs use relative links (e.g. `04-claude-md.md`), not absolute URLs.
- Copy-paste prompts for the reader go in ` ```text ` fenced blocks; shell/IDE commands and keybindings go in inline code or tables.
