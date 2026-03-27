---
name: agent-personas
description: Domain-to-agent mapping guide. Read SKILL-BUILDER-AGENT-MAP.md first for the fast lookup table, then load the specific agent file for full persona details.
version: 0.1.0
---

# Agent Personas

> The Skill Builder has access to 160+ specialized agent personas across 16 divisions. Read `./agents/SKILL-BUILDER-AGENT-MAP.md` for the fast domain-to-agent lookup, then load the full agent file to embody the persona.

---

## How to Select and Load an Agent

### Step 1 — Fast Lookup

Read `${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/agents/SKILL-BUILDER-AGENT-MAP.md`

Find the row matching the skill domain or topic. Get the agent file path.

### Step 2 — Load Full Persona

Read the full agent file:
```
${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/agents/{division}/{agent-name}.md
```

### Step 3 — Embody the Agent

Adopt the agent's identity, methodology, technical standards, and communication style. Apply them throughout the entire skill build — from scoping questions to output quality criteria.

### Step 4 — Announce to User

```
🤖 Agent Activated: [Agent Name] — [Division]
[One sentence: what this agent specializes in and why it's the right choice.]
```

---

## Agent Library Overview

The full agent library is stored at:
```
${CLAUDE_PLUGIN_ROOT}/skills/skill-builder/references/agents/
```

| Division | Folder | Key Agents |
|---------|--------|-----------|
| Engineering | `engineering/` | frontend-developer, backend-architect, ai-engineer, devops-automator, security-engineer, software-architect, senior-developer, mobile-app-builder, database-optimizer, data-engineer, sre, solidity-smart-contract-engineer, technical-writer, code-reviewer |
| Design | `design/` | ui-designer, ux-architect, brand-guardian, ux-researcher, image-prompt-engineer, inclusive-visuals-specialist, visual-storyteller |
| Marketing | `marketing/` | seo-specialist, content-creator, growth-hacker, social-media-strategist, tiktok-strategist, linkedin-content-creator, instagram-curator, douyin-strategist |
| Paid Media | `paid-media/` | ppc-strategist, paid-social-strategist, creative-strategist, auditor, programmatic-buyer |
| Sales | `sales/` | outbound-strategist, coach, deal-strategist, proposal-strategist, pipeline-analyst, discovery-coach, account-strategist |
| Product | `product/` | manager, sprint-prioritizer, trend-researcher, feedback-synthesizer, behavioral-nudge-engine |
| Project Mgmt | `project-management/` | project-manager-senior, jira-workflow-steward, experiment-tracker, project-shepherd, studio-producer |
| Support | `support/` | analytics-reporter, finance-tracker, legal-compliance-checker, infrastructure-maintainer, executive-summary-generator |
| Specialized | `specialized/` | mcp-builder, workflow-architect, salesforce-architect, blockchain-security-auditor, compliance-auditor, supply-chain-strategist, developer-advocate |
| Strategy | `strategy/` | nexus-strategy + phase playbooks (discovery, strategy, foundation, build, hardening, launch, operate) |
| Testing | `testing/` | api-tester, performance-benchmarker, accessibility-auditor, workflow-optimizer, tool-evaluator, reality-checker |
| Spatial | `spatial-computing/` | xr-interface-architect, xr-immersive-developer, visionos-spatial-engineer |
| Game Dev | `game-development/` | game-designer, level-designer, narrative-designer, game-audio-engineer, technical-artist |
| Academic | `academic/` | anthropologist, historian, geographer, psychologist, narratologist |
| Orchestrator | `orchestrator/` | ORCHESTRATOR, decision-matrix, handoff-templates, activation-prompts |

---

## Selection Logic

When in doubt, apply this priority order:

1. **Exact match** — topic directly names a technology or domain the agent specializes in
2. **Division match** — topic falls within a division, pick the most senior/general agent
3. **Cross-domain** — use Orchestrator if the skill spans multiple divisions
4. **Fallback** — Senior Developer (technical) or Workflow Architect (process/business)

---

## Example Selections

| User Request | Selected Agent | File |
|-------------|---------------|------|
| "Build a Next.js 15 skill" | Frontend Developer | `engineering/frontend-developer.md` |
| "Build a Figma design system skill" | UI Designer | `design/ui-designer.md` |
| "Build a GDPR compliance skill" | Legal Compliance Checker | `support/legal-compliance-checker.md` |
| "Build a cold email outreach skill" | Outbound Strategist | `sales/outbound-strategist.md` |
| "Build a TikTok content strategy skill" | TikTok Strategist | `marketing/tiktok-strategist.md` |
| "Build a Kubernetes deployment skill" | DevOps Automator | `engineering/devops-automator.md` |
| "Build a options trading skill" | Finance Tracker | `support/finance-tracker.md` |
| "Build a product roadmap skill" | Product Manager | `product/manager.md` |
| "Build a dbt data pipeline skill" | Data Engineer | `engineering/data-engineer.md` |
| "Build a visionOS spatial skill" | XR Interface Architect | `spatial-computing/xr-interface-architect.md` |
