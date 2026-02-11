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
