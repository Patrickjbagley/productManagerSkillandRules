# Product Manager Skills, Rules & Templates

A shareable collection of **rules**, **skills**, and **templates** for product-led development and documentation. Use them in **Cursor** to get consistent PRDs, specs, doc structure, and feature workflows.

## What’s in this repo

| Folder | Contents |
|--------|----------|
| **rules/** | Cursor/Claude rule files (e.g. `.mdc`) for doc structure and conventions |
| **skills/** | Agent skills (e.g. `SKILL.md`) for PM workflows, doc structure, and feature builder |
| **templates/** | Markdown templates for PRDs, specs, feature pages, and doc structure |
| **importPrompts/** | **cursor-import.md** — one prompt containing every rule, skill, and template; paste into Cursor Chat and the AI adds all of them to the project |

## Quick start (Cursor)

1. Open **importPrompts/cursor-import.md**.
2. Copy the **entire** file (one long prompt with all rules, skills, and templates embedded).
3. Paste it into Cursor Chat and say: **Add all of the following to this project.**
4. Cursor will create `.cursor/rules/`, `.cursor/skills/`, and `templates/` and write each file (2 rules, 6 skills, 4 templates).

## Skills overview

### Product & documentation (use in any AI coding tool)

- **feature-builder** — End-to-end feature workflow: discovery → PRD → spec → design review → doc library cleanup → optional implementation.
- **prd-generation** — Write or update a PRD from problem context (standalone or as part of feature-builder).
- **spec-doc-generation** — Write or update a spec (summary, problems, audience, features, success metrics, user flows).
- **design-review** — Review PRD and spec for consistency and completeness; optionally compare to mocks/wireframes.
- **doc-library-cleanup** — Keep index, README, feature pages, and spec listings in sync after PRD/spec changes.
- **doc-structure** — Scaffold the standard docs folder (README, productBrief, audienceProfiles, designDetails, features, specDocs, productRequirementsDocs, images).


## Rules

- **doc-structure.mdc** — When creating or editing docs under `docs/`, use the standard structure (productBrief, audienceProfiles, features, specDocs, productRequirementsDocs, etc.). Copy into `.cursor/rules/` for Cursor (and Claude Code where supported).
- **product-mindset.mdc** — Product philosophy and strategy: understand before acting, clarity over speed, outcomes over outputs. Always apply when discussing product, features, or requirements. Copy into `.cursor/rules/` for Cursor (and Claude Code where supported).

## Templates

The **templates/** folder is the **single source of truth**. The skills (prd-generation, spec-doc-generation, doc-structure) read from here — there are no duplicate template files inside the skill folders. When you update a template, edit only the file in **templates/**.

- **feature-template.md** — One feature overview page (e.g. for `docs/features/`).
- **PRD-template.md** — Product Requirements Document structure.
- **spec-template.md** — Spec doc with user flows (tables, Gherkin, edge cases).
- **DOC-STRUCTURE-SPEC.md** — Full docs folder tree, purposes, link conventions, and stub content for scaffolding.

## Sharing

Put this repo on GitHub or GitLab and share the link. Others open **importPrompts/cursor-import.md**, copy the whole prompt, paste it into Cursor, and get all rules, skills, and templates added to their project.

## License

Use and adapt as you like. If you share improvements, consider opening a PR or linking back to this repo.
