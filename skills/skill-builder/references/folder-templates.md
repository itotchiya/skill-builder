---
title: "Skill Builder — Adaptive Folder Templates"
description: "Principle-based guidance for structuring any skill folder. Not rigid templates — smart rules for determining what files a skill actually needs."
version: "2.0.0"
author: "Mustapha Boufous"
date_created: "2026-03-28"
last_updated: "2026-03-28"
status: "active"
category: "reference"
tags: [skill-builder, templates, folder-structure, adaptive]
audience: "AI agent"
---

# Skill Builder — Adaptive Folder Templates

> Structure is discovered, not assigned — read what the topic actually needs before deciding what files to create.

---

## `.agents` Vault Structure

The root vault structure is always:

```
{chosen-location}/
└── .agents/
    ├── SKILL.md                    ← master index (auto-updated after every build)
    └── skills/
        ├── {skill-name}/           ← one folder per skill, flat — no category subfolders
        │   ├── SKILL.md            ← entry point for any AI tool
        │   └── references/         ← supporting content files
        └── ...
```

**Rules:**
- `.agents/SKILL.md` is the master index — always update it after every build or update
- All skills live directly under `.agents/skills/` — no category subdirectories
- Each skill folder is fully self-contained — any AI can load it independently

---

## Adaptive Template Logic

<rules>
CRITICAL: Do NOT pick a folder template based on domain label alone.
Before creating any files, answer these 4 questions about the specific skill topic:

1. WHAT DOES AN AI NEED TO USE THIS EFFECTIVELY?
   → Only create files that contain knowledge an AI will actually reference

2. WHAT IS THE NATURAL SHAPE OF THIS CONTENT?
   → Some topics are lists (API methods), some are narratives (strategies), some are tables (rules/checklists)

3. HOW MUCH CONTENT IS THERE?
   → Small topic: 1–2 reference files. Large platform: 5–10 reference files. Never pad.

4. WHAT ARE THE MOST COMMON TASKS AN AI WILL DO WITH THIS?
   → Name files after those tasks (e.g., "objection-handling.md" not "content3.md")
</rules>

---

## File Decision Tree

Use this tree to determine which reference files to create. Work through it top-to-bottom.

```
Is this a technical library, framework, or tool?
├── YES → Does it have a CLI?
│   ├── YES → Include: installation.md, cli-commands.md, configuration.md, api-reference.md, code-examples.md, troubleshooting.md
│   └── NO  → Include: installation.md, api-reference.md, code-examples.md, configuration.md, troubleshooting.md
│         → If large API surface (>50 methods): split api-reference/ into sub-files by module
│
└── NO → Is this about HOW TO DO something (process/methodology/strategy)?
    ├── YES → Does it involve rules/criteria the AI must follow exactly?
    │   ├── YES → Include: rules.md or strategy.md (precise conditions), examples.md, quick-reference.md
    │   └── NO  → Include: overview.md or process.md, templates.md or frameworks.md, examples.md
    │
    └── NO → Is this about a BRAND or VISUAL IDENTITY?
        ├── YES → Include: colors.md (exact hex), typography.md (exact values), components.md, tokens.md
        │         → Add spacing.md, motion.md, accessibility.md only if scope requires it
        │
        └── NO → Is this about PEOPLE/AUDIENCE (sales, marketing, HR, comms)?
            ├── YES → Include: audience-profile.md or icp.md, messaging.md or templates.md, process.md or sequences.md
            │
            └── NO → Use custom shape:
                      → 1 main content file (core-knowledge.md or overview.md)
                      → Add examples.md if worked examples exist
                      → Add quick-reference.md if there are lookup tables or rules
                      → Add sources.md if citing authoritative external references
```

---

## Naming Rules

- All folder and file names: `kebab-case` (lowercase, hyphens, no spaces)
- Skill folder name = the topic slug: `nextjs-15`, `gdpr-compliance`, `cold-email-sequences`, `dark-dashboard-v2`
- File names must be self-documenting — anyone reading the folder list should know what each file contains
- Never use generic names: ~~`ref1.md`~~, ~~`content.md`~~, ~~`notes.md`~~

---

## Sizing Guidelines

| Skill Complexity | Files in references/ | When to Use |
|---|---|---|
| Micro | 1–2 files | Focused tool, single concept, narrow methodology |
| Small | 2–4 files | Standard library, brand guide, single process |
| Medium | 4–7 files | Framework with CLI, full methodology, product domain |
| Large | 7–12 files | Full platform, complex design system, multi-domain regulation |
| XL (split) | Use subfolders | Only when a single reference topic exceeds ~3000 words |

**Never create empty or near-empty files.** A file that is just a heading and 3 bullet points should be merged into another file.

---

## Domain Archetypes (Adaptive, Not Rigid)

