---
name: skill-builder-agent-map
description: Master lookup table mapping skill domains to the right agent persona file. Read this to select the correct agent before building any skill.
version: 0.1.0
---

# Skill Builder — Agent Map

> Fast-lookup table: given a skill domain or topic, find the exact agent file to load as the expert persona.

---

## How to Use This Map

1. Identify the skill domain from the user's request
2. Find the matching row below
3. Load the agent file at `./references/agents/{path}` relative to the plugin root
4. Announce the agent to the user before asking scoping questions

---

## Primary Domain → Agent Map

| Skill Domain | Best Agent | Agent File |
|-------------|-----------|-----------|
| React, Vue, Next.js, Svelte, frontend | Frontend Developer | `engineering/frontend-developer.md` |
| Node.js, Django, Rails, backend APIs | Backend Architect | `engineering/backend-architect.md` |
| iOS, Android, React Native, Flutter | Mobile App Builder | `engineering/mobile-app-builder.md` |
| AI/ML, LLM integration, embeddings | AI Engineer | `engineering/ai-engineer.md` |
| Docker, Kubernetes, CI/CD, cloud ops | DevOps Automator | `engineering/devops-automator.md` |
| SQL, PostgreSQL, MySQL, schema design | Database Optimizer | `engineering/database-optimizer.md` |
| ETL, pipelines, dbt, Spark, Airflow | Data Engineer | `engineering/data-engineer.md` |
| Security, auth, vulnerabilities | Security Engineer | `engineering/security-engineer.md` |
| Smart contracts, Solidity, DeFi | Solidity Smart Contract Engineer | `engineering/solidity-smart-contract-engineer.md` |
| SLOs, observability, incident response | SRE | `engineering/sre.md` |
| Architecture, system design, patterns | Software Architect | `engineering/software-architect.md` |
| General advanced coding | Senior Developer | `engineering/senior-developer.md` |
| Technical docs, API docs | Technical Writer | `engineering/technical-writer.md` |
| Code review, quality | Code Reviewer | `engineering/code-reviewer.md` |
| Rapid prototyping | Rapid Prototyper | `engineering/rapid-prototyper.md` |
| UI design, components, design systems | UI Designer | `design/ui-designer.md` |
| UX, user flows, usability | UX Architect | `design/ux-architect.md` |
| Brand identity, visual identity | Brand Guardian | `design/brand-guardian.md` |
| User research, usability testing | UX Researcher | `design/ux-researcher.md` |
| Image prompts, AI art | Image Prompt Engineer | `design/image-prompt-engineer.md` |
| Accessibility, inclusive design | Inclusive Visuals Specialist | `design/inclusive-visuals-specialist.md` |
| Visual storytelling | Visual Storyteller | `design/visual-storyteller.md` |
| SEO, search, organic | SEO Specialist | `marketing/seo-specialist.md` |
| Content, blog, long-form | Content Creator | `marketing/content-creator.md` |
| Growth, conversion, funnels | Growth Hacker | `marketing/growth-hacker.md` |
| Social media strategy | Social Media Strategist | `marketing/social-media-strategist.md` |
| TikTok | TikTok Strategist | `marketing/tiktok-strategist.md` |
| LinkedIn | LinkedIn Content Creator | `marketing/linkedin-content-creator.md` |
| Instagram | Instagram Curator | `marketing/instagram-curator.md` |
| Paid ads, PPC, Google Ads | PPC Strategist | `paid-media/ppc-strategist.md` |
| Paid social, Meta ads | Paid Social Strategist | `paid-media/paid-social-strategist.md` |
| Ad creative strategy | Creative Strategist | `paid-media/creative-strategist.md` |
| Performance marketing audit | Auditor | `paid-media/auditor.md` |
| Sales outreach, cold email | Outbound Strategist | `sales/outbound-strategist.md` |
| Discovery, demos, full-cycle sales | Sales Coach | `sales/coach.md` |
| Deal strategy, negotiation | Deal Strategist | `sales/deal-strategist.md` |
| Proposals, RFPs | Proposal Strategist | `sales/proposal-strategist.md` |
| Sales pipeline analysis | Pipeline Analyst | `sales/pipeline-analyst.md` |
| Product management, PRDs | Product Manager | `product/manager.md` |
| Sprint planning, prioritization | Sprint Prioritizer | `product/sprint-prioritizer.md` |
| User research, trends | Trend Researcher | `product/trend-researcher.md` |
| Legal compliance, GDPR, privacy | Legal Compliance Checker | `support/legal-compliance-checker.md` |
| Contracts, NDAs | Legal Compliance Checker | `support/legal-compliance-checker.md` |
| Finance tracking, budgets | Finance Tracker | `support/finance-tracker.md` |
| Data analytics, BI, dashboards | Analytics Reporter | `support/analytics-reporter.md` |
| Project management, roadmaps | Senior Project Manager | `project-management/project-manager-senior.md` |
| Jira, tickets, sprints | Jira Workflow Steward | `project-management/jira-workflow-steward.md` |
| Experiment tracking, A/B tests | Experiment Tracker | `project-management/experiment-tracker.md` |
| visionOS, XR, spatial | XR Interface Architect | `spatial-computing/xr-interface-architect.md` |
| Game design | Game Designer | `game-development/game-designer.md` |
| Level design | Level Designer | `game-development/level-designer.md` |
| Blockchain security audit | Blockchain Security Auditor | `specialized/blockchain-security-auditor.md` |
| MCP servers, tool building | MCP Builder | `specialized/mcp-builder.md` |
| Salesforce | Salesforce Architect | `specialized/salesforce-architect.md` |
| Supply chain | Supply Chain Strategist | `specialized/supply-chain-strategist.md` |
| Workflow automation | Workflow Architect | `specialized/workflow-architect.md` |
| Multi-agent orchestration | Agents Orchestrator | `orchestrator/ORCHESTRATOR.md` |
| Strategy, business planning | Nexus Strategy | `strategy/nexus-strategy.md` |
| Testing, QA | API Tester | `testing/api-tester.md` |
| Performance benchmarking | Performance Benchmarker | `testing/performance-benchmarker.md` |
| Accessibility audit | Accessibility Auditor | `testing/accessibility-auditor.md` |

---

## Fallback

If no agent matches precisely, use the **Senior Developer** for technical topics or the **Workflow Architect** for process/business topics.

For academic or research domains, see `academic/` — anthropologist, historian, geographer, psychologist, narratologist.

---

## Full Division Index

| Division | Folder | Count |
|---------|--------|-------|
| Engineering | `engineering/` | 20 agents |
| Design | `design/` | 8 agents |
| Marketing | `marketing/` | 17 agents |
| Paid Media | `paid-media/` | 7 agents |
| Sales | `sales/` | 8 agents |
| Product | `product/` | 5 agents |
| Project Management | `project-management/` | 6 agents |
| Support | `support/` | 6 agents |
| Specialized | `specialized/` | 17 agents |
| Strategy | `strategy/` | 10 files |
| Testing | `testing/` | 8 agents |
| Spatial Computing | `spatial-computing/` | 6 agents |
| Game Development | `game-development/` | 5 agents |
| Academic | `academic/` | 5 agents |
| Orchestrator | `orchestrator/` | 4 files |
