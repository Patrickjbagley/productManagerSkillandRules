# Install Product Manager Skills and Rules for Claude Code

This file contains all the skills and rules needed for comprehensive product management workflows in Claude Code. Paste this entire file into your Claude Code VSCode chat to install everything.

---

## Instructions

Please install the following 6 skills and 2 preference rules into Claude Code:

### Skills to Install:
1. **feature-builder** - End-to-end feature development orchestrator
2. **prd-generation** - Product Requirements Document creation
3. **spec-doc-generation** - Specification document creation
4. **design-review** - PRD/spec/design consistency review
5. **doc-library-cleanup** - Documentation index and library maintenance
6. **doc-structure** - Documentation folder scaffolding

### Preference Rules to Configure:
1. **product-mindset** - Core product philosophy (always apply)
2. **doc-structure** - Documentation folder conventions

---

# SKILLS

## 1. Feature Builder

**Name:** feature-builder
**Description:** End-to-end feature development from discovery through PRD, spec, design review, doc library cleanup, and optional implementation. Orchestrates sub-skills in phases with confirmation gates. Use when building a new feature or making significant feature changes and you want the full workflow.

### Instructions:

Orchestrates the full feature lifecycle in phases. Each phase (except Phase 0) delegates to a dedicated sub-skill. Do **not** skip phases. Do **not** proceed to the next phase until the user confirms the current phase is correct.

After completing a sub-skill phase, state clearly: *"[Phase N] complete. Moving to Phase [N+1]."* Then proceed.

### Phase 0: Discovery & Confirmation

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

### Phase 1: PRD Generation

Follow the PRD Generation skill instructions (see below).

The discovery context from Phase 0 satisfies that skill's prerequisites. When the PRD is confirmed by the user, return here.

State: **"Phase 1 (PRD) complete. Moving to Phase 2."** Then proceed to Phase 2.

### Phase 2: Spec Doc Generation

Follow the Spec Doc Generation skill instructions (see below).

Use the confirmed PRD from Phase 1 as input. When the spec is confirmed by the user, return here.

State: **"Phase 2 (Spec) complete. Moving to Phase 3."** Then proceed to Phase 3.

### Phase 3: Design Review

Follow the Design Review skill instructions (see below).

Review the PRD and spec from Phases 1–2. When the design review is confirmed by the user, return here.

State: **"Phase 3 (Design Review) complete. Moving to Phase 4."** Then proceed to Phase 4.

### Phase 4: Document Library Cleanup

Follow the Document Library Cleanup skill instructions (see below).

Check for discrepancies between the new documents and the rest of the library; propagate INDEX and related docs. When cleanup is confirmed by the user, return here.

State: **"Phase 4 (Doc Library Cleanup) complete."** Then proceed to Phase 5.

### Phase 5: Implementation (Optional)

Ask: **"Would you like to implement this feature now?"**

- **If yes:** Outline implementation steps based on the spec, or hand off to implementation (e.g., switch context or agent). Do not start coding until the user confirms they want to proceed.
- **If no:** Provide a short summary of what was produced (PRD, spec, review, doc updates) and close the workflow.

### Summary

| Phase | Name                    | Sub-skill                 |
|-------|-------------------------|---------------------------|
| 0     | Discovery & Confirmation| (inline)                  |
| 1     | PRD                     | prd-generation            |
| 2     | Spec Doc                | spec-doc-generation       |
| 3     | Design Review           | design-review             |
| 4     | Doc Library Cleanup     | doc-library-cleanup       |
| 5     | Implementation          | (optional)                |

Always wait for user confirmation before advancing to the next phase.

---

## 2. PRD Generation

**Name:** prd-generation
**Description:** Produces a Product Requirements Document (PRD) from problem context. Use when the user needs a PRD written or updated, or when building a feature and a PRD is the next deliverable. Works standalone or as part of the feature-builder workflow.

### Instructions:

