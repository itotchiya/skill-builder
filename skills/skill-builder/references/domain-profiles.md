# Domain Profiles

Per-domain inclusion checklists, folder structure guides, and quality requirements. Use this during Phase 4 and 5 of skill generation to ensure complete, high-quality output.

---

## Engineering / Technical Skills

**Goal:** Distill the entire official documentation so an LLM never needs to leave the skill folder to work effectively with this technology.

### What to Include
- Version information (current stable, LTS if applicable, changelog highlights)
- Installation and setup (all methods: npm/pip/brew/docker/manual)
- CLI commands (full reference: flags, arguments, examples)
- Configuration files (all valid options, types, defaults, examples)
- Core API reference (all exported functions, classes, hooks, components)
- TypeScript types and interfaces
- Code examples for common patterns (at least 10 real-world examples)
- Environment variables and secrets management
- Error messages and troubleshooting
- Performance optimization patterns
- Testing guidance
- External links (official docs, GitHub, community resources)

### What to Exclude (unless requested)
- Blog posts and marketing content
- Conference talks and videos
- Community forum discussions
- Deprecated APIs (note them, don't document in detail)

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← overview, quick start, version info
└── references/
    ├── installation.md         ← all setup methods
    ├── cli-commands.md         ← full CLI reference
    ├── configuration.md        ← all config options
    ├── api-reference.md        ← core API (split if >3000 words)
    ├── code-examples.md        ← 10+ real-world patterns
    ├── typescript-types.md     ← types and interfaces
    ├── troubleshooting.md      ← errors and fixes
    └── external-links.md       ← curated official resources
```

### Quality Checklist
- [ ] Version number prominently stated in SKILL.md
- [ ] Quick start (hello world) works from SKILL.md alone
- [ ] Every CLI command has at least one example
- [ ] All config options documented with type and default
- [ ] At least 10 code examples covering different use cases
- [ ] No broken relative links

---

## Design Skills

**Goal:** Create a complete design system reference that an LLM can use to generate pixel-perfect, on-brand UI without ever asking for the style guide again.

### What to Include
- Color palette (primary, secondary, accent, neutral, semantic colors — exact hex/rgb values)
- Typography (font families, size scale, weight options, line heights, letter spacing)
- Spacing system (base unit, scale, when to use each size)
- Sizing and layout (grid columns, gutters, max-widths, breakpoints)
- Component inventory (buttons, inputs, cards, modals, navigation — states, variants)
- Iconography (icon set name, style, sizing rules)
- Motion and animation (easing curves, duration values, when to animate)
- Dark/light mode variations (if applicable)
- Brand voice notes relevant to UI copy

### What to Exclude (unless requested)
- Raw asset files (reference them, don't embed)
- Logo usage guidelines (unless brand identity is the goal)
- Print/physical media guidelines

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← design overview, primary palette, typography
└── references/
    ├── colors.md               ← full color system with hex values
    ├── typography.md           ← font stack, size scale, usage rules
    ├── spacing-sizing.md       ← spacing scale, layout grid, breakpoints
    ├── components.md           ← component inventory with variants and states
    ├── motion.md               ← animation and transition guidelines
    └── tokens.md               ← all design tokens as variables (CSS/JSON/Tailwind)
```

### Quality Checklist
- [ ] Every color has an exact hex value (no "dark blue" — use #1A2B4C)
- [ ] Typography scale uses actual px/rem values
- [ ] At least one CSS/Tailwind token export per design element
- [ ] Component states documented (default, hover, active, disabled, focus)
- [ ] Responsive breakpoints listed with px values

---

## Marketing Skills

**Goal:** Give an LLM everything it needs to execute marketing work in this brand's voice, on this brand's channels, for this brand's audience.

### What to Include
- Brand voice and tone guidelines
- Target audience personas (demographics, psychographics, pain points, language they use)
- Channel strategy (which channels, what content types, posting frequency)
- Messaging frameworks (value propositions, taglines, elevator pitches)
- Content templates (email subject lines, social captions, ad copy formulas)
- SEO keyword clusters (if applicable)
- Campaign structure and naming conventions
- KPIs and success metrics
- Competitor positioning (what makes this brand different)

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← brand overview, primary audience, key messages
└── references/
    ├── brand-voice.md          ← tone, style, dos and don'ts
    ├── audience-personas.md    ← persona profiles
    ├── messaging-framework.md  ← value props, taglines, elevator pitches
    ├── content-templates.md    ← copy templates by channel and format
    ├── channel-strategy.md     ← channel-specific guidelines
    └── metrics.md              ← KPIs and measurement framework
```

---

## Legal Skills

**Goal:** Provide an LLM with structured legal knowledge to draft documents, review agreements, and navigate compliance without requiring external research for standard matters.

### What to Include
- Regulation summary (scope, who it applies to, key obligations)
- Key definitions (legal terms in plain language)
- Compliance checklist (action items, deadlines, responsibilities)
- Document templates (contracts, NDAs, notices, policies)
- Red flags (clauses or practices to avoid)
- Jurisdiction notes (where this law applies, notable differences)
- External authoritative sources (official texts, guidance documents)

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← regulation overview, applicability, key obligations
└── references/
    ├── definitions.md          ← key terms
    ├── compliance-checklist.md ← actionable steps
    ├── templates/              ← document templates
    ├── red-flags.md            ← what to watch for
    └── sources.md              ← official references and links
```

---

## Finance / Trading Skills

**Goal:** Encode a complete trading strategy, financial framework, or market knowledge base that an LLM can apply to analysis and decision support.

### What to Include
- Strategy definition (rules, conditions, entry/exit criteria)
- Indicators used (name, parameters, interpretation rules)
- Risk management rules (position sizing, stop loss, max drawdown)
- Backtesting criteria (timeframes, instruments, performance benchmarks)
- Market conditions where strategy applies (and where it doesn't)
- Example trades (annotated)
- Relevant metrics and formulas

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← strategy overview, instruments, timeframes
└── references/
    ├── strategy-rules.md       ← entry/exit conditions
    ├── indicators.md           ← all indicators with parameters
    ├── risk-management.md      ← sizing, stops, limits
    ├── examples.md             ← annotated trade examples
    └── performance-metrics.md  ← KPIs and measurement
```

---

## Sales Skills

**Goal:** Give an LLM everything it needs to operate as a high-performing sales professional in a specific context — from first touch to close.

### What to Include
- ICP (Ideal Customer Profile)
- Outreach sequences (email/LinkedIn/cold call scripts by stage)
- Discovery question frameworks
- Objection handling library (common objections + responses)
- Sales process stages and stage exit criteria
- Competitive battlecards
- Proposal and pitch frameworks
- CRM field definitions and stage mapping

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← ICP, sales process overview, quick reference
└── references/
    ├── outreach-sequences.md   ← templates by stage and channel
    ├── discovery-questions.md  ← question frameworks
    ├── objection-handling.md   ← objection/response pairs
    ├── battlecards.md          ← competitive positioning
    └── proposal-framework.md   ← pitch and proposal structure
```

---

## Product Skills

**Goal:** Encode a product methodology, framework, or domain so an LLM can write requirements, structure roadmaps, and facilitate product decisions.

### What to Include
- Methodology overview (agile, shape up, dual track, etc.)
- User story formats and acceptance criteria templates
- Prioritization frameworks (RICE, MoSCoW, Impact/Effort)
- PRD and spec templates
- Roadmap structure and planning cadence
- OKR/metric frameworks
- Decision-making frameworks (build/buy/partner, make/buy)

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← methodology overview, key templates
└── references/
    ├── user-stories.md         ← formats and examples
    ├── prioritization.md       ← frameworks with worked examples
    ├── prd-template.md         ← full PRD structure
    ├── roadmap-structure.md    ← roadmap formats and cadence
    └── metrics.md              ← product KPIs and OKR framework
```

---

## Data / Analytics Skills

**Goal:** Give an LLM a complete reference for working with a data domain — from schema understanding to analysis patterns to visualization standards.

### What to Include
- Data schema and entity relationships
- Key metrics (definitions, formulas, business context)
- SQL patterns and query templates
- Data pipeline architecture
- Dashboard and visualization standards
- Data quality rules and validation checks
- Glossary of domain-specific terms

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← data overview, key entities, primary metrics
└── references/
    ├── schema.md               ← tables, fields, relationships
    ├── metrics-library.md      ← metric definitions and formulas
    ├── sql-patterns.md         ← common queries and templates
    ├── pipeline-architecture.md← data flow and transformations
    └── visualization-guide.md  ← chart types, standards, examples
```

---

## Custom / General Skills

When a skill doesn't fit a canonical domain, use a flexible structure:

### Folder Structure
```
{skill-name}/
├── SKILL.md                    ← overview and key concepts
└── references/
    ├── core-knowledge.md       ← primary content
    ├── examples.md             ← worked examples
    ├── quick-reference.md      ← cheat sheet / lookup table
    └── sources.md              ← authoritative references
```

Apply the same quality principles: self-contained, relative links, no absolute paths, any LLM can navigate without external access.
