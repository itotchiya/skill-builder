---
description: Browse skills in your AI Skill Builder vault
allowed-tools: Read, Bash
argument-hint: "category name or skill name"
---

Browse the AI Skill Builder skill vault. The vault is located at:

```bash
VAULT_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')
```

## If no argument provided:

Read `$VAULT_PATH/INDEX.md` and present a clean overview of all skill categories and their contents.

Format the output as a readable summary:
- Show each category with skill count
- List skill names with one-line descriptions (from their SKILL.md frontmatter or first paragraph)
- Show date each skill was last updated (from file metadata if available)

If INDEX.md doesn't exist, scan `$VAULT_PATH/` for category directories and their contents using Bash.

## If argument is a category name (e.g., "engineering", "design"):

Read `$VAULT_PATH/{category}/_INDEX.md` and list all skills in that category with descriptions.

## If argument is a skill name (e.g., "nextjs-15", "dark-dashboard"):

Find the skill folder matching the name, read its SKILL.md, and display:
- Skill name and description
- What the skill covers (key topics)
- File list (so the user knows what reference material exists)
- How to invoke it in an AI tool

## If the vault is empty or doesn't exist:

Inform the user that no skills have been built yet and suggest running `/build` to create the first skill.

## Usage Examples

```
/browse                     → show all categories and skills
/browse engineering         → list all engineering skills
/browse nextjs-15           → show details for the nextjs-15 skill
/browse design              → list all design skills
```
