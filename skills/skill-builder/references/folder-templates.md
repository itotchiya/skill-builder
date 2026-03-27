# Folder Templates

## `.agents` Vault Structure

The root vault structure is always:

```
{chosen-location}/
└── .agents/
    ├── SKILL.md                    ← master index of all skills (auto-updated after each build)
    └── skills/
        ├── {skill-name}/           ← one folder per skill, no category subfolders
        │   ├── SKILL.md            ← entry point for any AI tool
        │   └── references/         ← detailed content files
        ├── {another-skill}/
        │   ├── SKILL.md
        │   └── references/
        └── ...
```

**Rules:**
- `.agents/SKILL.md` is the master index — always update it after every build or update
- All skills live directly under `.agents/skills/` — no category subdirectories
- Each skill folder is self-contained and can be loaded independently by any AI tool

---

Folder structures for each domain type. Select the template matching the skill's domain. Adapt file names to match the specific skill content — these are starting points, not rigid rules.

**Naming rules:**
- All directory and file names: kebab-case (lowercase, hyphens, no spaces)
- Skill folder name should be: `{technology-or-topic-name}` (e.g., `nextjs-15`, `dark-dashboard-v2`, `gdpr-compliance`)
- Reference files should have self-documenting names (e.g., `api-reference.md`, not `ref1.md`)

---

## Engineering Template

### Small (focused library or tool)
```
{skill-name}/
├── SKILL.md                        ← overview, version, quick start, installation
└── references/
    ├── api-reference.md            ← all functions, methods, exports
    ├── configuration.md            ← config options with types and defaults
    ├── code-examples.md            ← 10+ real-world usage patterns
    └── troubleshooting.md          ← common errors and solutions
```

### Medium (framework with CLI)
```
{skill-name}/
├── SKILL.md                        ← overview, version, quick start, key concepts
└── references/
    ├── installation.md             ← all setup methods
    ├── cli-commands.md             ← full CLI reference with flags
    ├── configuration.md            ← all config files and options
    ├── api-reference.md            ← core API (main exports, hooks, components)
    ├── code-examples.md            ← 10+ patterns covering common use cases
    ├── typescript-types.md         ← type definitions and interfaces
    ├── deployment.md               ← production deployment guide
    └── troubleshooting.md          ← errors, performance, debugging
```

### Large (full platform or comprehensive framework)
```
{skill-name}/
├── SKILL.md                        ← overview, version, architecture, quick start
└── references/
    ├── installation.md
    ├── cli-commands.md
    ├── configuration.md
    ├── core-concepts.md            ← fundamental mental models
    ├── api-reference/              ← split into sub-files if >3000 words
    │   ├── overview.md
    │   ├── {module-1}.md
    │   └── {module-2}.md
    ├── code-examples/
    │   ├── getting-started.md
    │   ├── {feature-1}.md
    │   └── {feature-2}.md
    ├── typescript-types.md
    ├── integrations.md             ← third-party integrations
    ├── performance.md              ← optimization patterns
    ├── security.md                 ← security considerations
    ├── testing.md                  ← testing strategies and setup
    ├── deployment.md
    └── troubleshooting.md
```

### SKILL.md Frontmatter for Engineering

<!-- Blueprint-compliant frontmatter — R1 requires ALL keys below -->

```yaml
---
title: "{Technology} {Version} — Complete Reference"
description: "Comprehensive skill for {Technology} {version}: installation, CLI, API, configuration, and code patterns."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{technology}, {version}, {domain}, engineering]
audience: "developer, AI agent"
language: "en"
related_files:
  - "./references/installation.md"
  - "./references/cli-commands.md"
  - "./references/api-reference.md"
  - "./references/code-examples.md"
  - "./references/configuration.md"
ai_instructions: "This skill covers {Technology} {version}. Load the appropriate reference file based on the user's task. For code generation, start with code-examples.md. For configuration, start with configuration.md."
---
```

