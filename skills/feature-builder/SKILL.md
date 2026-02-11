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
