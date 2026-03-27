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

## STEP 0 — Detect Storage Mode

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
> - **Obsidian vault** — saved inside your Obsidian vault in the `Agent-skills` folder
> - **Local folder** — saved to a folder on your computer

If they choose **Obsidian vault**:
- Ask Obsidian for the vault root path
- Set `SKILL_BASE = {vault-root}/Agent-skills`
- Use Obsidian MCP tools to create all files

If they choose **Local folder**:
- Read the configured path: `cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]'`
- If path is default (`~/ai-skill-builder-vault`) or doesn't exist, ask: "What folder should I save skills to?" (free text)
- Set `SKILL_BASE = {chosen-path}/Agent-skills`
- Use Bash/Write tools to create files

---

**Option B — Obsidian not available:**

Read the configured path:
```bash
CONFIGURED_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')
```

If the path is the default placeholder or does not exist on disk, ask the user:
> "No Obsidian vault is connected. Where should I save this skill? (Enter a folder path)"

Set `SKILL_BASE = {chosen-or-configured-path}/Agent-skills`
Use Bash/Write tools to create files.

---

**In all cases, the skills folder is always named `Agent-skills`.**

Final skill path: `{SKILL_BASE}/{category}/{skill-name}/`

Save the resolved base path for use in all subsequent steps.

---

## STEP 1 — Domain Detection

Analyze "$ARGUMENTS" and identify the skill domain. Map to:
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

Create the skill at: `{SKILL_BASE}/{category}/{skill-name}/`

**Storage method depends on where the user chose to save:**

If **Obsidian vault**: use `mcp__obsidian__create_or_update_file` for each file
If **Local folder**: use the Write tool for each file

Every `.md` file must be MD Blueprint compliant (R1–R16):
- Full YAML frontmatter on every file
- One H1 + one-liner blockquote
- XML tags for rules/instructions blocks
- Tables for structured data, not nested bullets
- Code blocks always have language tags
- All internal links are relative paths

---

## STEP 6 — Update Agent-skills Index

After creating the skill:

**Update category index:** `{SKILL_BASE}/{category}/_INDEX.md`
Create if it doesn't exist. Add the new skill row.

**Update root index:** `{SKILL_BASE}/INDEX.md`
Create if it doesn't exist. Update category count and "Recently Added".

---

## STEP 7 — Completion Report

```
✅ Skill Built: [{skill-name}]
📁 Location: {SKILL_BASE}/{category}/{skill-name}/
💾 Stored in: {Obsidian vault | Local folder}
📄 Files: {count} — {list}
🤖 Agent: {agent-name}
📐 Format: MD Blueprint v2.0 compliant

To use in any AI tool:
"Load the {skill-name} skill from Agent-skills"
→ {SKILL_BASE}/{category}/{skill-name}/SKILL.md
```
