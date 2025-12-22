# 📚 System Overview

## What is Agentic Sites?

Agentic Sites is a multi-agent AI system that automates the production of complete, professional websites. Instead of one AI doing everything, specialized agents handle different aspects of the build — just like a real agency team.

---

## How It Works

### 1. Input: Client Brief
Every project starts with a standardized brief containing business info, design preferences, and requirements.

### 2. Orchestration
The Main Orchestrator Agent analyzes the brief and creates a task plan, assigning work to specialized subagents.

### 3. Parallel & Sequential Execution
- **Parallel:** Logo and Content agents can work simultaneously
- **Sequential:** Frontend needs logo/content first, SEO needs frontend, etc.

### 4. Handoffs
Each agent completes their task and hands off to the next with standardized deliverables.

### 5. Output: Live Website + Docs
The final output is a deployed website plus complete client documentation.

---

## Agent Roles

| Agent | Role | Key Output |
|-------|------|------------|
| **Orchestrator** | Coordination | Task assignments, status tracking |
| **Logo Agent** | Brand identity | Logo, colors, typography |
| **Content Agent** | Copywriting | Page content, meta text |
| **Frontend Agent** | Development | Built website in Lovable |
| **SEO Agent** | Optimization | Meta tags, schema, sitemap |
| **Hosting Agent** | Deployment | Live site on Vercel |
| **SOP Agent** | Documentation | Client handoff package |

---

## Tech Stack

- **Claude Code** — Agent orchestration and execution
- **Lovable.dev** — Frontend development
- **Vercel** — Hosting and deployment
- **Cloudflare** — DNS and SSL
- **GitHub** — Version control
- **n8n** — Workflow automation (optional)

---

## File Structure

```
agentic-sites/
├── agents/           # Agent prompts and logic
│   ├── orchestrator/ # Main controller
│   ├── subagents/    # Specialized agents
│   └── shared/       # Common protocols
├── templates/        # Reusable templates
├── projects/         # Individual builds
└── docs/            # System documentation
```

---

## Getting Started

1. Clone the repo
2. Create a new project folder in `/projects/`
3. Copy `templates/client_intake.md` and fill it out
4. Create `brief.md` for your project
5. Begin orchestration with Claude Code

---

*Last Updated: December 2025*
