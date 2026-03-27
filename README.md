<div align="center">

# 🧠 Skill Builder

**A Smart, Adaptive AI Skill Generator Plugin for Claude Cowork**

[![Version](https://img.shields.io/badge/version-0.1.0-blue?style=flat-square)](https://github.com/itotchiya/skill-builder)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)
[![Author](https://img.shields.io/badge/author-Mustapha%20Boufous-purple?style=flat-square)](https://github.com/itotchiya)
[![Platform](https://img.shields.io/badge/platform-Claude%20Cowork-orange?style=flat-square)](https://claude.ai)

*Build structured, self-contained knowledge bases from any documentation — readable by any AI on any tool.*

</div>

---

## ✨ What Is Skill Builder?

**Skill Builder** is a Cowork plugin that turns raw documentation, URLs, and expert knowledge into clean, structured **skill folders** that any LLM can read and load instantly.

Think of it as a knowledge factory: you point it at a topic, it asks the right questions, activates the right expert agent, scrapes or processes your references, and builds a complete, self-contained skill — ready for Claude, Cursor, Windsurf, or any other AI tool.

**Supported domains:** Engineering · Design · Marketing · Legal · Finance · Trading · Sales · Product · Data · and any custom domain.

---

## 🚀 Installation in Claude Cowork

### Step 1 — Download the plugin

Download the latest `.plugin` file from the [Releases](https://github.com/itotchiya/skill-builder/releases) page, **or** clone the repo:

```bash
git clone https://github.com/itotchiya/skill-builder.git
```

### Step 2 — Install in Cowork

1. Open **Claude Cowork** on your desktop
2. Click the **Plugins** icon in the sidebar (puzzle piece)
3. Click **"Install from file"**
4. Select the downloaded `skill-builder.plugin` file
5. Click **Install** — the plugin activates immediately

> **Alternative:** If you cloned the repo, point Cowork to the folder directly via **"Install from folder"**.

### Step 3 — Set your vault path *(optional)*

By default, skills are saved to `~/Agent-skills`. To change this, edit:

```
config/vault-path.txt
```

**Windows:**
```
C:\Users\YourName\Workspace\Agent-skills
```

**macOS / Linux:**
```
/Users/yourname/Documents/Agent-skills
```

> If you have **Obsidian MCP** connected, the plugin will automatically detect it and ask whether you want to save skills to your Obsidian vault or your local folder.

### Step 4 — Build your first skill

Type in Cowork chat:

```
/build Next.js 15
```

That's it. The plugin takes over from there.

---

## 🛠️ Commands

| Command | What it does |
|---|---|
| `/build [topic]` | Build a new skill from scratch with expert guidance |
| `/browse [category]` | Browse your skill vault by domain or search by name |
| `/update [skill name]` | Refresh an existing skill with new docs or version updates |

---

## 🔄 How It Works

When you run `/build`, the plugin follows a 4-phase process:

```
Phase 1 — DETECT     Identifies the domain, activates a matching expert agent persona
Phase 2 — SCOPE      Asks you 5–20 targeted questions to understand depth and focus
Phase 3 — GENERATE   Scrapes docs / processes references / builds structured content
Phase 4 — STORE      Saves the skill to your vault (Obsidian or local folder)
```

### Storage detection

Every time you build, the plugin checks:

1. **Is Obsidian MCP connected?** → Offers to save inside your Obsidian vault
2. **No Obsidian?** → Saves to your local `Agent-skills` folder

You always choose. Nothing is saved without confirmation.

---

## 🤖 Agent Personas

The plugin ships with **160+ specialized agent personas** across 16 domains. The right agent is automatically selected based on your topic:

| Domain | Example Agents |
|---|---|
| Engineering | Senior Developer, Software Architect, DevOps Automator |
| Design | UI Designer, UX Architect, Brand Guardian |
| Marketing | SEO Specialist, Content Creator, Growth Hacker |
| Sales | Deal Strategist, Outbound Specialist, Discovery Coach |
| Legal | Compliance Auditor, Contract Reviewer |
| Product | Product Manager, Trend Researcher, Sprint Prioritizer |
| + 10 more | Spatial Computing, Game Dev, Paid Media, Support, Testing... |

The active agent is always announced before questioning begins so you can redirect if needed.

---

## 📁 Vault Structure

All skills are saved in a clean, navigable structure:

```
Agent-skills/
├── INDEX.md                      ← master navigation
├── engineering/
│   ├── _INDEX.md
│   └── nextjs-15/
│       ├── SKILL.md              ← entry point for any AI tool
│       └── references/           ← deep-dive content
├── design/
├── marketing/
├── legal/
├── finance/
├── sales/
├── product/
├── data/
└── custom/
```

Once built, load any skill in any AI tool with:

```
"Load the nextjs-15 skill from my Agent-skills vault"
```

---

## 💡 Example Builds

```
/build Next.js 15
/build GDPR compliance for SaaS
/build dark dashboard design system
/build options trading strategy
/build cold email outreach sequences
/build React Query v5
/build Stripe integration
```

---

## 📋 Requirements

- **Claude Cowork** (desktop app, any version with plugin support)
- An active Claude account
- *(Optional)* Obsidian with the Local REST API plugin, connected via MCP

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first.

---

## 📄 License

MIT © [Mustapha Boufous](https://github.com/itotchiya)

---

<div align="center">

Made with ❤️ for the Claude Cowork community

**[⭐ Star this repo](https://github.com/itotchiya/skill-builder)** if it helps you build smarter AI workflows

</div>
