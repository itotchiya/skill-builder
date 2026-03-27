---
description: Refresh or update an existing skill with latest documentation
allowed-tools: ["Read", "Write", "Edit", "Bash", "WebFetch", "WebSearch", "mcp__Claude_in_Chrome__navigate", "mcp__Claude_in_Chrome__get_page_text", "mcp__Claude_in_Chrome__read_page", "mcp__Claude_in_Chrome__javascript_tool"]
argument-hint: "skill name or category/skill-name"
---

@${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/SKILL.md

Update an existing skill in your Agent-skills vault.

---

## STEP 0 — Detect Storage Mode

Run the same detection as the /build command:

1. Try to call an Obsidian MCP tool (`mcp__obsidian__list_files_in_vault` or similar)
   - **Succeeds** → Obsidian connected → ask: "Update skill in Obsidian vault or local folder?"
   - **Fails** → Use local folder

2. Read configured path if local:
```bash
CONFIGURED_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')
```

Set `SKILL_BASE = {chosen-path}/Agent-skills`

---

## STEP 1 — Find the Skill

If a skill name is in $ARGUMENTS, search for it:

**Local:** `find "$SKILL_BASE" -name "SKILL.md" | xargs grep -l "{skill-name}" 2>/dev/null`

**Obsidian:** Use `mcp__obsidian__search_vault` with the skill name

If multiple matches or no argument, show a list and ask which skill to update.

---

## STEP 2 — Read Existing Skill

Read the current SKILL.md and all files in its `references/` directory. Note:
- Current version (engineering skills)
- Sources used
- Last updated date
- What's currently covered and what's missing

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
Edit existing files or create new reference files.

**Correction:**
Edit the relevant file. Add `> Updated: {date} — {what changed}` note.

**Full rebuild:**
Archive old folder as `{skill-name}-archived-{date}/`, then follow the full /build process.

**Storage method:** use Obsidian MCP tools if in vault, Write tool if local.

---

## STEP 5 — Update Indexes

Update `_INDEX.md` for the category and root `INDEX.md` "Last Updated" timestamp.

---

## STEP 6 — Completion Report

```
✅ Skill Updated: [{skill-name}]
📋 Changes: {summary}
🗓️ Version: {old} → {new}
📄 Files modified: {list}
💾 Location: {SKILL_BASE}/{category}/{skill-name}/
```
