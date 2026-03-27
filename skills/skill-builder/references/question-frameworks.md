# Question Frameworks

Adaptive question sets for each domain. These are starting templates — generate additional specific questions based on what the user is requesting. Use `AskUserQuestion` in batches of up to 4 questions. Continue until you have a complete picture.

**Rule:** Never ask the same question twice. If the user's initial request already answers a question, skip it.

---

## Engineering / Technical Skills

### Batch 1 — Foundation
1. What technology, framework, or library is this skill for? (Include the specific version if relevant.)
2. What is your primary use case? (e.g., building a SaaS app, a CLI tool, data processing, etc.)
3. Should I scrape the full official documentation, or focus on specific sections?
4. Are there any areas you want to exclude? (e.g., legacy APIs, enterprise-only features, specific plugins)

### Batch 2 — Depth & Scope
1. How experienced are you with this technology? (Beginner / intermediate / advanced — affects how much foundational context to include)
2. Will this skill be used for greenfield projects, maintaining existing code, or both?
3. Are there specific patterns, architectures, or integrations you definitely need covered?
4. Should I include testing strategies and tools for this technology?

### Batch 3 — Format & Output
1. Which AI tools will primarily use this skill? (Cowork, Claude Code, Cursor, Kimi Code, OpenCode, etc.)
2. Should code examples use TypeScript, JavaScript, or both?
3. Do you need Docker / deployment configurations included?
4. Are there any community libraries or ecosystem tools that should be covered alongside the core framework?

### Follow-up Questions (ask if relevant)
- What versions do you need to support? (min/max)
- Do you use this with a specific cloud provider? (AWS, GCP, Azure, Vercel, etc.)
- Should authentication/authorization patterns be included?
- Is there a monorepo setup I should document?

---

## Design Skills

### Batch 1 — Source Materials
1. What are you providing as input? (Screenshots, Figma file exports, a live website URL, brand guidelines document, or a description?)
2. What is the name/context of this design system or brand? (e.g., "our SaaS product dashboard", "a fintech mobile app", "a luxury e-commerce brand")
3. What platforms will this design be used on? (Web, iOS, Android, all of the above?)
4. Do you have an existing color palette I should extract, or should I derive it from the images?

### Batch 2 — Components & Scope
1. Which component types are most important to document? (Navigation, forms, cards, modals, tables, charts, etc.)
2. Should the skill include dark mode / light mode variations?
3. Do you need responsive breakpoints and mobile-specific patterns?
4. Is there a specific design tool the consuming AI will generate code for? (Tailwind CSS, CSS-in-JS, plain CSS, Figma tokens, etc.)

### Batch 3 — Brand & Voice
1. Are there any strict brand rules to document? (Colors never to use, typography restrictions, logo clearspace, etc.)
2. Should I include UI copy and microcopy tone guidelines?
3. Are there any competitor brands whose styles you want to explicitly differentiate from?

---

## Marketing Skills

### Batch 1 — Brand & Audience
1. What product, service, or brand is this marketing skill for?
2. Who is the primary target audience? (Age range, profession, psychographic profile, pain points)
3. What channels does this brand primarily use? (Email, social, paid ads, SEO, content, etc.)
4. What is the brand voice? (Professional, casual, bold, educational, playful, etc.)

### Batch 2 — Goals & Content
1. What is the primary marketing goal? (Lead generation, brand awareness, sales conversion, retention, etc.)
2. Are there existing campaigns or content I should use as reference for tone and style?
3. What should be explicitly avoided? (Competitor names, certain claims, specific phrases)
4. Should I include SEO keyword frameworks?

### Batch 3 — Templates & Formats
1. Which content formats should the skill cover? (Email, LinkedIn posts, Twitter/X, blog posts, ad copy, landing pages, etc.)
2. Do you need campaign structure templates? (Funnel stages, naming conventions, UTM structures)
3. Should KPIs and measurement frameworks be included?

---

## Legal Skills

### Batch 1 — Regulation & Scope
1. Which specific regulation, law, or legal domain is this skill for? (e.g., GDPR, US employment law, SaaS contract templates, IP licensing)
2. Which jurisdiction(s) does this need to cover? (EU, US, UK, France, global, etc.)
3. What is the intended use? (Drafting documents, reviewing agreements, compliance audits, internal training)
4. Who will be applying this skill? (Lawyers, non-legal business users, both?)

### Batch 2 — Depth & Templates
1. Are there specific document types that must be covered? (NDAs, DPAs, Terms of Service, Employment contracts, etc.)
2. Should I include clause-by-clause analysis or just high-level summaries?
3. Do you need negotiation positions and fallback language?
4. Are there any regulatory deadlines or recent changes to the law that are particularly important?

