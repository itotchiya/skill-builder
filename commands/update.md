---
description: Refresh or update an existing skill with latest documentation
allowed-tools: ["Read", "Write", "Edit", "Bash", "WebFetch", "WebSearch", "mcp__Claude_in_Chrome__navigate", "mcp__Claude_in_Chrome__get_page_text", "mcp__Claude_in_Chrome__read_page", "mcp__Claude_in_Chrome__javascript_tool"]
argument-hint: "skill name"
---

@${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/SKILL.md

Update an existing skill in your `.agents` vault.

---

## STEP 0 — Detect Storage Mode

1. Try to call an Obsidian MCP tool (`mcp__obsidian__list_files_in_vault` or similar)
   - **Succeeds** → Obsidian connected → ask: "Update skill in Obsidian vault or local folder?"
   - **Fails** → Use local folder

2. Read configured path if local:
```bash
CONFIGURED_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')
```

Set `AGENTS_ROOT = {chosen-path}/.agents`
Skill path: `{AGENTS_ROOT}/skills/{skill-name}/`

---

## STEP 1 — Find the Skill

If a skill name is in $ARGUMENTS, search for it:

**Local:** `find "{AGENTS_ROOT}/skills" -maxdepth 2 -name "SKILL.md" | xargs grep -l "{skill-name}" 2>/dev/null`

**Obsidian:** Use `mcp__obsidian__search_vault` with the skill name

If no match or no argument provided, list all skills from `{AGENTS_ROOT}/SKILL.md` and ask the user which one to update.

---

## STEP 2 — Read Existing Skill

Read the current `{AGENTS_ROOT}/skills/{skill-name}/SKILL.md` and all files in its `references/` directory. Note:
- Current version
- Sources used
- Last updated date
- What's covered and what's missing

---

## STEP 3 — Determine Update Type

Ask the user what triggered this update:
- New version released
- Missing content found
- Incorrect content to fix
- Adding new topics
- Complete rebuild

---

## STEP 4 — Execute Update

**Version update (engineering):**
Read `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/scraping-guide.md`.
Check changelog first. Focus scraping on changed/new sections only.
Update version in SKILL.md. Add a "What changed in v{X}" section.

**Content addition:**
Fetch new content via Chrome or WebSearch.
Edit existing files or create new reference files in `references/`.

**Correction:**
Edit the relevant file. Add `> Updated: {date} — {what changed}` note.

**Full rebuild:**
Archive old folder as `{AGENTS_ROOT}/skills/{skill-name}-archived-{date}/`, then follow the full `/build` process.

**Storage method:** use Obsidian MCP tools if in vault, Write/Edit tools if local.

---

## STEP 5 — Update Master Index

Update `{AGENTS_ROOT}/SKILL.md` — refresh the skill's row with the new `last_updated` date and any description changes.

---

## STEP 6 — Completion Report

```
✅ Skill Updated: [{skill-name}]
📋 Changes: {summary}
🗓️ Version: {old} → {new}
📄 Files modified: {list}
💾 Location: {AGENTS_ROOT}/skills/{skill-name}/
```