**Skill description field** (for the plugin skill name field, not frontmatter):
```
This skill should be used when working with {Technology}, building {use-cases},
configuring {key-config}, or troubleshooting {common-issues}.
Activate when the user mentions "{technology}", "/{cli-command}", or needs
help with {specific-patterns}.
```

---

## Design Template

### Brand / Style Guide
```
{brand-name}-style/
├── SKILL.md                        ← brand overview, primary palette, main fonts
└── references/
    ├── colors.md                   ← full color system with hex + usage rules
    ├── typography.md               ← font stack, size scale, weight rules
    ├── spacing-sizing.md           ← spacing scale, grid, max-widths, breakpoints
    ├── components.md               ← component inventory with variants/states
    ├── motion.md                   ← animation durations, easing, principles
    └── tokens.md                   ← all tokens as CSS variables + Tailwind config
```

### Design System (comprehensive)
```
{system-name}-design-system/
├── SKILL.md                        ← system overview, usage principles, quick ref
└── references/
    ├── colors.md
    ├── typography.md
    ├── spacing-sizing.md
    ├── grid-layout.md              ← column systems, gutters, containers
    ├── components/
    │   ├── overview.md             ← component list and usage guidance
    │   ├── {component-group}.md    ← e.g., forms.md, navigation.md, data-display.md
    ├── icons.md                    ← icon set, usage rules, sizing
    ├── motion.md
    ├── accessibility.md            ← WCAG requirements, color contrast ratios
    ├── dark-mode.md                ← dark mode token overrides
    └── tokens.md
```

### SKILL.md Frontmatter for Design

<!-- Blueprint-compliant frontmatter — R1 requires ALL keys below -->

```yaml
---
title: "{Brand/System Name} — Design System"
description: "Complete design system reference for {brand}: colors, typography, spacing, components, and token exports."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{brand}, design-system, ui, components, tokens]
audience: "designer, developer, AI agent"
language: "en"
related_files:
  - "./references/colors.md"
  - "./references/typography.md"
  - "./references/spacing-sizing.md"
  - "./references/components.md"
  - "./references/tokens.md"
ai_instructions: "This skill contains a complete design system for {brand}. For color work, load colors.md. For component generation, load components.md. For CSS/Tailwind output, load tokens.md."
---
```

---

## Marketing Template

```
{brand-name}-marketing/
├── SKILL.md                        ← brand overview, primary audience, key messages
└── references/
    ├── brand-voice.md              ← tone, style, dos and don'ts with examples
    ├── audience-personas.md        ← persona profiles (name, demographics, pains)
    ├── messaging-framework.md      ← value props, taglines, elevator pitches
    ├── content-templates/
    │   ├── email-templates.md
    │   ├── social-captions.md
    │   └── ad-copy.md
    ├── channel-strategy.md         ← per-channel guidelines and best practices
    ├── seo-keywords.md             ← keyword clusters and content mapping
    └── metrics.md                  ← KPIs and measurement framework
```

---

## Legal Template

```
{regulation-or-domain}/
├── SKILL.md                        ← overview, scope, applicability, key obligations
└── references/
    ├── definitions.md              ← key terms in plain language
    ├── compliance-checklist.md     ← actionable steps with priorities
    ├── templates/
    │   └── {document-type}.md      ← e.g., dpa-template.md, nda-template.md
    ├── red-flags.md                ← clauses and practices to avoid
    ├── jurisdiction-notes.md       ← territorial differences
    └── sources.md                  ← official texts, guidance, links
```

---

## Finance / Trading Template

```
{strategy-or-framework-name}/
├── SKILL.md                        ← strategy overview, instruments, timeframes
└── references/
    ├── strategy-rules.md           ← entry/exit conditions (precise and complete)
    ├── indicators.md               ← all indicators: name, parameters, interpretation
    ├── risk-management.md          ← sizing rules, stops, max drawdown, limits
    ├── examples.md                 ← 5+ annotated real or simulated trade examples
    ├── market-conditions.md        ← when to use / when to avoid
    └── performance-metrics.md      ← backtest results, expected KPIs
```