---

## Finance / Trading Skills

### Batch 1 — Strategy & Instruments
1. What is the name or type of this trading strategy or financial framework?
2. Which financial instruments does it apply to? (Equities, crypto, forex, options, futures, indices)
3. Which timeframes? (Scalping/seconds, intraday/minutes, swing/days, position/weeks)
4. Is this a discretionary or algorithmic/rule-based strategy?

### Batch 2 — Rules & Risk
1. What are the core entry conditions? (Indicator signals, price action patterns, fundamental triggers)
2. What are the exit conditions? (Take profit targets, stop loss rules, time-based exits)
3. How is position sizing determined? (Fixed lot, % of account, Kelly criterion, volatility-adjusted)
4. What are the maximum drawdown and risk-per-trade limits?

### Batch 3 — Context & Validation
1. Have you backtested this strategy? If so, what platforms and what were the results?
2. What market conditions does this strategy work best in? (Trending, ranging, high volatility, low volatility)
3. Are there any known failure conditions or market environments to avoid?

---

## Sales Skills

### Batch 1 — Product & Market
1. What product or service is being sold?
2. What is the ICP (Ideal Customer Profile)? (Company size, industry, role/title of buyer, geography)
3. What is the average deal size and sales cycle length?
4. What is the primary value proposition in one sentence?

### Batch 2 — Process & Channels
1. What sales channels does the team use? (Cold email, LinkedIn, cold calling, inbound, partnerships, events)
2. What are the stages of your sales process? (e.g., Prospecting → Discovery → Demo → Proposal → Close)
3. What CRM is used, and what fields/stages need to be documented?
4. What are the 3-5 most common objections you encounter?

### Batch 3 — Content & Enablement
1. Should the skill include email sequence templates? If so, how many touches?
2. Do you need call scripts or talk tracks?
3. Should competitive battlecards be included? If so, who are the main competitors?
4. What resources do reps typically use during the sales process? (Case studies, ROI calculators, demos)

---

## Product Skills

### Batch 1 — Methodology & Context
1. What product methodology does the team use? (Agile/Scrum, Shape Up, Kanban, Dual Track, etc.)
2. What type of product is this for? (B2B SaaS, mobile app, marketplace, internal tool, API product)
3. Who are the primary stakeholders this skill needs to serve? (PMs, engineers, designers, executives)
4. Are you documenting an existing methodology or creating a new framework?

### Batch 2 — Templates & Frameworks
1. Which artifacts should the skill cover? (User stories, PRDs, roadmaps, OKRs, opportunity assessments, etc.)
2. What prioritization frameworks do you use? (RICE, MoSCoW, ICE, Impact/Effort, etc.)
3. Should the skill include sprint ceremonies and meeting formats?
4. Do you need stakeholder communication templates? (Status updates, executive briefings, etc.)

---

## Data / Analytics Skills

### Batch 1 — Domain & Stack
1. What data domain is this skill for? (E-commerce analytics, financial data, product analytics, marketing attribution, etc.)
2. What is the primary data warehouse or database? (BigQuery, Snowflake, PostgreSQL, Redshift, etc.)
3. What BI or analytics tools are used? (Looker, Tableau, Metabase, dbt, etc.)
4. What is the primary audience for this skill? (Data analysts, data engineers, business stakeholders, data scientists)

### Batch 2 — Metrics & Schema
1. What are the 5-10 most important business metrics this skill should define?
2. Should I include the underlying data schema and entity relationships?
3. Are there specific SQL query patterns or dbt model structures to document?
4. What data quality rules or SLAs should be encoded?

---

## Custom / General Skills

### Batch 1 — Definition
1. How would you describe this skill in one sentence?
2. What problem does an AI solve better when it has this skill?
3. Where does the source knowledge come from? (Existing documents, URLs, your own expertise, a combination)
4. Who is the primary user of this skill? (You, your team, a specific AI agent, the general public)

### Batch 2 — Scope & Depth
1. How deep should this skill go? (Quick reference cheat sheet / comprehensive knowledge base / something in between)
2. What should definitely be included?
3. What should definitely be excluded?
4. Are there any existing resources (URLs, files) I should use as primary sources?

### Batch 3 — Format & Use
1. In what context will this skill be invoked? (Specific task prompts, always loaded, on-demand)
2. Should the skill include worked examples or case studies?
3. Are there multiple sub-topics that should each get their own reference file?
