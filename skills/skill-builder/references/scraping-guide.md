# Documentation Scraping Guide

Step-by-step guide for scraping official documentation using Claude in Chrome. Use this when building engineering or technical skills that require comprehensive documentation coverage.

---

## When to Use Full Browser Scraping

Use Claude in Chrome (not WebFetch) when:
- Documentation is rendered by JavaScript frameworks (React, Vue, Docusaurus, GitBook, Mintlify)
- Content is spread across many paginated pages
- Navigation requires clicking tabs, expanding sections, or switching versions
- The docs site requires login or has dynamic content loading

Use WebFetch when:
- Documentation is simple static HTML
- You only need one specific page
- The doc site explicitly allows crawling and renders content server-side

---

## Phase 1: Map the Documentation

Before extracting content, understand the full structure.

### Step 1: Open the documentation homepage
```
Navigate to: {docs-url}
```

### Step 2: Extract the navigation structure
Using `mcp__Claude_in_Chrome__get_page_text` or `mcp__Claude_in_Chrome__read_page`, extract all navigation links. Build a complete sitemap:

```
Section: Getting Started
  - Installation
  - Quick Start
  - Configuration

Section: Core Concepts
  - Architecture
  - Data Flow
  - ...

Section: API Reference
  - Functions
  - Hooks
  - Components
  - ...
```

### Step 3: Prioritize sections
Rank sections by importance for the skill being built:
1. **Must scrape:** Getting Started, Core API, Configuration, CLI Reference
2. **Should scrape:** Guides, Tutorials, Advanced Patterns, Troubleshooting
3. **Skip unless requested:** Blog, Community, Changelog (older versions), Legacy APIs

---

## Phase 2: Systematic Extraction

### Extracting a Single Page
```
1. Navigate to: {page-url}
2. Wait for content to fully load (check for loading spinners)
3. Use get_page_text to extract main content
4. Strip navigation, footers, ads — keep only documentation content
5. Note the page URL in your extraction notes
```

### Handling Pagination
For docs with Next/Previous navigation:
```
1. Start at the first page of a section
2. Extract content
3. Find the "Next" button or link
4. Navigate to it
5. Repeat until the section ends
```

### Handling Tabbed Content
For docs with tabbed examples (e.g., JS/TS/Python tabs):
```
1. Click each tab
2. Extract the content for each
3. In the skill reference file, label each block:
   # TypeScript
   {ts-code}

   # JavaScript
   {js-code}
```

### Handling Expandable Sections
For docs with accordion/collapsible content:
```
1. Use JavaScript tool to expand all sections:
   document.querySelectorAll('[aria-expanded="false"]').forEach(el => el.click())
2. Wait 500ms
3. Extract full page content
```

---

## Phase 3: Content Processing

### What to Extract Per Page

**For API reference pages:**
- Function/method signature
- Parameter names, types, defaults, required/optional status
- Return type and value
- Description (concise version — remove marketing language)
- Code example (the first complete example, or the best one)
- Any important notes or warnings

**For guide/tutorial pages:**
- Core concept being taught
- Code examples (complete, runnable)
- Configuration options mentioned
- Common pitfalls noted

**For CLI reference pages:**
- Command name and syntax
- All flags with types and defaults
- At least one usage example per command

### Content Cleanup Rules
- Remove navigation elements, breadcrumbs, "Was this helpful?" widgets
- Remove advertisement or sponsor content
- Convert HTML lists to Markdown lists
- Preserve code blocks exactly (whitespace matters in code)
- Keep warning and info callouts — mark them with `> ⚠️` or `> ℹ️`
- Keep version badges (note "Available since v{x.x}")

---

## Phase 4: Version Handling

Always capture version information:

```markdown
# {Technology} — v{X.Y.Z}

> **Version:** {X.Y.Z} (stable) | LTS: {X.Y.Z} | Released: {date}
> **Scraped:** {scraping-date}
> **Docs source:** {docs-url}
```

If the docs cover multiple versions:
1. Default to the current stable version
2. Note breaking changes between major versions in `references/migration.md`
3. Tag deprecated APIs with `[DEPRECATED in v{X}]`

---

## Phase 5: Quality Verification

After scraping, verify:

- [ ] All sections from the priority list were covered
- [ ] Every CLI command has at least one example
- [ ] Every major API function is documented
- [ ] Code examples are syntactically correct (no truncated snippets)
- [ ] Version number is captured in SKILL.md
- [ ] All internal links within the skill folder are relative and working
- [ ] No page had a 404 or redirect that was silently ignored

---

## Scraping Etiquette

- Do not scrape faster than needed — navigate page by page, not in parallel
- If a site returns a 429 (too many requests), wait and retry
- Do not bypass paywalls, login walls, or access restrictions
- If docs require authentication and you don't have credentials, document what's missing and note which sections were unavailable

---

## Reference: Common Documentation Platforms

| Platform | Notes |
|----------|-------|
| Docusaurus | JavaScript-rendered. Use Chrome. Navigation in left sidebar. |
| GitBook | JavaScript-rendered. Content often loads lazily on scroll. |
| Mintlify | JavaScript-rendered. Check for version selector dropdown. |
| VitePress | JavaScript-rendered. Good sitemap available at /sitemap.xml |
| ReadTheDocs | Server-rendered HTML. WebFetch usually works. |
| Sphinx | Server-rendered. Check for genindex.html for full coverage. |
| JSDoc / TypeDoc | Server-rendered. Good module index page. |
| Storybook | Component explorer — use Chrome, click each story. |
| Swagger / OpenAPI | Use get_page_text on /openapi.json or /swagger.json for full spec. |

---

## Handling Incomplete Scraping

If you cannot fully scrape all documentation (time constraints, access issues, complex navigation):

1. Document what was covered in the skill's SKILL.md
2. Add an "Incomplete Coverage" section:
   ```markdown
   ## ⚠️ Coverage Notes
   The following sections were not fully scraped and may need manual review:
   - Advanced Enterprise Features (requires login)
   - Plugin API (large section — partial coverage only)
   ```
3. Add source links so the LLM can fetch more detail when needed:
   ```markdown
   For complete coverage, see: {docs-url}/{section}
   ```