---

## Sales Template

```
{product-or-process-name}-sales/
├── SKILL.md                        ← ICP, sales process stages, quick reference
└── references/
    ├── icp-profile.md              ← ideal customer profile in detail
    ├── outreach-sequences.md       ← multi-touch templates by channel
    ├── discovery-questions.md      ← question bank by stage
    ├── objection-handling.md       ← objection/response pairs
    ├── battlecards.md              ← competitive positioning
    └── proposal-framework.md       ← pitch structure, ROI calculator logic
```

---

## Product Template

```
{methodology-or-product-name}/
├── SKILL.md                        ← methodology overview, key templates, principles
└── references/
    ├── user-stories.md             ← format, acceptance criteria, examples
    ├── prioritization.md           ← frameworks with worked examples
    ├── prd-template.md             ← full product requirements document structure
    ├── roadmap-structure.md        ← roadmap formats, planning cadence
    ├── metrics.md                  ← product KPIs and OKR framework
    └── ceremonies.md               ← meeting formats, agendas, rituals
```

---

## Data / Analytics Template

```
{domain-name}-analytics/
├── SKILL.md                        ← data domain overview, key entities, primary metrics
└── references/
    ├── schema.md                   ← tables, fields, types, relationships
    ├── metrics-library.md          ← metric definitions with formulas
    ├── sql-patterns.md             ← common queries and templates
    ├── pipeline-architecture.md    ← data flow, transformations, dependencies
    └── visualization-guide.md      ← chart types, standards, naming conventions
```

---

## Custom / General Template

```
{topic-name}/
├── SKILL.md                        ← topic overview, key concepts, scope
└── references/
    ├── core-knowledge.md           ← primary content
    ├── examples.md                 ← worked examples or case studies
    ├── quick-reference.md          ← cheat sheet / lookup table
    └── sources.md                  ← authoritative references and links
```

---

## Frontmatter Templates by Domain

<!-- Blueprint R1: every .md file in a generated skill must have complete frontmatter -->
<!-- Use these as the base for SKILL.md and all reference files in generated skills -->

### Marketing

```yaml
---
title: "{Brand} — Marketing Knowledge Base"
description: "Brand voice, audience personas, messaging framework, and content templates for {brand}."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{brand}, marketing, content, campaigns]
audience: "marketer, copywriter, AI agent"
language: "en"
ai_instructions: "Marketing skill for {brand}. Load brand-voice.md first to understand tone. Load content-templates.md for copy generation."
---
```

### Legal

```yaml
---
title: "{Regulation/Domain} — Legal Reference"
description: "Structured legal knowledge base for {regulation}: obligations, compliance checklist, templates, and red flags."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{regulation}, legal, compliance]
audience: "legal professional, compliance officer, AI agent"
language: "en"
priority: "high"
ai_instructions: "Legal skill for {regulation}. Always load compliance-checklist.md first for actionable obligations. Red flags are in red-flags.md."
---
```

### Finance / Trading

```yaml
---
title: "{Strategy Name} — Trading Strategy"
description: "Complete trading strategy reference: entry/exit rules, indicators, risk management, and annotated examples."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{strategy-name}, trading, finance, {instrument}]
audience: "trader, quant analyst, AI agent"
language: "en"
ai_instructions: "Trading strategy skill. Entry/exit rules are in strategy-rules.md. Never apply this strategy outside the market conditions documented in market-conditions.md."
---
```

### Sales

```yaml
---
title: "{Product} — Sales Playbook"
description: "Complete sales enablement for {product}: ICP, outreach sequences, objection handling, and discovery frameworks."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{product}, sales, outreach, enablement]
audience: "sales rep, account executive, AI agent"
language: "en"
ai_instructions: "Sales playbook for {product}. Start with icp-profile.md to understand the target. Outreach templates are in outreach-sequences.md."
---
```

