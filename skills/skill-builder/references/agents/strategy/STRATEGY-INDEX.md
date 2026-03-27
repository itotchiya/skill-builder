---
type: strategy-index
title: "Agent Strategy Index"
parent: "[[agents/AGENTS-INDEX.md]]"
last_updated: "2026-03-16"
---

# Agent Strategy Index

> **FOR AI**: Use this for multi-phase projects. Pick a playbook (sequential phases) or runbook (scenario-specific). Both assume the orchestrator is coordinating specialist agents.

## Table of Contents

- [TL;DR](#tldr)
- [Playbooks (Sequential)](#playbooks-sequential)
- [Runbooks (Scenario-Based)](#runbooks-scenario-based)
- [Strategy Reference](#strategy-reference)

---

## TL;DR

- **Playbooks** = sequential 7-phase lifecycle for building full products
- **Runbooks** = scenario-specific execution guides for known situations
- Always pair with [[agents/orchestrator/ORCHESTRATOR.md]] for coordination
- Each phase/scenario maps to specific agent activations

---

## Playbooks (Sequential)

Use when building something from zero through production.

| Phase | File | Focus |
|-------|------|-------|
| 0 | [[agents/strategy/playbooks/phase-0-discovery.md]] | Requirements, research, constraints |
| 1 | [[agents/strategy/playbooks/phase-1-strategy.md]] | Architecture decisions, tech stack |
| 2 | [[agents/strategy/playbooks/phase-2-foundation.md]] | Project scaffolding, base setup |
| 3 | [[agents/strategy/playbooks/phase-3-build.md]] | Feature implementation with QA loops |
| 4 | [[agents/strategy/playbooks/phase-4-hardening.md]] | Security, performance, testing |
| 5 | [[agents/strategy/playbooks/phase-5-launch.md]] | Deployment, monitoring, go-live |
| 6 | [[agents/strategy/playbooks/phase-6-operate.md]] | Post-launch ops, iteration, growth |

---

## Runbooks (Scenario-Based)

Use when you have a specific situation to handle.

| Scenario | File | Agents Involved |
|----------|------|----------------|
| Build a startup MVP | [[agents/strategy/runbooks/startup-mvp.md]] | product-manager → backend-architect → frontend-developer → devops-automator |
| Develop an enterprise feature | [[agents/strategy/runbooks/enterprise-feature.md]] | project-shepherd → backend-architect → frontend-developer → code-reviewer → api-tester |
| Production incident | [[agents/strategy/runbooks/incident-response.md]] | incident-response-commander → sre → devops-automator |
| Marketing campaign | [[agents/strategy/runbooks/marketing-campaign.md]] | growth-hacker → content-creator → social-media-strategist → seo-specialist |

---

## Strategy Reference

| File | Purpose |
|------|---------|
| [[agents/strategy/nexus-strategy.md]] | Multi-agent orchestration philosophy (8-agent example) |
| [[agents/strategy/QUICKSTART.md]] | Quick start guide for the agency-agents system |
| [[agents/strategy/EXECUTIVE-BRIEF.md]] | High-level strategic overview |
