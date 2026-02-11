---
name: doc-library-cleanup
description: Keeps the project's document library consistent after new or changed PRDs and specs. Discovers or uses the project's index, README, feature/capability pages, and spec listings; proposes and applies updates so new docs are discoverable. Use when new docs are added or changed and the user wants index and related pages propagated. Works standalone or as part of the feature-builder workflow.
---

# Document Library Cleanup

Ensures new or updated PRDs and specs are reflected across the project's doc library (e.g. index, README, feature or capability pages, spec listings). Can run **standalone** or **composed** (e.g. after Feature Builder Phases 1–3). Adapts to the project's actual doc structure; does not assume a specific folder layout.

---

## Prerequisites Check

You need: the new or changed PRD/Spec (path or content) and the feature or capability name/area.

- **If the user has already provided these** (e.g. from prior phases): proceed to **Document Discovery** below.
- **If not:** ask for the path to the new/updated PRD and spec and the feature or capability name. **STOP until you have them.** Then proceed to **Document Discovery**.

---

## Step 1: Document Discovery

1. **Identify the feature or capability area** from the new docs or the user.
2. **Discover the project's doc structure** by inspecting the repo (or asking the user):
   - Is there an **index or catalog** of docs (e.g. INDEX.md, docs/README.md, or similar)? Where are PRDs/specs listed?
   - Where do **specs or requirements** live (e.g. specs/, docs/specs/, requirements/)? Is there a README or listing there?
   - Are there **feature or capability pages** that link to PRDs/specs (e.g. a features folder, product areas, or module docs)? What do they look like (tables, bullets, frontmatter)?
3. **Identify what to update:** which index rows, README sections, feature/capability pages, and spec listings need to be added or changed so the new docs are discoverable and consistent. If the project has no index or feature pages, say so and propose minimal updates (e.g. add to a single README or create a simple index) and confirm with the user.

---

## Step 2: Propose Updates

Before editing, tell the user what you will change and ask for confirmation.

List the updates you plan, using the **project's actual paths and conventions** (from Step 1):

- **Index/catalog:** add or update a row or section for the new PRD/Spec; update "Applies to" or description if editing an existing entry.
- **Feature/capability pages:** add or update a row or section that references this capability; link to the new or updated PRD/Spec; add or update any "How do I…?" or similar bullets if that's the project's pattern.
- **README or overview:** only if this capability belongs in the project's main README or docs overview; add or adjust wording and link.
- **Specs/requirements listing:** if the project has a specs README or listing file, add or update the entry for the new spec.

Ask: **"Confirm that I should update these docs as above (or tell me what to change)."**

**STOP and wait for confirmation** before making any edits.

---

## Step 3: Apply Updates

Only after the user confirms, apply the doc propagation edits. Check for discrepancies (e.g. wrong links, duplicate entries, outdated descriptions) and fix them.

---

## Output

- Updated index, README, feature/capability pages, and spec listings as agreed (using the project's actual structure).
- Short summary of what was updated.

---

## Confirmation Gate

After applying updates:

- Summarize what was changed and where.
- Ask: **"Doc library cleanup done. Confirm to proceed, or tell me what to fix."**

**STOP and wait for confirmation.** Do not proceed until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 4 (Doc Library Cleanup) is complete and return to the orchestrator.
