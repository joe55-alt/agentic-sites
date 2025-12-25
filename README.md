# 🤖 Agentic Sites

**AI-powered website factory using multi-agent orchestration**

Built by Joe (joe55-alt) | Powered by Claude Code + Lovable.dev + Vercel

---

## 🎯 What This Is

Agentic Sites is a multi-agent system that builds production-ready websites through specialized AI agents working together. Each agent has a defined role, and the orchestrator coordinates them to deliver complete website builds.

## 🏗️ Architecture

```
ORCHESTRATOR AGENT (Main Controller)
         │
    ┌────┴────┬──────────┬──────────┬──────────┬──────────┐
    │         │          │          │          │          │
Frontend    SEO      Content     Logo      Hosting      SOP
 Agent     Agent      Agent     Agent      Agent       Agent
    │         │          │          │          │          │
    ▼         ▼          ▼          ▼          ▼          ▼
 Lovable   Meta/      Copy      Design    Vercel/     Docs/
  Build   Schema    Generation   Gen     Cloudflare  Handoff
```

## 📁 Folder Structure

```
agentic-sites/
├── agents/                    # All agent prompts and logic
│   ├── orchestrator/          # Main controller agent
│   ├── subagents/             # Specialized worker agents
│   └── shared/                # Handoff protocols
├── templates/                 # Reusable templates
├── projects/                  # Individual client builds
├── docs/                      # System documentation
└── scripts/                   # Automation scripts
```

## 🚀 Tech Stack

| Layer | Tools |
|-------|-------|
| Agent Orchestration | Claude Code (CLI + Desktop) |
| Vibe Coding | Lovable.dev, Bolt.new |
| Hosting | Vercel, Cloudflare |
| Version Control | GitHub |
| Automation | n8n |

## 📋 Current Projects

| # | Client | Status | Type |
|---|--------|--------|------|
| 001 | Bloom & Basin (POC) | 🟡 In Progress | Plant Shop + Landscaping |

## 🔄 Workflow

1. **Client Intake** → Standardized brief completed
2. **Orchestrator** → Analyzes brief, assigns tasks to subagents
3. **Subagents Execute** → Each agent completes their specialty
4. **Quality Check** → Review gates before deployment
5. **Deployment** → Vercel + DNS/SSL configuration
6. **Handoff** → SOPs and documentation delivered

## 📈 Roadmap

- [x] Phase 1: Agent architecture design
- [ ] Phase 1: First POC build (Bloom & Basin)
- [ ] Phase 1: Refine agent prompts based on learnings
- [ ] Phase 2: Agency dashboard (future)
- [ ] Phase 2: White-label platform (future)

## 📝 License

Private repository - All rights reserved

---

*Built with Claude Code | Maintained by joe55-alt*
