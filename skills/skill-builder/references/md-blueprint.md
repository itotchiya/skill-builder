---
title: "MD Blueprint — AI Markdown Authoring Instructions"
description: "Universal instruction set for any AI/LLM to produce clean, structured, and AI-readable markdown files. Not a fixed template — a set of rules, principles, and an element catalog."
version: "2.0.0"
author: "Mustapha Boufous"
date_created: "2026-03-26"
last_updated: "2026-03-26"
status: "active"
category: "guide"
tags: [markdown, blueprint, ai-instructions, llm, authoring]
audience: "AI agent, LLM"
language: "en"
ai_instructions: "Read this entire file before creating any .md document inside a skill folder. Apply every rule in Part 1 to every file you generate. Pick elements from the catalog based on the document's purpose. Do NOT copy this file's structure — build your own based on context."
---


# MD Blueprint — AI Markdown Authoring Instructions

> This is NOT a template to copy. It is an **instruction set**. Read the rules, understand the principles, pick the right elements from the catalog, and build a structure that fits the document you are creating.


---


## Part 1: Core Rules

<!-- THESE ARE NON-NEGOTIABLE — every .md file generated inside a skill folder must respect these -->

<rules>

**R1 — Frontmatter is mandatory.**
Every .md file must start with a YAML frontmatter block (`---`). At minimum include: `title`, `description`, `version`, `date_created`, `last_updated`, `status`, `category`, `tags`, and `audience`. Add more keys from the catalog (Part 3, Section A) when they add value. The frontmatter is the file's identity card — it lets any AI understand the file without reading the body.

**R2 — One H1 only.**
Every file gets exactly one `#` heading. It is the document title. Everything else uses `##` and below.

**R3 — Clean heading hierarchy.**
Never skip heading levels. `##` → `###` → `####`. Never jump from `##` to `####`. This is how AI models parse document structure — broken hierarchy breaks comprehension.

**R4 — One-liner after the H1.**
Immediately after the H1, include a single blockquote sentence that tells any reader (human or AI) what this document is and what it achieves. This is the first thing an AI reads after frontmatter — make it count.

**R5 — Front-load critical information.**
AI models weight the beginning of a document more heavily. Whatever matters most goes first. Purpose and context before details. Rules before examples. The reader should understand the "what" and "why" within the first 10 lines of body content.

**R6 — No fixed section list.**
Do NOT force the same sections on every file. Analyze what the document is about and build sections that serve its purpose. A technical spec needs different sections than a meeting note, a product roadmap, or a style guide. Let the content dictate the structure.

**R7 — No empty sections.**
If a section has no content, remove it entirely. An empty section is worse than no section — it signals missing information and confuses AI models.

**R8 — Use XML tags for critical boundaries.**
Wrap hard rules in `<rules>`, examples in `<examples>`, scope definitions in `<scope>`, and context blocks in `<context>`. AI models (especially Claude) treat these as semantic containers with clear start/end boundaries. Use them when precision matters, not everywhere.

**R9 — Use HTML comments for AI-only instructions.**
`<!-- text -->` is invisible in rendered markdown but AI can read it. Use it to embed processing hints, context notes, or implementation guidance that shouldn't clutter the visible document.

**R10 — Use tables for structured data, not bullet lists.**
When data has 2+ attributes per item (like name + description, or permission + role + scope), use a table. AI models parse tables with much higher accuracy than nested bullets.

**R11 — Use code blocks with language tags.**
Always specify the language identifier on fenced code blocks (` ```python `, ` ```json `, etc.). This tells AI exactly how to interpret the content inside.

**R12 — Bold means priority.**
Use `**bold**` sparingly and only for key terms or critical words. AI models interpret bold text as higher importance. Overuse destroys the signal.

**R13 — One idea per paragraph.**
Short, focused paragraphs. Each paragraph covers one concept. This is how AI tokenizes and retrieves information — mixed paragraphs cause blurry retrieval.

