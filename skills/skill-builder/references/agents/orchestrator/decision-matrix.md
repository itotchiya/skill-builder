---
type: decision-engine
title: "Agent Decision Matrix"
parent: "[[agents/orchestrator/ORCHESTRATOR.md]]"
last_updated: "2026-03-16"
---

# Agent Decision Matrix

> **FOR AI**: Use this when a user prompt maps to multiple possible agents. Score keywords, pick the highest-match division and agent. Multi-domain prompts → orchestrator.

## Table of Contents

- [Decision Flow](#decision-flow)
- [Keyword Routing](#keyword-routing)
- [Multi-Agent Triggers](#multi-agent-triggers)
- [Fallback Rules](#fallback-rules)

---

## Decision Flow

```
1. Parse prompt for: domain keywords + action verbs + deliverable type
2. Match against keyword routing table below
3. ONE clear match → division index → agent file → read related vault skills
4. MULTIPLE matches → activate ORCHESTRATOR → pick runbook or coordinate manually
5. NO match → check skills/workflow/ for process guidance, then generic approach
```

---

## Keyword Routing

| Keywords in Prompt | Division | Best Agent |
|-------------------|----------|-----------|
| architect, API, backend, microservice, scale, server | engineering | `backend-architect` |
| frontend, component, UI, interface, layout, React, Next.js | engineering | `frontend-developer` |
| mobile, iOS, Android, React Native, Expo | engineering | `mobile-app-builder` |
| deploy, CI/CD, pipeline, container, Docker, Kubernetes, infra | engineering | `devops-automator` |
| SRE, reliability, uptime, monitoring, on-call | engineering | `sre` |
| review, PR, pull request, code quality, refactor, lint | engineering | `code-reviewer` |
| security, vulnerability, OWASP, auth, pentest | engineering | `security-engineer` |
| AI, LLM, model, embeddings, RAG, agent, ML | engineering | `ai-engineer` |
| database, query, index, schema, ORM, migration | engineering | `database-optimizer` |
| incident, outage, down, rollback, production issue | engineering | `incident-response-commander` |
| SEO, search engine, ranking, keyword, organic | marketing | `seo-specialist` |
| growth, viral, funnel, conversion, A/B test, acquisition | marketing | `growth-hacker` |
| content, blog, article, editorial calendar | marketing | `content-creator` |
| social media, post, engagement, community | marketing | `social-media-strategist` |
| TikTok, short video, Douyin | marketing | `tiktok-strategist` |
| Instagram, Reels, visual platform | marketing | `instagram-curator` |
| LinkedIn, professional network, B2B content | marketing | `linkedin-content-creator` |
| Reddit, subreddit, community builder | marketing | `reddit-community-builder` |
| WeChat, Xiaohongshu, Bilibili, Zhihu, Weibo | marketing | `wechat-official-account` |
| brand, identity, logo, guidelines, visual language | design | `brand-guardian` |
| UI design, mockup, wireframe, component library | design | `ui-designer` |
| UX, user flow, journey map, usability | design | `ux-architect` |
| user research, persona, interview, usability test | design | `ux-researcher` |
| image prompt, Midjourney, DALL-E, visual AI | design | `image-prompt-engineer` |
| sales, outbound, prospecting, cold email, SDR | sales | `outbound-strategist` |
| deal, negotiation, pricing, proposal, close | sales | `deal-strategist` |
| QA, test, validate, bug, regression | testing | `reality-checker` |
| API test, endpoint, integration test, contract test | testing | `api-tester` |
| performance, load test, benchmark, latency | testing | `performance-benchmarker` |
| accessibility, a11y, WCAG, screen reader | testing | `accessibility-auditor` |
| product, roadmap, feature, backlog, prioritize | product | `manager` |
| sprint, planning, agile, story points | product | `sprint-prioritizer` |
| market research, trend, competitive analysis | product | `trend-researcher` |
| project, timeline, milestone, stakeholder, risk | project-management | `project-shepherd` |
| PPC, Google Ads, bid, ROAS, search campaign | paid-media | `ppc-strategist` |
| programmatic, DSP, display, audience targeting | paid-media | `programmatic-buyer` |
| support, ticket, customer issue, helpdesk | support | `support-responder` |
| analytics, dashboard, KPI, reporting | support | `analytics-reporter` |
| MCP, tool server, Claude tool, custom tool | specialized | `mcp-builder` |
| Salesforce, CRM architecture, Apex | specialized | `salesforce-architect` |
| blockchain, smart contract, Web3, audit | specialized | `blockchain-security-auditor` |
| compliance, GDPR, governance, audit | specialized | `compliance-auditor` |
| VR, AR, XR, spatial, visionOS, immersive | spatial-computing | `xr-interface-architect` |
| game, level, mechanic, Unity, Unreal, Godot | game-development | `game-designer` |
| history, historical, archaeology, primary source | academic | `historian` |
| psychology, cognitive, behavioral, mental | academic | `psychologist` |
| culture, anthropology, ethnography, social | academic | `anthropologist` |

---

## Multi-Agent Triggers

When you see these patterns → always use [[agents/orchestrator/ORCHESTRATOR.md]] + a runbook:

| Pattern | Runbook |
|---------|---------|
| "Build and launch..." / "from scratch to production" | [[agents/strategy/runbooks/startup-mvp.md]] |
| "Full stack feature" / "end-to-end implementation" | [[agents/strategy/runbooks/enterprise-feature.md]] |
| "Marketing campaign" / "go-to-market" | [[agents/strategy/runbooks/marketing-campaign.md]] |
| "Production incident" / "system is down" | [[agents/strategy/runbooks/incident-response.md]] |
| "Build + deploy + market" (3+ domains) | [[agents/strategy/nexus-strategy.md]] |

---

## Fallback Rules

1. If no keyword matches → check [[skills/workflow/SKILLS-WORKFLOW.md]] first
2. If multiple divisions match equally → pick ENGINEERING as default for technical tasks, MARKETING for growth tasks
3. If uncertain → tell the user you're using the orchestrator and explain which agents you're coordinating
4. Never activate more than 3 agents simultaneously without an explicit orchestrator session
