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
