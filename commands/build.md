---
description: Build a new AI skill from scratch
allowed-tools: ["Read", "Write", "Edit", "Bash", "WebFetch", "WebSearch", "mcp__Claude_in_Chrome__navigate", "mcp__Claude_in_Chrome__get_page_text", "mcp__Claude_in_Chrome__read_page", "mcp__Claude_in_Chrome__find", "mcp__Claude_in_Chrome__javascript_tool"]
argument-hint: "skill topic or name"
---

<!-- BOOTSTRAP: Load core intelligence and Markdown authoring rules before doing anything else -->

@${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/SKILL.md
@${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/md-blueprint.md

You are building a new AI skill. The topic is: $ARGUMENTS

If no topic was provided, ask the user what skill they want to build before proceeding.

---

## STEP 0 — Detect Storage Location

Before anything else, determine where the skill will be saved.

**Detection sequence — run in order:**

### Check 1: Is Obsidian MCP available?

Attempt to call an Obsidian MCP tool (try `mcp__obsidian__list_files_in_vault`, `mcp__obsidian__search_vault`, or any available `mcp__obsidian__*` tool with no parameters).

- **If it succeeds** → Obsidian is connected → go to **Option A**
- **If it fails or tool does not exist** → Obsidian not available → go to **Option B**

---

**Option A — Obsidian is connected:**

Ask the user:
> "Obsidian is connected. Where would you like to store this skill?"
> - **Obsidian vault** — saved inside your Obsidian vault under `.agents/skills/`
> - **Local folder** — saved to a folder on your computer under `.agents/skills/`

If they choose **Obsidian vault**:
- Ask Obsidian for the vault root path
- Set `AGENTS_ROOT = {vault-root}/.agents`
- Use Obsidian MCP tools to create all files

If they choose **Local folder**:
- Read the configured path: `cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]'`
- If path is default or doesn't exist, ask: "What folder should I save skills to?" (free text)
- Set `AGENTS_ROOT = {chosen-path}/.agents`
- Use Bash/Write tools to create files

---

**Option B — Obsidian not available:**

Read the configured path:
```bash
CONFIGURED_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')
```

If the path is the default placeholder or does not exist on disk, ask the user:
> "Where should I save this skill? (Enter a folder path)"

Set `AGENTS_ROOT = {chosen-or-configured-path}/.agents`
Use Bash/Write tools to create files.

---

**In all cases:**
- The agents folder is always named `.agents`
- Skills always go inside `.agents/skills/{skill-name}/`
- The master index is always at `.agents/SKILL.md`

Final skill path: `{AGENTS_ROOT}/skills/{skill-name}/`

Save the resolved `AGENTS_ROOT` path for use in all subsequent steps.

---

## STEP 1 — Domain Detection

Analyze "$ARGUMENTS" and identify the skill domain. Map to one of:
`engineering`, `design`, `marketing`, `legal`, `finance`, `sales`, `product`, `data`, `custom`

Use the domain mapping table in SKILL.md. If ambiguous, ask the user before proceeding.

---

## STEP 2 — Agent Activation

Read `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/agents/SKILL-BUILDER-AGENT-MAP.md`.

Find the best-fit agent for this domain and topic. Load the full agent file:
```
${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/agents/{division}/{agent-file}.md
```

Announce the activated agent:
```
🤖 Agent Activated: [Agent Name]
[One sentence: specialty and why it was chosen for this skill.]
```

Embody this agent's identity, methodology, and standards throughout the entire build. Wait for user confirmation or redirection.

---

## STEP 3 — Adaptive Scoping

Read `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/question-frameworks.md`.

Generate domain-specific questions tailored to this exact skill. Use `AskUserQuestion` in batches of up to 4. Continue until you have full clarity on:
- Scope (what to include, what to exclude)
- Required depth
- Source materials (docs URLs, images, files)
- Intended use cases and target AI tools

Do NOT proceed to Step 4 until scoping is complete.

---

## STEP 4 — Knowledge Acquisition

Based on domain and scoping answers:

**Engineering / Technical:**
Read `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/scraping-guide.md`.
Execute the full scraping protocol using Claude in Chrome browser tools.

**Design:**
Process provided images, URLs, or Figma references. Extract exact hex colors, typography with real values, component states, spacing tokens, CSS/Tailwind equivalents.

**All other domains:**
Use WebSearch and WebFetch. Apply the activated agent's methodology to synthesize knowledge from authoritative sources.

---

## STEP 5 — Skill Generation

Read before writing any file:
- `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/md-blueprint.md` ← **Markdown rules**
- `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/folder-templates.md` ← **Folder structure**
- `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/domain-profiles.md` ← **Quality checklist**

Create the skill at: `{AGENTS_ROOT}/skills/{skill-name}/`

**Ensure the `.agents/skills/` directory exists before writing:**
```bash
mkdir -p "{AGENTS_ROOT}/skills/{skill-name}/references"
```

**Storage method depends on where the user chose to save:**

If **Obsidian vault**: use `mcp__obsidian__create_or_update_file` for each file
If **Local folder**: use the Write tool for each file

Every `.md` file must be MD Blueprint compliant (R1–R16):
- Full YAML frontmatter on every file
- One H1 + one-liner blockquote
- XML tags for rules/instructions blocks
- Tables for structured data, not nested bullets
- Code blocks always have language tags
- All internal links use standard relative markdown: `[Label](./references/file.md)`
  → This format works in Obsidian, GitHub, VS Code, Cursor, and every other tool
  → Never use [[wikilinks]], absolute paths, or URLs for local file navigation

---

## STEP 6 — Update Master Index

After creating the skill, update the master index at `{AGENTS_ROOT}/SKILL.md`.

Create it if it doesn't exist. The format is:

```markdown
---
title: "Agent Skills Index"
description: "Master index of all AI skills in this .agents vault"
last_updated: "{date}"
total_skills: {count}
---

# Agent Skills Index

> All skills built by the Skill Builder plugin — load any skill by pointing your AI tool to its SKILL.md file.

## Skills

| Skill | Domain | Description | Last Updated |
|---|---|---|---|
| [nextjs-15](./skills/nextjs-15/SKILL.md) | engineering | Next.js 15 core concepts and patterns | 2026-03-27 |
| [skill-name](./skills/{skill-name}/SKILL.md) | {domain} | {one-line description} | {date} |
```

Add the new skill as a new row in the table. Update `last_updated` and `total_skills`.

---

## STEP 7 — Completion Report

```
✅ Skill Built: [{skill-name}]
📁 Location: {AGENTS_ROOT}/skills/{skill-name}/
💾 Stored in: {Obsidian vault | Local folder}
📄 Files: {count} — {list}
🤖 Agent: {agent-name}
📐 Format: MD Blueprint v2.0 compliant

To use in any AI tool:
"Load the {skill-name} skill from .agents"
→ {AGENTS_ROOT}/skills/{skill-name}/SKILL.md

Master index updated:
→ {AGENTS_ROOT}/SKILL.md
```