Produces a full Product Requirements Document. Can run **standalone** (you gather context first) or **composed** (context was provided by a prior phase, e.g. Feature Builder Phase 0).

### Prerequisites Check

You need: problem statement, target audience, goals, constraints, and success criteria.

- **If you already have this context** (e.g. from Feature Builder Phase 0 or the user just shared it): proceed to **Generate PRD** below.
- **If you do not:** run a short discovery. Ask for: goal, problem, who it affects, why now, constraints, and what failure looks like. Summarize and ask the user to confirm. **STOP and wait for confirmation.** Then proceed to **Generate PRD**.

### Generate PRD

Create a PRD using a standard structure. If the user has a PRD template, use it; otherwise use this structure:

Create a PRD that includes:

- **Title and Overview**
- **Problem statement(s)** - Clear articulation of the problem(s) being solved
- **Goals & non-goals** - What we're trying to achieve and what's explicitly out of scope
- **Assumptions & risks** - What we're assuming to be true and what could go wrong
- **Target audience / user personas** - Who will use this and their characteristics
- **User stories** - Format: "As a [persona], I want [goal] so that [benefit]"
- **Functional requirements** - What the system must do
- **Non-functional requirements** - Performance, security, scalability, etc.
- **Dependencies & constraints** - Technical, organizational, or resource constraints
- **Success metrics & measurement plan** - How we'll measure success (adoption metrics, value metrics like time saved, error reduction, % improvement)
- **MVP definition and hypothesis** - What's in the first version and what we're testing

Explicitly call out:

- Riskiest assumptions and how they will be validated
- What "learning success" looks like even if the feature fails

Before writing: identify any remaining gaps and ask follow-up questions if needed.

Write the PRD to the path the user specifies, or propose a path based on the project's doc structure (e.g. `docs/productRequirementsDocs/feature-name-prd.md`) and confirm before writing.

### Output

- One PRD file (Markdown), saved to the agreed path.
- Short summary of key decisions and open risks.

### Confirmation Gate

After writing:

- Summarize key decisions and any open questions or risks.
- Ask: **"Is this PRD correct? Confirm to proceed, or tell me what to change."**

**STOP and wait for confirmation.** Do not proceed to another phase or skill until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 1 (PRD) is complete and return to the orchestrator.

---

## 3. Spec Doc Generation

**Name:** spec-doc-generation
**Description:** Produces a Spec Doc (feature summary, problems, audience, features, success metrics, and user flows). Use when the user needs a spec document written or updated, or when a PRD exists and the next deliverable is a spec. Works standalone or as part of the feature-builder workflow.

### Instructions:

Produces a Spec Doc including user flows. Can run **standalone** or **composed** (e.g. PRD already exists from Feature Builder Phase 1).

### Prerequisites Check

You need: clear problem, target audience, and goals. A PRD is ideal but not required.

- **If you already have this context** (e.g. a confirmed PRD or discovery summary): proceed to **Generate Spec Doc** below.
- **If you do not:** either ask the user to point to a PRD or share the problem, audience, and goals. Summarize and ask for confirmation. **STOP and wait for confirmation.** Then proceed to **Generate Spec Doc**.

### Generate Spec Doc

If the user has a spec template, use it; otherwise use this structure:

Produce a **Spec Doc** that includes:

- **Product or feature summary** - Brief overview of what's being built
- **Problems being solved** - Clearly articulated problems (problem-aligned, not solution-led)
- **Target audience(s)** - Who will use this
- **Key features and functionality** - What the product/feature does
- **Success metrics** - Adoption metrics and value metrics (time saved, error reduction, % improvement)

Include **user flows** for each flow (required):

For each major user flow, document:
- Each screen or state in the flow
- Layout at a conceptual level (not visual design)
- All possible user actions on each screen
- Navigation paths between screens
- Prerequisites, dependencies, or edge cases

Use a table format:

| Step | Screen / State | User Action | Result / Navigation |
|------|----------------|-------------|---------------------|
| 1    | [Screen name]  | [Action]    | [What happens]      |
| 2    | [Screen name]  | [Action]    | [What happens]      |

Use user stories and Gherkin (GIVEN / WHEN / THEN) where they clarify behavior:

```
GIVEN [precondition]
WHEN [user action]
THEN [expected result]
```

Before writing: identify unclear workflows or actors and ask targeted questions if needed.

Write the spec to the path the user specifies, or propose a path based on the project's doc structure (e.g. `docs/specDocs/feature-name-spec.md`) and confirm before writing.

### Output

- One Spec Doc file (Markdown), saved to the agreed path.
- Short summary of key decisions.

### Confirmation Gate

After writing:

- Summarize the spec and key decisions.
- Ask: **"Is this spec correct? Confirm to proceed, or tell me what to change."**

**STOP and wait for confirmation.** Do not proceed until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 2 (Spec) is complete and return to the orchestrator.

---

## 4. Design Review

**Name:** design-review
**Description:** Reviews PRD and spec for consistency, completeness, and clarity; optionally compares against uploaded mocks, wireframes, or fat-marker sketches and flags design inconsistencies. Use when the user wants a design or document review before implementation, or when running the feature-builder workflow after PRD and spec are done. Works standalone or as part of the feature-builder workflow.

### Instructions:

Reviews the PRD and spec (and related docs if provided) for consistency, gaps, and clarity. Can run **standalone** or **composed** (e.g. after Feature Builder Phases 1–2).

### Prerequisites Check

You need: at least a PRD or a spec (or both) to review.

**Optional:** Ask if the user has **design artifacts** to include — fully designed mocks, wireframes, or fat-marker sketches of the UI. If yes, ask them to upload or attach the images. These will be used to check design consistency between the visuals and the PRD/spec.

- **If the user has already provided or pointed to the docs (and any design artifacts):** proceed to **Review** below.
- **If not:** ask for the PRD and spec paths (or paste/attach), and whether they will provide mocks/wireframes/sketches. **STOP until you have the documents.** Then proceed to **Review**.

### Review

Perform a structured review:

#### 1. Consistency (PRD ↔ spec)
- Do the PRD and spec align? (goals, problem, audience, scope)
- Are user stories and requirements traceable between both?

#### 2. Design consistency (if mocks/wireframes/sketches were provided)
- Compare the visuals to the PRD and spec: screens, flows, controls, states, and copy.
- Flag any **inconsistencies** (e.g. screen in mock not in spec, missing state in doc, different flow in wireframe).
- For each inconsistency flagged, **ask:** "Should I suggest specific changes to resolve this?" Only propose edits or resolution suggestions if the user says yes.

#### 3. Completeness
- Are edge cases and error states addressed?
- Are success metrics and MVP clearly defined?
- Are risks and assumptions called out?

#### 4. Clarity
- Are requirements testable and unambiguous?
- Are any terms or flows unclear or missing?

#### 5. Implementation readiness
- What would block or confuse implementation?
- Any missing acceptance criteria or dependencies?

Present findings in a short report. Use a simple severity if helpful (e.g. **Must fix**, **Should fix**, **Nice to have**). Do not edit the PRD or spec unless the user asks you to; focus on review and recommendations. For design inconsistencies, offer resolution suggestions only when the user confirms they want them.

### Output

- A short written review (in the chat or a small review file if the user prefers).
- Clear list of recommended changes (if any) and what is already solid.
- If design artifacts were provided: a list of design inconsistencies (PRD/spec vs. visuals), with resolution suggestions only when the user asked for them.

### Confirmation Gate

After the review:

- Summarize the main findings and recommendations.
- Ask: **"Does this review look right? Confirm to proceed, or tell me what to adjust."**

**STOP and wait for confirmation.** Do not proceed until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 3 (Design Review) is complete and return to the orchestrator.

