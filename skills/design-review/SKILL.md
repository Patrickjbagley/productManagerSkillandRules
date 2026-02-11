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