### Product

```yaml
---
title: "{Methodology} — Product Framework"
description: "Product management framework and templates for {methodology}: user stories, PRD structure, prioritization, and OKRs."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{methodology}, product-management, roadmap, user-stories]
audience: "product manager, designer, AI agent"
language: "en"
ai_instructions: "Product skill. For writing user stories load user-stories.md. For PRD creation load prd-template.md. For prioritization load prioritization.md."
---
```

### Data / Analytics

```yaml
---
title: "{Domain} — Data Analytics Reference"
description: "Data reference for {domain}: schema, metric definitions, SQL patterns, and visualization standards."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{domain}, analytics, sql, metrics, data]
audience: "data analyst, data engineer, AI agent"
language: "en"
ai_instructions: "Data skill for {domain}. Schema and entity relationships are in schema.md. Metric formulas are in metrics-library.md. Query templates are in sql-patterns.md."
---
```

### Custom / General

```yaml
---
title: "{Topic} — Knowledge Base"
description: "AI-readable knowledge base for {topic}: core concepts, examples, quick reference, and authoritative sources."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{topic}, knowledge-base, custom]
audience: "AI agent, practitioner"
language: "en"
ai_instructions: "Knowledge base for {topic}. Core concepts are in core-knowledge.md. Examples are in examples.md. Quick lookup is in quick-reference.md."
---
```

### Reference File Frontmatter Template

<!-- Use this for every file inside references/ — adapt title, description, tags, and ai_instructions -->

```yaml
---
title: "{Skill Name} — {Reference File Topic}"
description: "Detailed reference for {specific-topic} within the {skill-name} skill."
version: "0.1.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "reference"
tags: [{skill-name}, {topic}, reference]
audience: "AI agent"
language: "en"
---
```


---


## Vault Index Files

### Root INDEX.md structure

<!-- Blueprint-compliant: includes full frontmatter, one H1, one-liner blockquote -->

```markdown
---
title: "AI Skill Builder — Master Index"
description: "Navigation index for the isolated AI Skill Builder vault. Lists all skill categories and recently added skills."
version: "1.0.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "note"
tags: [index, vault, navigation]
audience: "AI agent"
ai_instructions: "This is the master navigation file. Read a category _INDEX.md to find skills in that domain. Never link outside this vault."
---

# AI Skill Builder — Master Index

> Isolated skill vault — standalone knowledge library with no connections to other AI brains or knowledge bases.

## Categories

| Category | Skills | Last Updated |
|----------|--------|-------------|
| [Engineering](./engineering/_INDEX.md) | {count} | {date} |
| [Design](./design/_INDEX.md) | {count} | {date} |
| [Marketing](./marketing/_INDEX.md) | {count} | {date} |
| [Legal](./legal/_INDEX.md) | {count} | {date} |
| [Finance](./finance/_INDEX.md) | {count} | {date} |
| [Sales](./sales/_INDEX.md) | {count} | {date} |
| [Product](./product/_INDEX.md) | {count} | {date} |
| [Data](./data/_INDEX.md) | {count} | {date} |
| [Custom](./custom/_INDEX.md) | {count} | {date} |

## Recently Added

| Skill | Category | Date |
|-------|----------|------|
| [{skill-name}](./{category}/{skill-name}/SKILL.md) | {category} | {date} |
```

### Category _INDEX.md structure

```markdown
---
title: "{Category} Skills — Index"
description: "Navigation index for all {category} skills in the AI Skill Builder vault."
version: "1.0.0"
author: "AI Skill Builder"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "active"
category: "note"
tags: [{category}, index, navigation]
audience: "AI agent"
---

# {Category} Skills

> All {category} skills in the AI Skill Builder vault, organized by topic.

| Skill | Description | Built | Last Updated |
|-------|-------------|-------|-------------|
| [{skill-name}](./{skill-name}/SKILL.md) | {one-line description} | {date} | {date} |
```