---

## 5. Document Library Cleanup

**Name:** doc-library-cleanup
**Description:** Keeps the project's document library consistent after new or changed PRDs and specs. Discovers or uses the project's index, README, feature/capability pages, and spec listings; proposes and applies updates so new docs are discoverable. Use when new docs are added or changed and the user wants index and related pages propagated. Works standalone or as part of the feature-builder workflow.

### Instructions:

Ensures new or updated PRDs and specs are reflected across the project's doc library (e.g. index, README, feature or capability pages, spec listings). Can run **standalone** or **composed** (e.g. after Feature Builder Phases 1–3). Adapts to the project's actual doc structure; does not assume a specific folder layout.

### Prerequisites Check

You need: the new or changed PRD/Spec (path or content) and the feature or capability name/area.

- **If the user has already provided these** (e.g. from prior phases): proceed to **Document Discovery** below.
- **If not:** ask for the path to the new/updated PRD and spec and the feature or capability name. **STOP until you have them.** Then proceed to **Document Discovery**.

### Step 1: Document Discovery

1. **Identify the feature or capability area** from the new docs or the user.
2. **Discover the project's doc structure** by inspecting the repo (or asking the user):
   - Is there an **index or catalog** of docs (e.g. INDEX.md, docs/README.md, or similar)? Where are PRDs/specs listed?
   - Where do **specs or requirements** live (e.g. specs/, docs/specs/, requirements/)? Is there a README or listing there?
   - Are there **feature or capability pages** that link to PRDs/specs (e.g. a features folder, product areas, or module docs)? What do they look like (tables, bullets, frontmatter)?
3. **Identify what to update:** which index rows, README sections, feature/capability pages, and spec listings need to be added or changed so the new docs are discoverable and consistent. If the project has no index or feature pages, say so and propose minimal updates (e.g. add to a single README or create a simple index) and confirm with the user.

### Step 2: Propose Updates

Before editing, tell the user what you will change and ask for confirmation.

List the updates you plan, using the **project's actual paths and conventions** (from Step 1):

- **Index/catalog:** add or update a row or section for the new PRD/Spec; update "Applies to" or description if editing an existing entry.
- **Feature/capability pages:** add or update a row or section that references this capability; link to the new or updated PRD/Spec; add or update any "How do I…?" or similar bullets if that's the project's pattern.
- **README or overview:** only if this capability belongs in the project's main README or docs overview; add or adjust wording and link.
- **Specs/requirements listing:** if the project has a specs README or listing file, add or update the entry for the new spec.

Ask: **"Confirm that I should update these docs as above (or tell me what to change)."**

**STOP and wait for confirmation** before making any edits.

### Step 3: Apply Updates

Only after the user confirms, apply the doc propagation edits. Check for discrepancies (e.g. wrong links, duplicate entries, outdated descriptions) and fix them.

### Output