**R14 — Numbered sections when order matters.**
Use numbered headings (`## 1. Setup`, `## 2. Configuration`) only when sequence matters (guides, steps, specs with dependencies). For reference docs, knowledge bases, or notes where sections are independent, use descriptive headings without numbers.

**R15 — Consistent heading style.**
Pick a heading style and stick with it throughout the file. Either all sentence-case (`## How to configure the API`) or all title-case (`## API Configuration`). Never mix.

**R16 — File name is the first signal.**
The file name is the very first thing any AI, search tool, or human sees — before frontmatter, before content. It must be descriptive, scannable, and self-explanatory.

- Use **kebab-case**: `api-authentication.md`, not `API Auth.md`
- Lead with the **subject, not the type**: `api-authentication.md` not `guide-api-auth.md`
- Be **specific, not generic**: `prospect-soft-delete-rules.md` not `rules.md`
- Keep it **short but complete**: aim for 2–5 words
- No spaces, no special characters: only lowercase letters, hyphens, numbers
- Use a **date prefix only for time-based documents**: `2026-03-26-sprint-retro.md`
- **Group related files** with a shared prefix: `rbac-roles.md`, `rbac-permissions.md`

</rules>


---


## Part 2: How to Decide the Structure

<!-- THIS IS THE THINKING PROCESS — not a template, but a decision framework -->

<instructions>

Before writing any .md file, ask:

**Step 1 — What is this document?**
Identify the type: spec, guide, reference, report, plan, log, note. This determines which elements are useful.

**Step 2 — Who reads this?**
Identify the audience: developers, managers, AI agents, end users. This determines tone, depth, and which elements to include.

**Step 3 — What is the one thing the reader needs to walk away with?**
This becomes the one-liner after H1 and shapes the front-loading order.

**Step 4 — What are the natural divisions of this content?**
Let the content tell you its sections. Don't impose structure — discover it.

**Step 5 — Which elements from the catalog serve this document?**
Open Part 3 and pick what fits. A technical spec might need tables, code blocks, XML rule tags, and a glossary. A meeting note might only need headings, bullets, and callouts.

**Step 6 — Does this document need a changelog, references, or glossary?**
Only add these if the document will be versioned, links to external resources, or uses domain-specific terms.

</instructions>

### Decision table

| Document type | Likely structure |
|---------------|-----------------|
| Technical spec | Frontmatter → One-liner → Purpose → Context → Core rules (XML) → Sections with tables → Examples → Glossary |
| How-to guide | Frontmatter → One-liner → Prerequisites → Numbered steps → Code blocks → Troubleshooting → References |
| API reference | Frontmatter → One-liner → Authentication → Endpoints (tables) → Error codes → Rate limits → Examples |
| Knowledge base | Frontmatter → One-liner → Problem → Solution → Code examples → Related articles |
| Skill SKILL.md | Frontmatter → One-liner → What it does → Domain context → Key concepts → Quick reference table → Reference file links |
| Reference file | Frontmatter → One-liner → Main content organized by natural sections → Tables and code blocks as needed |


---


## Part 3: Element Catalog

> **This is a menu, not a checklist.** Pick what fits the document. Skip what doesn't.


---


### A. Frontmatter (YAML Metadata)

```yaml
---
title: "Document Title"
description: "One-line summary of what this document is and does"
version: "1.0.0"
author: "Name or Organization"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
status: "draft | active | review | deprecated | archived"
category: "guide | reference | spec | template | report | note | plan | log"
tags: [tag1, tag2, tag3]
audience: "developer | designer | manager | AI agent | LLM"
language: "en"
related_files: ["./other-file.md"]
ai_instructions: "Optional direct guidance for AI reading this file"
---
```

**All available frontmatter keys:**

