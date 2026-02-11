---
name: doc-structure
description: Scaffolds the standard documentation folder structure (README, productBrief, audienceProfiles, designDetails, features, specDocs, productRequirementsDocs, images). Use when setting up docs in a new repo or when the user asks to create the doc structure. When adding a new feature page, use the feature-template.md structure.
---

# Doc structure (scaffold)

Use this skill when the user wants to **scaffold the documentation folder structure** in a repo (new or existing) or when they ask to **add a new feature page** under docs. The canonical layout and stub content are in **templates/DOC-STRUCTURE-SPEC.md** (project root); **templates/feature-template.md** defines the structure for one feature page. Read those files when scaffolding; if they are missing, ask the user to add the templates folder from this repo.

---

## When to use

- User says "scaffold the doc structure", "create the doc folder structure", "set up docs", or similar.
- User says "add a new feature page" or "create a feature doc for [feature name]" and the repo uses (or will use) this structure.

---

## Scaffold steps (full structure)

When scaffolding the doc structure:

1. **Ensure `docs/` exists** in the project root. Create it if it does not.

2. **Create the folder tree:**
   - `docs/README.md`
   - `docs/productBrief.md`
   - `docs/audienceProfiles.md`
   - `docs/designDetails/style-guide.md`
   - `docs/features/` (directory)
   - `docs/specDocs/` (directory)
   - `docs/productRequirementsDocs/` (directory)
   - `docs/images/` (directory)

3. **Write stub content** for each file using the templates in **templates/DOC-STRUCTURE-SPEC.md**:
   - **README.md** — Short entry with links to productBrief, audienceProfiles, features, specDocs, productRequirementsDocs, and optional INDEX. (Exact stub is in the spec under "Stub content for scaffolding → README.md".)
   - **productBrief.md** — Section headings and "Audience: see [audienceProfiles.md](audienceProfiles.md)." plus placeholders for Vision, Measurements, Features overview, Service blueprint, Quick answers. (Use spec's productBrief stub.)
   - **audienceProfiles.md** — Sections: Primary audience, Secondary audience; subsections "Jobs to be done" per persona with placeholder bullets. (Use spec's audienceProfiles stub.)
   - **designDetails/style-guide.md** — Placeholder sections: Typography, Spacing, Colors, Components. (Use spec's designDetails stub.)

4. **Optional:**
   - Add `docs/specDocs/README.md` with one line: "Spec documents. Naming: feature-name-spec.md."
   - Add `docs/productRequirementsDocs/README.md` with one line: "Product requirements documents. Naming: feature-name-prd.md."
   - Add `docs/images/.gitkeep` so the images folder is tracked if empty.

5. **Do not overwrite** existing files that already have content. If a file exists and is non-empty, skip writing that file or ask the user whether to replace it.

---

## Adding a new feature page

When the user asks to add a new feature page (e.g. "add a feature doc for [name]"):

1. **Read templates/feature-template.md** (project root) to get the exact structure and link conventions.
2. **Create** `docs/features/[feature-name].md` (use kebab-case for the filename, e.g. `report-generation.md`).
3. **Fill in** the template sections:
   - Title: `# [Feature Name] — Feature Overview`
   - Intro paragraph, **Applies to:**, *Related:* (links to other feature pages if relevant)
   - **Features and documentation** — table with columns Feature | Applies to | Spec / PRD. Use `../specDocs/` and `../productRequirementsDocs/` for links.
   - **How do I…?** — placeholder Q&A bullets with links to specDocs/PRDs as needed
   - **Implementation reference** (optional) — add if the user has architecture/plan docs to link
4. Replace all `[placeholders]` with the feature name and any known routes or sub-features. If the feature does not yet have a spec or PRD, leave the table row or link as a placeholder and note "(to be added)".

---

## Reference files

- **templates/DOC-STRUCTURE-SPEC.md** — Full folder tree, purpose of each file/folder, link conventions, and all stub content. Use it when scaffolding or when unsure about the layout.
- **templates/feature-template.md** — Copy-paste-ready template for one feature page. Use it when creating `docs/features/[feature-name].md`.
- **doc-structure.mdc** (in this repo's `rules/` folder) — Cursor rule. Recipients can copy it into their repo's `.cursor/rules/` so Cursor (and Claude Code) respects the structure when creating or editing docs.

---

## Sharing

To share this structure with others: give them the **doc-structure** skill (this SKILL.md), the **templates** folder (DOC-STRUCTURE-SPEC.md, feature-template.md, etc.), and the **rules/doc-structure.mdc** rule. They copy the skill into `.cursor/skills/`, the templates into their project root, and the rule into `.cursor/rules/`. Then they can run the skill to scaffold `docs/` in their repo.