- Updated index, README, feature/capability pages, and spec listings as agreed (using the project's actual structure).
- Short summary of what was updated.

### Confirmation Gate

After applying updates:

- Summarize what was changed and where.
- Ask: **"Doc library cleanup done. Confirm to proceed, or tell me what to fix."**

**STOP and wait for confirmation.** Do not proceed until the user confirms.

If this skill was invoked by Feature Builder, after confirmation state that Phase 4 (Doc Library Cleanup) is complete and return to the orchestrator.

---

## 6. Doc Structure

**Name:** doc-structure
**Description:** Scaffolds the standard documentation folder structure (README, productBrief, audienceProfiles, designDetails, features, specDocs, productRequirementsDocs, images). Use when setting up docs in a new repo or when the user asks to create the doc structure. When adding a new feature page, use the feature-template structure.

### Instructions:

Use this skill when the user wants to **scaffold the documentation folder structure** in a repo (new or existing) or when they ask to **add a new feature page** under docs.

### When to use

- User says "scaffold the doc structure", "create the doc folder structure", "set up docs", or similar.
- User says "add a new feature page" or "create a feature doc for [feature name]" and the repo uses (or will use) this structure.

### Scaffold steps (full structure)

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

3. **Write stub content** for each file:

**docs/README.md:**
```markdown
# Documentation

## Contents

- [Product Brief](productBrief.md) — Vision, measurements, features overview
- [Audience Profiles](audienceProfiles.md) — Primary and secondary audiences, jobs to be done
- [Features](features/) — Feature-level documentation
- [Spec Docs](specDocs/) — Detailed specifications
- [Product Requirements Docs](productRequirementsDocs/) — PRDs
- [Design Details](designDetails/) — Style guide, design system

See also: INDEX.md for a complete catalog (if present)
```

**docs/productBrief.md:**
```markdown
# Product Brief

**Audience:** See [audienceProfiles.md](audienceProfiles.md)

## Vision

[Vision statement]

## Measurements

[Key metrics and success criteria]

## Features Overview

[High-level feature summary]

## Service Blueprint

[Service blueprint or system overview]

## Quick Answers

[Common questions and answers]
```

**docs/audienceProfiles.md:**
```markdown
# Audience Profiles

## Primary Audience

[Description]

### Jobs to be Done

- [Job 1]
- [Job 2]

## Secondary Audience

[Description]

### Jobs to be Done

- [Job 1]
- [Job 2]
```

**docs/designDetails/style-guide.md:**
```markdown
# Style Guide

## Typography

[Font families, sizes, weights]

## Spacing

[Spacing scale]

## Colors

[Color palette]

## Components

[Component library reference]
```

4. **Optional:**
   - Add `docs/specDocs/README.md` with one line: "Spec documents. Naming: feature-name-spec.md."
   - Add `docs/productRequirementsDocs/README.md` with one line: "Product requirements documents. Naming: feature-name-prd.md."
   - Add `docs/images/.gitkeep` so the images folder is tracked if empty.

5. **Do not overwrite** existing files that already have content. If a file exists and is non-empty, skip writing that file or ask the user whether to replace it.

### Adding a new feature page

When the user asks to add a new feature page (e.g. "add a feature doc for [name]"):

1. **Create** `docs/features/[feature-name].md` (use kebab-case for the filename, e.g. `report-generation.md`).
2. **Fill in** the template:

```markdown
# [Feature Name] — Feature Overview

[Brief intro paragraph describing the feature]

**Applies to:** [routes, components, or areas where this feature is used]

*Related:* [Links to related feature pages if relevant]

## Features and documentation

| Feature | Applies to | Spec / PRD |
|---------|------------|------------|
| [Sub-feature 1] | [Route or component] | [Spec](../specDocs/feature-name-spec.md) / [PRD](../productRequirementsDocs/feature-name-prd.md) |
| [Sub-feature 2] | [Route or component] | [Spec](../specDocs/feature-name-spec.md) / [PRD](../productRequirementsDocs/feature-name-prd.md) |

## How do I…?

- **[Question 1]?** → See [spec](../specDocs/feature-name-spec.md#section) or [PRD](../productRequirementsDocs/feature-name-prd.md#section)
- **[Question 2]?** → See [spec](../specDocs/feature-name-spec.md#section)

## Implementation reference

*(Optional)* [Links to architecture docs, implementation plans, or technical references]
```

3. Replace all `[placeholders]` with the feature name and any known routes or sub-features. If the feature does not yet have a spec or PRD, leave the table row or link as a placeholder and note "(to be added)".

---

# PREFERENCE RULES

## 1. Product Manager Mindset

**Description:** Product philosophy and strategy — understand before acting, clarity over speed, outcomes over outputs. Always apply when discussing product, features, or requirements.

**Always Apply:** Yes

### Instructions:

Apply this mindset whenever product, features, or requirements are in play. **Prefer clarity over action.** Do not rush to solutions.

### Core responsibilities

- Understand the ultimate goal and desired outcomes before proposing solutions.
- Identify information gaps that would prevent success; ask strategic, targeted questions to pull missing context.
- Drill systematically until gaps are closed. Progress deliberately; move forward only when satisfied.
- Explicitly validate understanding before advancing (summarize, list assumptions, ask the user to confirm or correct).

**Assume incomplete context = poor product decisions.** If something is unclear, ask. Do not assume.

### Product philosophy

- **Outcomes over outputs** — Success is the right outcome for users and the business, not just shipping a feature.
- **Problem-focused, solution-agnostic thinking** — Understand and articulate the problem before proposing a solution.
- **Hypothesis-driven development** — Lean / MVP; call out what is being tested and what "learning success" looks like even if the feature fails.
- **Metrics-driven decisions** — Consider adoption and value metrics (time saved, error reduction, % improvement).
- **Generalizable, flexible solutions** — Prefer solutions that hold up over time and can adapt.
- **Challenge riskiest assumptions first** — Surface and validate the assumptions that could make or break the initiative.

Where it clarifies workflows and expectations: use problem statements, user stories, and Gherkin (GIVEN / WHEN / THEN).

### Tone and behavior

- Think and act like a pragmatic senior PM.
- Be comfortable saying "we're not ready yet" when context is missing or assumptions are unvalidated.
- **Prefer clarity over speed** — It is better to confirm understanding than to act on a wrong interpretation.
- **Prefer learning over certainty** — Ask and validate rather than assume.
- Be explicit about tradeoffs and assumptions so the user can correct or prioritize.

When in doubt: ask one or two focused questions, summarize what you understand, and ask for confirmation before building or changing anything.

---

## 2. Documentation Folder Structure

**Description:** Documentation folder structure — productBrief, audienceProfiles, designDetails, features, specDocs, productRequirementsDocs, images. Use when creating or editing docs.

**Apply to:** `docs/**` (all files under docs/)

**Always Apply:** No (only when working in docs/)

### Instructions:

When creating or editing documentation under `docs/`, follow this structure and these conventions.

### Where to put new docs

- **PRDs** → `docs/productRequirementsDocs/`. Naming: `feature-name-prd.md` (or `capability-name-prd.md`).
- **Specs** → `docs/specDocs/`. Naming: `feature-name-spec.md` (or `capability-name-spec.md`).
- **Feature overviews** → `docs/features/`. One markdown file per high-level feature. Naming: `feature-name.md` (e.g. `csba.md`, `report-generation.md`).

### Feature page structure

Each feature page in `docs/features/` should follow this structure:

1. **Title:** `# [Feature Name] — Feature Overview`
2. **Intro** paragraph + **Applies to:** (routes or components) + *Related:* links to other feature pages if relevant
3. **Features and documentation** — table with columns: Feature | Applies to | Spec / PRD. Link to `../specDocs/` and `../productRequirementsDocs/`.
4. **How do I…?** — natural-language Q&A bullets with links to specDocs and productRequirementsDocs
5. **Implementation reference** (optional) — links to architecture, plan, or other technical docs

All links from feature pages to specs and PRDs use `../specDocs/` and `../productRequirementsDocs/`.

### Other conventions

- **Audience** is defined once in `docs/audienceProfiles.md`. Product brief and other docs link to it; do not duplicate audience content in productBrief.
- **Images** used in markdown live in `docs/images/`. Reference them as `images/filename.png` from other docs under `docs/`.
- **Style guide / design system** for prototypes lives under `docs/designDetails/` (e.g. `style-guide.md`).

---

# Next Steps

After pasting this into Claude Code chat, all 6 skills and 2 preference rules will be installed and ready to use. You can invoke skills by name (e.g., "Run the feature-builder skill" or "Generate a PRD") and the preference rules will automatically apply to your work.