| Key | Purpose | Example |
|-----|---------|---------|
| `title` | Document name | `"API Reference"` |
| `description` | One-line summary | `"All REST endpoints for v2"` |
| `version` | Semantic version | `"2.1.0"` |
| `author` | Creator | `"Mustapha Boufous"` |
| `date_created` | When created | `"2026-03-26"` |
| `last_updated` | Last edit | `"2026-03-26"` |
| `status` | Lifecycle state | `"active"` |
| `category` | Document type | `"reference"` |
| `tags` | Searchable labels | `[api, rest, v2]` |
| `audience` | Intended reader | `"developer"` |
| `language` | Content language | `"en"` |
| `priority` | Importance level | `"high"` |
| `related_files` | Linked documents | `["./auth.md"]` |
| `dependencies` | Required reading | `["./setup.md"]` |
| `license` | Usage terms | `"MIT"` |
| `ai_instructions` | Direct AI guidance | `"Use formal tone"` |


---


### B. Headings

```markdown
# H1 — Document Title (ONE per file, always)
## H2 — Major Sections
### H3 — Subsections
#### H4 — Sub-subsections
```


---


### C. Text Formatting

| Syntax | When to use | AI impact |
|--------|------------|-----------|
| `**Bold**` | Key terms, critical words | AI reads as high-priority |
| `*Italic*` | Emphasis, introducing terms | Moderate signal |
| `~~Strikethrough~~` | Deprecated content | AI may reduce weight |
| `` `Inline code` `` | Paths, variables, commands | AI treats as literal/technical |
| `> Blockquote` | Callouts, one-liner summaries | Draws attention |


---


### D. Lists

**Unordered — when order doesn't matter:**
```markdown
- Item one
- Item two
  - Nested item
```

**Ordered — when sequence matters:**
```markdown
1. First step
2. Second step
```

**Checklists — for tasks and tracking:**
```markdown
- [ ] Incomplete task
- [x] Completed task
```


---


### E. Tables

```markdown
| Column A | Column B | Column C |
|----------|----------|----------|
| Data     | Data     | Data     |
```

> **When to use:** Any time data has 2+ attributes per item. Always prefer tables over nested bullets for structured data.


---


### F. Code Blocks

Always use a language tag:

```markdown
```python
def hello():
    print("Hello")
```

```bash
npm install my-package
```

```json
{ "key": "value" }
```
```

**Common tags:** `python`, `javascript`, `typescript`, `json`, `yaml`, `bash`, `html`, `css`, `sql`, `go`, `rust`, `diff`, `plaintext`


---


### G. Links

```markdown
[Display Text](https://example.com)          <!-- external link -->
[Other Doc](./references/other.md)           <!-- relative link — always use relative -->
[Jump to Section](#section-heading)          <!-- anchor link -->
```

> **Always use relative links for internal skill file references.** Never hardcode absolute paths.


---


### H. Blockquote Callouts

```markdown
> **NOTE:** Important information the reader should not miss.
> **WARNING:** Could cause problems if ignored.
> **IMPORTANT:** Must be followed exactly.
> **TIP:** Helpful suggestion, not required.
> **DEPRECATED:** No longer supported — note the replacement.
```


---


### I. XML Semantic Tags

LLMs treat these as hard semantic boundaries. Use when precision matters.

```markdown
<context>
Background the AI needs before processing.
</context>

<rules>
Hard constraints that must be followed.
</rules>

<examples>
Concrete input/output demonstrations.
</examples>

<scope>
What is included and excluded.
</scope>

<instructions>
Step-by-step directions.
</instructions>

<output_format>
Exact format for the deliverable.
</output_format>

<constraints>
Limitations or things to avoid.
</constraints>

<persona>
Voice, tone, or role to adopt.
</persona>
```


---


### J. HTML Comments

```markdown
<!-- Invisible in rendered markdown, but AI CAN read this. -->
<!-- Use for: processing hints, AI context, instructions not meant for human readers -->
```


---


### K. Collapsible Sections

```markdown
<details>
<summary>Click to expand — optional verbose content</summary>

Hidden content here. Use for long examples or secondary reference material
that shouldn't clutter the main view.

</details>
```


---


### L. Footnotes

```markdown
This claim needs a source[^1].

[^1]: Source or explanation here.
```


---


### M. Math (LaTeX)

```markdown
Inline: $E = mc^2$

Block:
$$
\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n
$$
```


---


<!-- END OF MD BLUEPRINT v2.0 — Mustapha Boufous -->
