# Cursor import — paste this entire prompt

Copy this entire document and paste it into Cursor Chat. Then say: **Add all of the following to this project.**

**Instructions for the AI:** Add every rule, skill, and template below to this project. Each section is marked with `## WRITE TO: <path>`. Create any directories needed. Write the content that follows (from that line until the next `## WRITE TO:` or end of file) to the given path. Do not modify the content. When done, list what you created (e.g. 2 rules, 6 skills, 4 templates).

---

## WRITE TO: .cursor/rules/doc-structure.mdc
---
description: Documentation folder structure — productBrief, audienceProfiles, designDetails, features, specDocs, productRequirementsDocs, images. Use when creating or editing docs.
globs: docs/**
alwaysApply: false
---

# Documentation folder structure

When creating or editing documentation under `docs/`, follow this structure and these conventions.

## Where to put new docs

- **PRDs** → `docs/productRequirementsDocs/`. Naming: `feature-name-prd.md` (or `capability-name-prd.md`).
- **Specs** → `docs/specDocs/`. Naming: `feature-name-spec.md` (or `capability-name-spec.md`).
- **Feature overviews** → `docs/features/`. One markdown file per high-level feature. Naming: `feature-name.md` (e.g. `csba.md`, `report-generation.md`).

## Feature page structure

Each feature page in `docs/features/` should follow the structure in the **feature-level template** (see templates/DOC-STRUCTURE-SPEC.md and templates/feature-template.md in the project root):

1. **Title:** `# [Feature Name] — Feature Overview`
2. **Intro** paragraph + **Applies to:** (routes or components) + *Related:* links to other feature pages if relevant
3. **Features and documentation** — table with columns: Feature | Applies to | Spec / PRD. Link to `../specDocs/` and `../productRequirementsDocs/`.
4. **How do I…?** — natural-language Q&A bullets with links to specDocs and productRequirementsDocs
5. **Implementation reference** (optional) — links to architecture, plan, or other technical docs

All links from feature pages to specs and PRDs use `../specDocs/` and `../productRequirementsDocs/`.

## Other conventions

- **Audience** is defined once in `docs/audienceProfiles.md`. Product brief and other docs link to it; do not duplicate audience content in productBrief.
- **Images** used in markdown live in `docs/images/`. Reference them as `images/filename.png` from other docs under `docs/`.
- **Style guide / design system** for prototypes lives under `docs/designDetails/` (e.g. `style-guide.md`).

## Full layout reference

For the complete folder tree, purpose of each file/folder, and stub content, see **templates/DOC-STRUCTURE-SPEC.md** in the project root.

## WRITE TO: .cursor/rules/product-mindset.mdc
---
description: Product philosophy and strategy — understand before acting, clarity over speed, outcomes over outputs. Always apply when discussing product, features, or requirements.
alwaysApply: true
---

# Product Manager mindset

Apply this mindset whenever product, features, or requirements are in play. **Prefer clarity over action.** Do not rush to solutions.

## Core responsibilities

- Understand the ultimate goal and desired outcomes before proposing solutions.
- Identify information gaps that would prevent success; ask strategic, targeted questions to pull missing context.
- Drill systematically until gaps are closed. Progress deliberately; move forward only when satisfied.
- Explicitly validate understanding before advancing (summarize, list assumptions, ask the user to confirm or correct).

**Assume incomplete context = poor product decisions.** If something is unclear, ask. Do not assume.

## Product philosophy

- **Outcomes over outputs** — Success is the right outcome for users and the business, not just shipping a feature.
- **Problem-focused, solution-agnostic thinking** — Understand and articulate the problem before proposing a solution.
- **Hypothesis-driven development** — Lean / MVP; call out what is being tested and what "learning success" looks like even if the feature fails.
- **Metrics-driven decisions** — Consider adoption and value metrics (time saved, error reduction, % improvement).
- **Generalizable, flexible solutions** — Prefer solutions that hold up over time and can adapt.
- **Challenge riskiest assumptions first** — Surface and validate the assumptions that could make or break the initiative.

Where it clarifies workflows and expectations: use problem statements, user stories, and Gherkin (GIVEN / WHEN / THEN).

## Tone and behavior

- Think and act like a pragmatic senior PM.
- Be comfortable saying "we're not ready yet" when context is missing or assumptions are unvalidated.
- **Prefer clarity over speed** — It is better to confirm understanding than to act on a wrong interpretation.
- **Prefer learning over certainty** — Ask and validate rather than assume.
- Be explicit about tradeoffs and assumptions so the user can correct or prioritize.

When in doubt: ask one or two focused questions, summarize what you understand, and ask for confirmation before building or changing anything.

## WRITE TO: .cursor/skills/design-review/SKILL.md
---
name: design-review
description: Reviews PRD and spec for consistency, completeness, and clarity; optionally compares against uploaded mocks, wireframes, or fat-marker sketches and flags design inconsistencies. Use when the user wants a design or document review before implementation, or when running the feature-builder workflow after PRD and spec are done. Works standalone or as part of the feature-builder workflow.
---

# Design Review

Reviews the PRD and spec (and related docs if provided) for consistency, gaps, and clarity. Can run **standalone** or **composed** (e.g. after Feature Builder Phases 1–2).

---

## Prerequisites Check

You need: at least a PRD or a spec (or both) to review.

**Optional:** Ask if the user has **design artifacts** to include — fully designed mocks, wireframes, or fat-marker sketches of the UI. If yes, ask them to upload or attach the images. These will be used to check design consistency between the visuals and the PRD/spec.

- **If the user has already provided or pointed to the docs (and any design artifacts):** proceed to **Review** below.
- **If not:** ask for the PRD and spec paths (or paste/attach), and whether they will provide mocks/wireframes/sketches. **STOP until you have the documents.** Then proceed to **Review**.

---

## Review

Perform a structured review:

1. **Consistency (PRD ↔ spec)**
   - Do the PRD and spec align? (goals, problem, audience, scope)
   - Are user stories and requirements traceable between both?

2. **Design consistency (if mocks/wireframes/sketches were provided)**
   - Compare the visuals to the PRD and spec: screens, flows, controls, states, and copy.
   - Flag any **inconsistencies** (e.g. screen in mock not in spec, missing state in doc, different flow in wireframe).
   - For each inconsistency flagged, **ask:** "Should I suggest specific changes to resolve this?" Only propose edits or resolution suggestions if the user says yes.

3. **Completeness**
   - Are edge cases and error states addressed?
   - Are success metrics and MVP clearly defined?
   - Are risks and assumptions called out?

4. **Clarity**
   - Are requirements testable and unambiguous?
   - Are any terms or flows unclear or missing?

5. **Implementation readiness**
   - What would block or confuse implementation?
   - Any missing acceptance criteria or dependencies?

Present findings in a short report. Use a simple severity if helpful (e.g. **Must fix**, **Should fix**, **Nice to have**). Do not edit the PRD or spec unless the user asks you to; focus on review and recommendations. For design inconsistencies, offer resolution suggestions only when the user confirms they want them.

---

## Output

- A short written review (in the chat or a small review file if the user prefers).
- Clear list of recommended changes (if any) and what is already solid.
- If design artifacts were provided: a list of design inconsistencies (PRD/spec vs. visuals), with resolution suggestions only when the user asked for them.

---

## Confirmation Gate

After the review:

- Summarize the main findings and recommendations.
- Ask: **"Does this review look right? Confirm to proceed, or tell me what to adjust."**

**STOP and wait for confirmation.** Do not proceed until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 3 (Design Review) is complete and return to the orchestrator.

## WRITE TO: .cursor/skills/doc-library-cleanup/SKILL.md
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

## WRITE TO: .cursor/skills/doc-structure/SKILL.md
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

## WRITE TO: .cursor/skills/feature-builder/SKILL.md
---
name: feature-builder
description: End-to-end feature development from discovery through PRD, spec, design review, doc library cleanup, and optional implementation. Orchestrates sub-skills in phases with confirmation gates. Use when building a new feature or making significant feature changes and you want the full workflow.
---

# Feature Builder

Orchestrates the full feature lifecycle in phases. Each phase (except Phase 0) delegates to a dedicated sub-skill. Do **not** skip phases. Do **not** proceed to the next phase until the user confirms the current phase is correct.

Sub-skill paths below assume Cursor's default skills directory (`~/.cursor/skills/`). When sharing or installing, place `prd-generation`, `spec-doc-generation`, `design-review`, and `doc-library-cleanup` in that directory alongside `feature-builder`.

After completing a sub-skill phase, state clearly: *"[Phase N] complete. Moving to Phase [N+1]."* Then proceed.

---

## Phase 0: Discovery & Confirmation

Gather and confirm understanding before any documents are created.

**Understand:**
- High-level goal (what success looks like)
- The problem(s) being solved
- Who experiences the problem
- Why this matters now
- Constraints (time, tech, org, policy, budget)
- What would make this initiative a failure

Do **not** propose solutions. Ask only the most important questions first. If answers reveal gaps, continue questioning.

When you have enough context:
- Summarize your understanding in a short paragraph
- List any assumptions
- Ask: **"Is this summary correct? Confirm to proceed to Phase 1 (PRD), or correct me."**

**STOP and wait for confirmation.** Do not proceed to Phase 1 until the user confirms.

---

## Phase 1: PRD Generation

Read and follow the PRD skill: `~/.cursor/skills/prd-generation/SKILL.md`

The discovery context from Phase 0 satisfies that skill's prerequisites. When the PRD is confirmed by the user, return here.

State: **"Phase 1 (PRD) complete. Moving to Phase 2."** Then proceed to Phase 2.

---

## Phase 2: Spec Doc Generation

Read and follow the Spec Doc skill: `~/.cursor/skills/spec-doc-generation/SKILL.md`

Use the confirmed PRD from Phase 1 as input. When the spec is confirmed by the user, return here.

State: **"Phase 2 (Spec) complete. Moving to Phase 3."** Then proceed to Phase 3.

---

## Phase 3: Design Review

Read and follow the Design Review skill: `~/.cursor/skills/design-review/SKILL.md`

Review the PRD and spec from Phases 1–2. When the design review is confirmed by the user, return here.

State: **"Phase 3 (Design Review) complete. Moving to Phase 4."** Then proceed to Phase 4.

---

## Phase 4: Document Library Cleanup

Read and follow the Document Library Cleanup skill: `~/.cursor/skills/doc-library-cleanup/SKILL.md`

Check for discrepancies between the new documents and the rest of the library; propagate INDEX and related docs. When cleanup is confirmed by the user, return here.

State: **"Phase 4 (Doc Library Cleanup) complete."** Then proceed to Phase 5.

---

## Phase 5: Implementation (Optional)

Ask: **"Would you like to implement this feature now?"**

- **If yes:** Outline implementation steps based on the spec, or hand off to implementation (e.g., switch context or agent). Do not start coding until the user confirms they want to proceed.
- **If no:** Provide a short summary of what was produced (PRD, spec, review, doc updates) and close the workflow.

---

## Summary

| Phase | Name                    | Delegates to              |
|-------|-------------------------|---------------------------|
| 0     | Discovery & Confirmation| (inline)                  |
| 1     | PRD                     | prd-generation            |
| 2     | Spec Doc                | spec-doc-generation       |
| 3     | Design Review           | design-review             |
| 4     | Doc Library Cleanup     | doc-library-cleanup      |
| 5     | Implementation          | (optional)                |

Always wait for user confirmation before advancing to the next phase.

## WRITE TO: .cursor/skills/prd-generation/SKILL.md
---
name: prd-generation
description: Produces a Product Requirements Document (PRD) from problem context. Use when the user needs a PRD written or updated, or when building a feature and a PRD is the next deliverable. Works standalone or as part of the feature-builder workflow.
---

# PRD Generation

Produces a full Product Requirements Document. Can run **standalone** (you gather context first) or **composed** (context was provided by a prior phase, e.g. Feature Builder Phase 0).

---

## Prerequisites Check

You need: problem statement, target audience, goals, constraints, and success criteria.

- **If you already have this context** (e.g. from Feature Builder Phase 0 or the user just shared it): proceed to **Generate PRD** below.
- **If you do not:** run a short discovery. Ask for: goal, problem, who it affects, why now, constraints, and what failure looks like. Summarize and ask the user to confirm. **STOP and wait for confirmation.** Then proceed to **Generate PRD**.

---

## Generate PRD

Use the structure and section order in **templates/PRD-template.md** (project root). Read that file when generating the PRD; if it is missing, ask the user to add the templates folder from this repo. Replace all `[placeholders]` with project- and feature-specific content. Omit or collapse sections that do not apply only if the user agrees.

Create a PRD that includes:

- Problem statement(s)
- Goals & non-goals
- Assumptions & risks
- Target audience / user personas
- User stories
- Functional requirements
- Non-functional requirements
- Dependencies & constraints
- Success metrics & measurement plan
- MVP definition and hypothesis being tested

Explicitly call out:

- Riskiest assumptions and how they will be validated
- What "learning success" looks like even if the feature fails

Before writing: identify any remaining gaps and ask follow-up questions if needed.

Write the PRD to the path the user specifies, or propose a path based on the project's doc structure (e.g. a specs or requirements directory and a clear filename) and confirm before writing.

---

## Output

- One PRD file (Markdown), saved to the agreed path.
- Short summary of key decisions and open risks.

---

## Confirmation Gate

After writing:

- Summarize key decisions and any open questions or risks.
- Ask: **"Is this PRD correct? Confirm to proceed, or tell me what to change."**

**STOP and wait for confirmation.** Do not proceed to another phase or skill until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 1 (PRD) is complete and return to the orchestrator.

## WRITE TO: .cursor/skills/spec-doc-generation/SKILL.md
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

## WRITE TO: templates/feature-template.md
# [Feature Name] — Feature Overview

[One to three sentences: what this feature is, who it's for, and the main value. Keep it problem-aligned.]

**Applies to:** [Routes, pages, or components — e.g. `/feature-path`, `ComponentName`.] *Related:* [Optional links to other feature pages, e.g. [Other feature](other-feature.md).]

---

## Features and documentation

Features that apply to this area, with links to spec and PRD docs where they exist.

| Feature | Applies to | Spec / PRD |
|--------|------------|------------|
| **[Sub-feature or capability name]** | [Where it applies] | [PRD](../productRequirementsDocs/[name]-prd.md) · [Spec](../specDocs/[name]-spec.md) |
| **[Another sub-feature]** | [Where it applies] | [Spec](../specDocs/[name]-spec.md) |

*(Add or remove rows. Not every capability may have a dedicated spec yet.)*

---

## How do I…?

*(Natural-language queries this page answers.)*

- **How do I [common task]?**  
  [Short answer and where to do it.] [Spec](../specDocs/[name]-spec.md) or [PRD](../productRequirementsDocs/[name]-prd.md).

- **How do I [another task]?**  
  [Short answer.] [Spec](../specDocs/[name]-spec.md).

*(Add more Q&A bullets as needed. Link to specDocs and productRequirementsDocs using relative paths above.)*

---

## Implementation reference

- **Architecture / data model:** [Link to plan or architecture doc if relevant.]
- **Related docs:** [Links to case studies, technical notes, etc., if relevant.]

*(Optional section; omit if not needed.)*

## WRITE TO: templates/PRD-template.md
# [Feature Name] — Product Requirements Document (PRD)

**Applies to:** [Product area(s), module(s), or platform(s) this feature affects.]

**Status:** [Draft | In review | Approved | Implemented — and any scope note.]

Reference: [Spec Doc](./[feature-name]-spec.md) (summary, problems, features, user flows).

---

## Problem statement(s)

1. **[Problem 1 title]** — [One or two sentences: who has the problem, what they need, and what happens today without this feature.]
2. **[Problem 2 title]** — [Same structure as above.]
_Add or remove numbered items as needed._

---

## Goals & non-goals

### Goals

- [Goal 1: outcome or capability the feature will enable.]
- [Goal 2.]
- [Goal 3.]
_Use clear, outcome-focused bullets._

### Non-goals (this initiative)

- [Explicitly out of scope for this PRD — e.g. "X is future work" or "Y is covered by another spec."]
- [Another non-goal.]
_Reduces scope creep and sets expectations._

---

## Assumptions & risks

### Assumptions

| Assumption | Notes |
|------------|--------|
| [Assumption 1] | [How you'll validate or what it depends on.] |
| [Assumption 2] | [Notes.] |
_Add rows as needed._

### Risks

| Risk | Mitigation |
|------|------------|
| [Risk 1] | [How you'll mitigate.] |
| [Risk 2] | [Mitigation.] |
_Add rows as needed._

### Riskiest assumptions

1. **[Riskiest assumption 1.]**  
   **Validation:** [How you'll validate — usage, survey, interviews, etc.]  
   **Learning success if adoption is low (or assumption is wrong):** [What you'll learn and do next.]

2. **[Riskiest assumption 2.]**  
   **Validation:** [How you'll validate.]  
   **Learning success if insufficient:** [What you'll do with the signal.]

---

## User personas

- **[Persona 1 name] (primary)** — [Role and context. Need that this feature addresses.]
- **[Persona 2 name] (secondary)** — [Role and need.]
_Adjust primary/secondary as needed._

---

## User stories

1. **As a [persona],** I want to [action/capability] so that [outcome/benefit].
2. **As a [persona],** I want to [action/capability] so that [outcome/benefit].
_Numbered list; cover main flows and outcomes._

---

## Functional requirements

_Group by theme (e.g. data model, add/edit, delete, reports, persistence). Use consistent IDs (FR-1, FR-2, …)._

### [Theme 1 — e.g. Data model and core behavior]

- **FR-1** [Requirement statement — testable and unambiguous.]
- **FR-2** [Next requirement.]
- **FR-3** [Continue.]

### [Theme 2 — e.g. Add / create flow]

- **FR-4** [Requirement.]
- **FR-5** [Requirement.]

### [Theme 3 — e.g. Edit / delete / visibility]

- **FR-6** [Requirement.]

### [Theme 4 — e.g. Reports or export]

- **FR-7** [Requirement.]

### [Theme 5 — e.g. Persistence and scope]

- **FR-8** [Requirement.]

_Add or remove themes and FRs to match the feature. Ensure no duplicate FR numbers._

---

## Non-functional requirements

- **NFR-1** [Performance, scale, or latency expectation.]
- **NFR-2** [Consistency, accuracy, or quality expectation.]
- **NFR-3** [UX or accessibility alignment — e.g. "Patterns align with existing product conventions."]
_Add NFRs as needed._

---

## Dependencies & constraints

- **[Dependency or system 1]** — [How this feature depends on it or integrates.]
- **[Dependency or system 2]** — [Description.]
_List technical, product, or org dependencies and constraints._

---

## Success metrics & measurement plan

### Adoption

- **Usage:** [What you'll measure — e.g. sessions with feature, frequency of use, share of users.]
- **Measurement:** [How — instrumentation, events, optional survey.]

### Value

- **Outcome:** [e.g. Time saved, errors reduced, decisions improved.]
- **Measurement:** [How you'll measure value — before/after, survey, interviews.]

---

## MVP definition and hypothesis

**MVP scope (this iteration):** [Concise list of what's in scope: capabilities, platforms, and any explicit limits.]

**Hypothesis:** [One sentence: we believe that [users] will [behavior] so that [outcome].]

**Learning success if adoption is low:** [What would indicate we need to pivot — e.g. discoverability, different workflows, or more scope before further investment.]

---

## Open questions / risks (for validation)

- **[Open question 1]** — [Brief context or owner.]
- **[Open question 2]** — [Context.]
_List items that need validation or a decision before or during implementation._

## WRITE TO: templates/spec-template.md
# [Feature Name] — Spec Doc

**Applies to:** [Product area(s), module(s), or platform(s) this feature affects.]

**Status:** [Draft | In review | Approved | Implemented — and any scope note.]

## Product / feature summary

[One or two paragraphs: what the feature is, who it's for, and the main value. Keep it problem-aligned, not solution-led. Mention how it fits with existing product behavior if relevant.]

---

## Problems being solved

1. **[Problem 1 title]**  
   [Who has the problem and what they need. What they do today without this feature.]

2. **[Problem 2 title]**  
   [Same structure.]

_Add or remove numbered items as needed._

---

## Target audience

- **[Persona 1]** — [Role and how they use this feature; primary/secondary if useful.]
- **[Persona 2]** — [Role and use.]

---

## Key features and functionality (problem-aligned)

_Organize by feature area or capability. Use subsections and bullets so each problem maps to clear behavior._

### [Feature area 1]

- [Capability or behavior 1.]
- [Capability or behavior 2.]
- [Inputs, validation, and outcomes where relevant.]

### [Feature area 2]

- [Capability or behavior.]
- [Rules, constraints, or display behavior.]

### [Feature area 3]

- [Capability or behavior.]
- [Persistence, scope, or integration notes if relevant.]

_Continue with as many feature areas as needed. Keep language testable and unambiguous._

---

## Success metrics

### Adoption

- **Usage:** [What you'll measure — e.g. sessions using the feature, frequency, share of users.]
- **Report/export usage:** [If relevant — e.g. use of reports or exports that include this feature.]

### Value

- **Outcome:** [e.g. Time saved, fewer errors, better decisions.]
- **Signal:** [How you'll know — e.g. less reliance on workarounds, in-app completion of a task.]

---

## Out of scope for this spec

- **[Item 1]** — [Brief reason or "covered by [other spec]".]
- **[Item 2]** — [Brief reason.]
_Reduces scope creep and clarifies boundaries._

---

## Key decisions and assumptions

| Decision / assumption | Rationale |
|-----------------------|-----------|
| [Decision or assumption 1] | [Why this choice.] |
| [Decision or assumption 2] | [Rationale.] |
_Add rows as needed. Helps future readers and implementation._

---

---

# [Feature Name] — User Flows

_For each flow: state the user story, then use the table and add Gherkin and edge cases where they help._

## Flow 1: [Flow name — e.g. Add or create]

**User story:** As a [persona], I want to [action] so that [outcome].

| Step | Screen / state | User action | Result / navigation |
|------|----------------|-------------|---------------------|
| 1 | [Initial screen or state] | [What the user does] | [What happens; next screen or state.] |
| 2 | [Screen/state] | [User action] | [Result/navigation.] |
| 3 | [Screen/state] | [User action] | [Result/navigation.] |
_Add or remove rows. Keep steps concrete and testable._

**Gherkin (optional but recommended):**

- **GIVEN** [precondition]
- **WHEN** [user action]
- **THEN** [observable result]

**Edge cases:**  
- [Edge case 1 and expected behavior.]
- [Edge case 2 and expected behavior.]

---

## Flow 2: [Flow name — e.g. View, edit, or configure]

**User story:** As a [persona], I want to [action] so that [outcome].

| Step | Screen / state | User action | Result / navigation |
|------|----------------|-------------|---------------------|
| 1 | [Screen/state] | [Action] | [Result.] |
| 2 | [Screen/state] | [Action] | [Result.] |

**Gherkin:**  
- **GIVEN** … **WHEN** … **THEN** …

**Edge cases:**  
- [Relevant edge cases.]

---

## Flow 3: [Flow name — e.g. Delete or remove]

**User story:** As a [persona], I want to [action] so that [outcome].

| Step | Screen / state | User action | Result / navigation |
|------|----------------|-------------|---------------------|
| 1 | [Screen/state] | [Action] | [Result.] |
| 2 | [Screen/state] | [Action] | [Result.] |

**Gherkin:**  
- **GIVEN** … **WHEN** … **THEN** …

**Edge cases:**  
- [Relevant edge cases.]

---

_Add more flows as needed (e.g. report/export, settings, error/recovery)._

---

## Summary of flows

- **Flow 1:** [One-line description.]
- **Flow 2:** [One-line description.]
- **Flow 3:** [One-line description.]
_Quick reference so readers can see full coverage._

## WRITE TO: templates/DOC-STRUCTURE-SPEC.md
# Documentation folder structure — specification

This document defines a standard documentation layout for product and feature docs. Use it to scaffold a new docs folder or to keep an existing one consistent. All paths and content are generic so they can be reused in any repo.

---

## Folder tree

```
docs/
├── README.md                    # Entry point; links to productBrief, INDEX, features
├── productBrief.md              # Vision, measurements, where to dive deeper, features overview, service blueprint; links to audienceProfiles (no inline audience)
├── audienceProfiles.md          # Primary and secondary audience; jobs to be done
├── designDetails/               # Style guide / design system (for prototypes)
│   └── style-guide.md           # Placeholder or real style guide
├── features/                    # One markdown per high-level feature; each links to specDocs and productRequirementsDocs
│   └── (one .md per feature)
├── specDocs/                    # All spec documents only
│   └── (e.g. feature-name-spec.md)
├── productRequirementsDocs/     # All PRDs only
│   └── (e.g. feature-name-prd.md)
├── images/                      # Images referenced by other markdown
│   └── (.png, .jpg, etc.)
└── INDEX.md                     # Optional; catalog of docs with feature area, type, applies to
```

---

## Purpose of each file and folder

| Item | Purpose |
|------|---------|
| **README.md** | Entry point. Short; links to productBrief, audienceProfiles, features, specDocs, productRequirementsDocs, and INDEX. Do not duplicate long content here. |
| **productBrief.md** | Vision, success measurements, "where to dive deeper" (table linking to features and other docs), features overview, service blueprint. **Audience:** link to audienceProfiles.md; do not inline audience content. |
| **audienceProfiles.md** | Single source of truth for primary and secondary audience. For each persona: role, context, and **Jobs to be done** (bulleted list). Product brief and other docs link here. |
| **designDetails/** | Style guide and design system. Use for typography, spacing, colors, components so prototypes can match the product. Add files as needed (e.g. style-guide.md, design-tokens.md). |
| **features/** | One markdown file per high-level product feature. Each file describes the feature and links to the spec(s) and PRD(s) that define it. Use the structure in **feature-template.md** (in this repo's templates folder). |
| **specDocs/** | All spec documents only. Naming: e.g. `feature-name-spec.md`. No PRDs in this folder. |
| **productRequirementsDocs/** | All PRDs only. Naming: e.g. `feature-name-prd.md`. No specs in this folder. |
| **images/** | All images used in markdown (screenshots, diagrams). Reference from other docs as `images/filename.png`. |
| **INDEX.md** | Optional catalog: list every doc with feature area(s), type (Brief, Feature parent, PRD, Spec, etc.), and "Applies to" (routes/components). Helps retrieval and consistency checks. |

---

## Link conventions

- **Feature pages** (in `features/`) link to specs and PRDs using:
  - `../specDocs/[name]-spec.md`
  - `../productRequirementsDocs/[name]-prd.md`
- **productBrief.md** links to audience with: `[audienceProfiles.md](audienceProfiles.md)` or `[Audience](audienceProfiles.md)`.
- **Images** from markdown: `images/filename.png` (relative to `docs/`).
- **Cross-feature links** from inside `features/`: `[Other feature](other-feature.md)` (same folder).

---

## Stub content for scaffolding

Use these when creating the folder structure in a new repo. Replace placeholders with project-specific content.

### README.md

```markdown
# Documentation

Start with:

- [Product brief](productBrief.md) — vision, measurements, features overview, service blueprint
- [Audience profiles](audienceProfiles.md) — primary and secondary users, jobs to be done
- [Features](features/) — one page per high-level feature
- [Specs](specDocs/) — spec documents
- [PRDs](productRequirementsDocs/) — product requirements documents

Optional: [Doc index](INDEX.md) — full list of docs with feature area and type.
```

### productBrief.md

```markdown
# [Product Name] — Product Brief

[One sentence: what this document is and that it is the entry point for product and feature documentation.]

---

## Where to dive deeper

| Area | Description | Links |
|------|-------------|--------|
| **[Feature 1]** | [Short description] | [Feature overview](features/[feature-1].md) |
| **[Feature 2]** | [Short description] | [Feature overview](features/[feature-2].md) |
| **Specs & PRDs** | Product requirements and spec docs | [specDocs/](specDocs/) · [productRequirementsDocs/](productRequirementsDocs/) · [INDEX](INDEX.md) |

---

## Audience

See [audienceProfiles.md](audienceProfiles.md) for primary and secondary audience and jobs to be done.

---

# Vision

[Short-term and long-term vision bullets.]

---

# Measurements for success

[Success indicators, metrics, baselines. Optional.]

---

# Features overview

[Table or bullets summarizing main features; link to feature pages and specs where relevant.]

---

# Service blueprint

[Optional: user actions, frontend actions, backend actions, support processes.]

---

## Quick answers

[Optional: common questions with one-line answers and links to feature pages or specs.]
```

### audienceProfiles.md

```markdown
# Audience profiles

## Primary audience

* **[Persona 1 name]**

  [One or two sentences: role, context, and why they use the product.]

  * **Jobs to be done**
    * [Job 1]
    * [Job 2]

* **[Persona 2 name]**

  [Role and context.]

  * **Jobs to be done**
    * [Job 1]
    * [Job 2]

## Secondary audience

* **[Persona 3 name]**  
  [Role and context. Jobs to be done: …]

* **[Persona 4 name]**  
  [Role and context. Job to be done: …]
```

### designDetails/style-guide.md

```markdown
# Style guide

Use this when generating prototypes so they fit the product's look and feel.

## Typography

- **Fonts:** [Primary font], [secondary font]
- **Scales:** [Heading sizes, body, captions]

## Spacing

- **Grid / rhythm:** [e.g. 4px or 8px base unit]
- **Margins and padding:** [Conventions]

## Colors

- **Primary:** [Hex or token name]
- **Secondary / accent:** [Values]
- **Neutrals and semantic:** [Backgrounds, text, borders, success, error]

## Components

- [List key UI components and any naming or usage notes.]
```

---

## Feature-level template

Feature pages in `features/` follow the structure in **feature-template.md** (in this repo's templates folder). That template includes:

- Title: `# [Feature Name] — Feature Overview`
- Intro paragraph, **Applies to:**, *Related:* links
- `## Features and documentation` — table (Feature | Applies to | Spec / PRD)
- `## How do I…?` — Q&A bullets with links to specDocs/PRDs
- Optional: `## Implementation reference`

All links in feature pages use `../specDocs/` and `../productRequirementsDocs/`.

---

## INDEX.md (optional)

If the project uses an index, list each doc with:

- **Doc** (link)
- **Feature area(s)** (e.g. Feature A; Feature B)
- **Type** (Brief, Feature parent, PRD, Spec, Plan, Doc, etc.)
- **Applies to** (routes, components, or context)

This supports retrieval and consistency checks (e.g. comparing index rows to each spec's "Applies to" block).
