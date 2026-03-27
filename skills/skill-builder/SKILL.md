---
name: skill-builder
description: >
  This skill should be used when the user wants to "build a skill", "create a skill for [topic]",
  "add [topic] to my AI brain", "make a skill about [subject]", "generate knowledge for [domain]",
  "build a coding skill for [framework]", "create a design skill from screenshots",
  "build a marketing skill", "create a legal knowledge base", "generate a trading skill",
  or any request to create an AI-readable knowledge base for a technology, framework, design system,
  process, domain, or field of expertise. Also activates when the user runs /build, /browse,
  or /update commands from this plugin.
version: 0.1.0
---


# AI Skill Builder — Core Intelligence

> Generate domain-adaptive, self-contained skill folders that any LLM can read to gain expert-level knowledge on any topic — from Next.js API references to brand design systems to legal compliance frameworks.


---


## What This Skill Does

<!-- This section tells the AI what context it is operating in -->

This skill guides Claude through a 4-phase process to produce a high-quality, AI-readable knowledge base:

1. **Domain Detection** — identify the skill's domain and select the right expert agent persona
2. **Adaptive Scoping** — ask domain-specific questions to fully understand scope and intent
3. **Knowledge Acquisition** — scrape docs, process images, or synthesize expert knowledge
4. **Skill Generation** — produce a structured folder and save it to the isolated skill vault

**Before generating any file:** read `./references/md-blueprint.md` and apply its rules to every `.md` file created.


---


## Vault Architecture

<!-- The vault is completely isolated — no cross-links to other knowledge bases -->

All generated skills live in an isolated vault at `~~skill-vault`. This vault has no connections to any other AI brain or knowledge base — it is a standalone skill library.

```
~~skill-vault/
├── INDEX.md                        ← master navigation (all categories)
├── engineering/
│   ├── _INDEX.md                   ← category navigation
│   └── {skill-name}/
│       ├── SKILL.md                ← entry point (blueprint-compliant)
│       └── references/             ← deep content (loaded on demand)
├── design/
├── marketing/
├── legal/
├── finance/
├── sales/
├── product/
├── data/
└── custom/
```

Every skill is fully self-contained. Internal links use relative Markdown paths so any LLM can navigate the skill without a web connection.


---


## Phase 1 — Domain Detection

<instructions>

Identify the skill's domain from the user's request. Map to one of the canonical domains below. If the domain is ambiguous, ask the user to confirm before proceeding.

</instructions>

| Domain | Trigger Keywords | Vault Category |
|--------|-----------------|----------------|
| engineering | code, framework, library, API, SDK, CLI, database, cloud, DevOps, backend, frontend, mobile | `engineering/` |
| design | UI, UX, style guide, colors, fonts, components, layout, branding, Figma, screenshots | `design/` |
| marketing | campaigns, SEO, content, ads, email, social media, growth, copywriting | `marketing/` |
| legal | contracts, compliance, GDPR, regulations, NDA, privacy, IP, terms | `legal/` |
| finance | trading, markets, indicators, strategies, risk, accounting, crypto, DeFi | `finance/` |
| sales | outreach, sequences, objection handling, pipeline, CRM, prospecting | `sales/` |
| product | roadmap, user stories, requirements, PRDs, prioritization, OKRs | `product/` |
| data | analytics, SQL, metrics, pipelines, dashboards, BI, ML, data science | `data/` |
| custom | anything not matching above | `custom/` |


---


## Phase 2 — Agent Persona Selection and Announcement

<instructions>

Before asking any questions, select the matching expert agent persona from `./references/agent-personas.md` and announce it to the user:

```
🤖 Agent Activated: [Agent Name]
[One sentence: what this agent specializes in and why it's right for this skill.]
```

This gives the user full transparency. Wait for confirmation or redirection before proceeding.

</instructions>


---


## Phase 3 — Adaptive Scoping Questions

<rules>

- Load `./references/question-frameworks.md` and generate domain-specific questions
- Use the `AskUserQuestion` tool in batches of up to 4 questions
- Minimum 5 questions for any skill — no fixed maximum
- Questions must be specific to the skill being built, not generic
- Continue asking until scope, depth, exclusions, and use cases are fully defined
- If the user says "whatever you think is best," propose specific options and get explicit confirmation
- Do NOT proceed to Phase 4 until scoping is complete

</rules>


---


## Phase 4 — Knowledge Acquisition

<instructions>

Apply the acquisition strategy appropriate to the domain:

**Engineering / Technical**
Load `./references/scraping-guide.md`. Use Claude in Chrome to systematically scrape official documentation. Navigate all sections, follow all doc links, extract CLI commands, API signatures, configuration options, and code examples.

**Design**
Process provided images, Figma exports, or reference URLs. Extract exact hex color values, font stacks with sizes/weights, spacing tokens, component patterns, layout grids, and breakpoints.

**All other domains**
Use WebSearch and WebFetch to gather authoritative sources. Apply the activated agent persona to synthesize, structure, and validate the knowledge.

</instructions>


---


## Phase 5 — Skill Generation

<rules>

**Before creating any file:** read `./references/md-blueprint.md` — apply every rule in Part 1 to every `.md` file generated.

1. Load `./references/folder-templates.md` for the domain-appropriate structure
2. Load `./references/domain-profiles.md` for quality requirements and inclusion checklist
3. Get the vault path: `VAULT_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')`
4. Create the skill at: `$VAULT_PATH/{category}/{skill-name}/`

**Every generated file must:**
- Have complete YAML frontmatter (per blueprint R1)
- Have exactly one H1 followed by a one-liner blockquote (per blueprint R2, R4)
- Use relative Markdown links for all internal references (per blueprint R16, G)
- Stay under 3,000 words per file — split into sub-files if longer
- Use XML tags for rules, instructions, or scope blocks (per blueprint R8)
- Use HTML comments for AI-only processing hints (per blueprint R9)
- Use tables instead of nested bullets for structured data (per blueprint R10)
- Use code blocks with language tags (per blueprint R11)

**After saving:**
- Update `$VAULT_PATH/{category}/_INDEX.md` — add skill entry
- Update `$VAULT_PATH/INDEX.md` — update category count and "Recently Added"

</rules>


---


## Reference Files

| File | Purpose |
|------|---------|
| `./references/md-blueprint.md` | **Read before generating any .md file.** Rules and element catalog for AI-readable Markdown. |
| `./references/domain-profiles.md` | Per-domain inclusion checklists, structure guides, quality requirements |
| `./references/agent-personas.md` | Expert agent library: 12 divisions, 144+ personas, selection logic |
| `./references/question-frameworks.md` | Adaptive question sets by domain |
| `./references/folder-templates.md` | Folder structures with blueprint-compliant frontmatter per domain |
| `./references/scraping-guide.md` | Step-by-step Chrome scraping protocol for technical documentation |
