# AI Skill Builder

**Version:** 0.1.0 | **Author:** Mustapha Boufous | **License:** MIT

A domain-adaptive AI skill generator. Build structured, self-contained skill folders from documentation, design references, and expert knowledge — readable by any LLM on any AI tool.

---

## What It Does

The AI Skill Builder plugin generates complete knowledge bases (called "skills") that any AI model can load to gain expert-level understanding of any topic. Skills are organized in an isolated vault on your file system, with no connections to other knowledge bases.

**Supported domains:** Engineering, Design, Marketing, Legal, Finance, Trading, Sales, Product, Data Analytics, and any custom domain.

**Supported output tools:** Cowork, Claude Code, Cursor, Windsurf, Kimi Code, Codex, OpenCode, Antigravity, or any LLM that can read Markdown files.

---

## Components

### Commands

| Command | Description |
|---------|-------------|
| `/build [topic]` | Build a new skill from scratch. Asks domain-adaptive questions, activates an expert agent persona, scrapes documentation or processes references, and generates a structured skill folder. |
| `/browse [category or skill]` | Browse your skill vault by category or look up a specific skill. |
| `/update [skill name]` | Refresh an existing skill with new documentation, version updates, or additional content. |

### Skill

**`skill-builder`** — The core intelligence layer. Loads automatically when any command runs. Contains the full 4-phase build process, domain detection logic, agent persona selection, and output generation rules.

### Agent

**`skill-architect`** — Autonomous skill generation agent. Use when you want Claude to handle the full pipeline (scoping → scraping → building) with minimal interruption.

---

## Setup

### 1. Set your vault path

Edit `config/vault-path.txt` and replace the default path with where you want skills stored:

**Windows:**
```
C:\Users\YourName\Workspace\ai-brain-vault\AI Skill Builder
```

**macOS / Linux:**
```
/Users/yourname/Documents/ai-skill-builder
```

The vault will be created automatically when you build your first skill.

### 2. Install the plugin

Drop this folder into your AI tool's plugin directory or install via the `.plugin` file.

### 3. Build your first skill

```
/build Next.js 15
```

---

## Usage

### Building a new skill

```
/build Next.js 15
/build GDPR compliance
/build dark dashboard design system
/build options trading strategy
/build cold email outreach sequences
```

When you run `/build`, the plugin will:
1. Detect the domain and activate the matching expert agent
2. Ask you 5-20 targeted questions to scope the skill
3. Scrape documentation (for technical skills) or process your references
4. Generate a complete skill folder in your vault
5. Update the vault index

### Browsing your vault

```
/browse                     → overview of all categories
/browse engineering         → list engineering skills
/browse nextjs-15           → show skill details
```

### Updating a skill

```
/update nextjs-15           → refresh with latest Next.js docs
/update gdpr-compliance     → update with recent regulatory changes
```

### Using a skill in any AI tool

Once built, point any AI tool to the skill:

```
"Load the nextjs-15 skill from my AI Skill Builder vault"
```

Or reference the file directly:
```
{vault-path}/engineering/nextjs-15/SKILL.md
```

---

## Vault Structure

```
{your-vault-path}/
├── INDEX.md                        ← master navigation
├── engineering/
│   ├── _INDEX.md
│   └── {skill-name}/
│       ├── SKILL.md                ← entry point
│       └── references/             ← detailed content
├── design/
├── marketing/
├── legal/
├── finance/
├── sales/
├── product/
├── data/
└── custom/
```

---

## How Agent Personas Work

The plugin selects an expert agent persona based on the skill domain. This shapes how questions are asked, what depth is prioritized, and how the output is structured. The active agent is always announced before questioning begins so you can redirect if needed.

Agent personas are based on the [agency-agents](https://github.com/msitarzewski/agency-agents) framework — a collection of 144+ specialized AI agents across engineering, design, marketing, legal, finance, sales, product, and more.

---

## Customization

See `CONNECTORS.md` for configuration options.

The only required configuration is the vault path in `config/vault-path.txt`.

---

## References

- [agency-agents](https://github.com/msitarzewski/agency-agents) — agent persona library
- [skills.sh](https://skills.sh) — AI skill directory
- [Anthropic Skills](https://github.com/anthropics/skills) — official skill examples
- [Claude Skills Docs](https://code.claude.com/docs/en/skills) — skill format specification
