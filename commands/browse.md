---
description: Browse skills in your .agents skill vault
allowed-tools: ["Read", "Bash"]
argument-hint: "skill name"
---

Browse the `.agents` skill vault.

```bash
CONFIGURED_PATH=$(cat "${CLAUDE_PLUGIN_ROOT}/config/vault-path.txt" | tr -d '[:space:]')
AGENTS_ROOT="${CONFIGURED_PATH}/.agents"
```

---

## If no argument provided:

Read `{AGENTS_ROOT}/SKILL.md` and present a clean overview of all skills.

Format the output as a readable table:
- Skill name (linked to its SKILL.md)
- Domain
- One-line description
- Last updated date

If `SKILL.md` doesn't exist at the root, scan `{AGENTS_ROOT}/skills/` for skill folders:
```bash
ls "{AGENTS_ROOT}/skills/"
```
Then read the SKILL.md frontmatter of each to build the overview.

---

## If argument is a skill name (e.g., "nextjs-15", "stripe-integration"):

Find the skill folder at `{AGENTS_ROOT}/skills/{argument}/`, read its SKILL.md, and display:
- Skill name and description
- What the skill covers (key topics)
- File list in the skill folder
- How to invoke it in any AI tool

---

## If the vault is empty or doesn't exist:

Inform the user that no skills have been built yet and suggest running `/build` to create the first skill.

---

## Usage Examples

```
/browse                     → show all skills in the vault
/browse nextjs-15           → show details for the nextjs-15 skill
/browse stripe-integration  → show details for stripe-integration skill
```