These are starting points — always adapt based on what the specific topic actually needs.

### Technical (library / framework / tool)

```
{skill-name}/
├── SKILL.md                         ← version, quick start, what it does
└── references/
    ├── installation.md              ← all setup methods
    ├── cli-commands.md              ← only if it has a CLI
    ├── configuration.md             ← config options with types and defaults
    ├── api-reference.md             ← core API (split into subfiles if >3000 words)
    ├── code-examples.md             ← 10+ real-world usage patterns
    ├── typescript-types.md          ← only if TypeScript-first
    ├── integrations.md              ← only if integrations are a primary concern
    ├── performance.md               ← only if performance is a key concern
    ├── testing.md                   ← only if testing workflow is non-obvious
    ├── deployment.md                ← only if deployment is non-trivial
    └── troubleshooting.md           ← errors and fixes
```

### Design / Brand

```
{skill-name}/
├── SKILL.md                         ← brand overview, primary palette, headline font
└── references/
    ├── colors.md                    ← ALWAYS: every color with exact hex + usage rule
    ├── typography.md                ← ALWAYS: every font with exact values
    ├── spacing-sizing.md            ← grid, scale, breakpoints
    ├── components.md                ← component inventory with all states/variants
    ├── tokens.md                    ← CSS vars, Tailwind config, JSON output
    ├── motion.md                    ← only if animation/transition is defined
    ├── accessibility.md             ← only if WCAG or contrast ratios are documented
    └── dark-mode.md                 ← only if dark mode tokens are defined
```

### Strategy / Process / Methodology

```
{skill-name}/
├── SKILL.md                         ← what it is, when to use it, key principles
└── references/
    ├── {process-name}.md            ← the core rules/steps (be specific with name)
    ├── examples.md                  ← 5+ worked examples or case studies
    ├── templates.md                 ← reusable templates or frameworks
    ├── quick-reference.md           ← cheat sheet, decision table, rule summary
    └── sources.md                   ← if based on published methodology or regulation
```

### People / Audience (sales, marketing, HR, comms, support)

```
{skill-name}/
├── SKILL.md                         ← who this is for, key goal, primary context
└── references/
    ├── audience.md or icp.md        ← who, what they care about, their language
    ├── messaging.md                 ← value props, key messages, tone
    ├── templates.md or sequences.md ← actual copy templates, scripts, sequences
    ├── objections.md                ← only for sales/support: objection handling
    └── metrics.md                   ← only if measurement framework is part of the skill
```

### Knowledge Base / Domain Reference

```
{skill-name}/
├── SKILL.md                         ← scope, key concepts, who it applies to
└── references/
    ├── definitions.md               ← key terms in plain language
    ├── core-knowledge.md            ← the primary substantive content
    ├── examples.md                  ← worked examples or case studies
    ├── quick-reference.md           ← lookup table, rules checklist, decision tree
    └── sources.md                   ← authoritative links and citations
```

---

## SKILL.md — Universal Frontmatter

Every SKILL.md must have this frontmatter (MD Blueprint R1 compliant):

```yaml
---
title: "{Topic} — {What the AI gets from this skill}"
description: "One sentence: what this skill covers and what an AI can do with it."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{topic-slug}, {domain}, {key-concept}]
audience: "AI agent"
language: "en"
related_files:
  - "./references/{file1}.md"
  - "./references/{file2}.md"
ai_instructions: >
  {One or two sentences telling the AI exactly which reference file to load first
  for the most common tasks. Be specific about which file answers which question.}
---
```

**`ai_instructions` examples (adapt to actual skill):**
- `"For code generation start with code-examples.md. For config options use configuration.md. For errors use troubleshooting.md."`
- `"For color work load colors.md first. For component states load components.md. For Tailwind output use tokens.md."`
- `"Load strategy-rules.md first for entry/exit conditions. Never apply outside conditions in market-conditions.md."`
- `"Load audience.md first to understand the target. Templates are in sequences.md. Objections in objections.md."`

---

## Reference File Frontmatter

Every file inside `references/` must also have frontmatter:

```yaml
---
title: "{Skill Name} — {This File's Topic}"
description: "What this file contains and when to load it."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{skill-name}, {file-topic}]
audience: "AI agent"
language: "en"
---
```

---

## Master Index Format (`.agents/SKILL.md`)

```markdown
---
title: "Agent Skills Index"
description: "Master index of all AI skills in this .agents vault."
last_updated: "YYYY-MM-DD"
total_skills: {N}
---

# Agent Skills Index

> Load any skill by pointing your AI tool to its SKILL.md file.

| Skill | Domain | Description | Last Updated |
|---|---|---|---|
| [skill-name](./skills/skill-name/SKILL.md) | {domain} | {one-line description} | YYYY-MM-DD |
```
