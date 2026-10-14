# Docs-as-code conventions

Short rules we (Dipin Roka) follow when writing documentation. These are the conventions a
recruiter can verify against the repositories.

## File conventions

- One `README.md` per repo. Every public repo has one; every repo we link from a resume has one.
- `docs/` for long-form. If a README grows beyond ~3 screens, split by audience.
- `SCHEMA.md` (or a schema block in the README) for any JSON/YAML file consumed by code.
- `CHANGELOG.md` in Keep a Changelog format for anything shipped to users.

## Markdown style

- Headings in ATX style (`#`, `##`), never setext.
- Code blocks always with a language tag.
- Tables only when they earn their place; otherwise lists.
- One idea per paragraph; lines ~100 chars where possible (so diffs stay small).
- No trailing whitespace. LF line endings.

## Commit conventions

`type(scope): summary` — Conventional Commits.

Types: `docs`, `feat`, `fix`, `refactor`, `chore`, `test`, `ci`.  
Example: `docs(astra): add JSON schema for incidents.json`.

## Pull requests

- Title matches the commit convention.
- Body has **What / Why / How to test** (three lines minimum).
- Screenshots attached for any visual change.
- One concept per PR.

## YAML / config

- 2-space indentation.
- Quote strings with special characters.
- Never hardcode secrets; use `${{ secrets.X }}` in workflows.
- Validate YAML in CI (`mkdocs build --strict` passes).

## Definition of "done" for a doc

- [ ] Renders without errors (`mkdocs build --strict`).
- [ ] Every code block runs as written.
- [ ] Links resolve (no 404).
- [ ] Front matter (title, status) present.
- [ ] Reviewed by a second pair of eyes, or, for solo work, re-read the next day.
