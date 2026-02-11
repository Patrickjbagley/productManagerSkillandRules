---
name: spec-doc-generation
description: Produces a Spec Doc (feature summary, problems, audience, features, success metrics, and user flows). Use when the user needs a spec document written or updated, or when a PRD exists and the next deliverable is a spec. Works standalone or as part of the feature-builder workflow.
---

# Spec Doc Generation

Produces a Spec Doc including user flows. Can run **standalone** or **composed** (e.g. PRD already exists from Feature Builder Phase 1).

---

## Prerequisites Check

You need: clear problem, target audience, and goals. A PRD is ideal but not required.

- **If you already have this context** (e.g. a confirmed PRD or discovery summary): proceed to **Generate Spec Doc** below.
- **If you do not:** either ask the user to point to a PRD or share the problem, audience, and goals. Summarize and ask for confirmation. **STOP and wait for confirmation.** Then proceed to **Generate Spec Doc**.

---

## Generate Spec Doc

Use the structure and section order in **templates/spec-template.md** (project root). Read that file when generating the spec; if it is missing, ask the user to add the templates folder from this repo. Replace all `[placeholders]` with project- and feature-specific content. Include user flows for each main flow; use the table format (Step | Screen / state | User action | Result / navigation) and add Gherkin and edge cases where they clarify behavior. Omit or collapse sections only if the user agrees.

Produce a **Spec Doc** that includes:

- Product or feature summary
- Problems being solved (clearly articulated)
- Target audience(s)
- Key features and functionality (problem-aligned, not solution-led)
- Success metrics: adoption metrics; value metrics (time saved, error reduction, % improvement)

Include **user flows** for each flow (required):

- Each screen or state
- Layout at a conceptual level (not visual design)
- All possible user actions on each screen
- Navigation paths between screens
- Prerequisites, dependencies, or edge cases

Use user stories and Gherkin (GIVEN / WHEN / THEN) where they clarify behavior.

Before writing: identify unclear workflows or actors and ask targeted questions if needed.

Write the spec to the path the user specifies, or propose a path based on the project's doc structure (e.g. a specs or requirements directory and a clear filename) and confirm before writing.

---

## Output

- One Spec Doc file (Markdown), saved to the agreed path.
- Short summary of key decisions.

---

## Confirmation Gate

After writing:

- Summarize the spec and key decisions.
- Ask: **"Is this spec correct? Confirm to proceed, or tell me what to change."**

**STOP and wait for confirmation.** Do not proceed until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 2 (Spec) is complete and return to the orchestrator.
