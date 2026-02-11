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
