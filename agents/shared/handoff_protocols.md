# 🔄 Handoff Protocols

## Overview

This document defines how agents pass work to each other and what constitutes a complete handoff.

---

## Agent Dependencies

```
START
  │
  ▼
┌─────────────────┐
│   ORCHESTRATOR  │ ← Receives brief, creates task plan
└────────┬────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌───────┐ ┌─────────┐
│ LOGO  │ │ CONTENT │  ← Can run in PARALLEL
└───┬───┘ └────┬────┘
    │          │
    └────┬─────┘
         ▼
   ┌───────────┐
   │ FRONTEND  │  ← Needs logo + content first
   └─────┬─────┘
         │
         ▼
   ┌───────────┐
   │    SEO    │  ← Needs frontend complete
   └─────┬─────┘
         │
         ▼
   ┌───────────┐
   │  HOSTING  │  ← Needs SEO complete
   └─────┬─────┘
         │
         ▼
   ┌───────────┐
   │    SOP    │  ← Needs hosting complete
   └─────┬─────┘
         │
         ▼
      COMPLETE
```

---

## Handoff Requirements

### Logo Agent → Frontend Agent

**Must Include:**
- [ ] Primary logo (SVG + PNG)
- [ ] Icon-only version
- [ ] Favicon (ICO, 32x32)
- [ ] Color palette with hex codes
- [ ] Typography selections (font names + weights)
- [ ] Brand guidelines document

**Saved To:**
```
/projects/{id}/assets/brand/
```

**Handoff Signal:**
"Logo complete. Assets saved to /projects/{id}/assets/brand/. Ready for frontend."

---

### Content Agent → Frontend Agent

**Must Include:**
- [ ] All page content (no placeholders)
- [ ] Meta titles and descriptions
- [ ] Image alt text suggestions
- [ ] CTA button text
- [ ] Any testimonials/quotes

**Saved To:**
```
/projects/{id}/content/
├── homepage.md
├── about.md
├── services.md
├── contact.md
└── meta_content.md
```

**Handoff Signal:**
"Content complete. All pages ready in /projects/{id}/content/. Ready for frontend."

---

### Frontend Agent → SEO Agent

**Must Include:**
- [ ] Lovable.dev project link
- [ ] Page structure/URLs
- [ ] GitHub sync status
- [ ] Screenshots (desktop + mobile)
- [ ] List of any dynamic elements

**Saved To:**
```
/projects/{id}/build/
├── lovable_link.md
├── screenshots/
└── structure.md
```

**Handoff Signal:**
"Frontend build complete. Lovable link: {url}. Ready for SEO optimization."

---

### SEO Agent → Hosting Agent

**Must Include:**
- [ ] All meta tags document
- [ ] Schema markup (JSON-LD files)
- [ ] robots.txt
- [ ] sitemap.xml
- [ ] Implementation instructions

**Saved To:**
```
/projects/{id}/seo/
├── meta_tags.md
├── schema/
├── robots.txt
└── sitemap.xml
```

**Handoff Signal:**
"SEO complete. Meta tags and schema ready for implementation. Ready for deployment."

---

### Hosting Agent → SOP Agent

**Must Include:**
- [ ] Live site URL
- [ ] Vercel project details
- [ ] DNS configuration records
- [ ] SSL status
- [ ] All credentials

**Saved To:**
```
/projects/{id}/deployment/
├── deployment_info.md
├── dns_records.md
└── credentials.md
```

**Handoff Signal:**
"Site live at https://{domain}.com. All deployment info documented. Ready for handoff docs."

---

## Handoff Message Format

When completing a task, agents report to orchestrator:

```markdown
## Handoff: {Agent Name} → {Next Agent}

**Project:** {project_id}
**Status:** ✅ Complete

### Deliverables
| Item | Location | Status |
|------|----------|--------|
| {item} | {path} | ✅ |

### Notes
{Any important context for next agent}

### Dependencies Met
- [x] {Requirement 1}
- [x] {Requirement 2}

### Ready for: {Next Agent Name}
```

---

## Blocker Protocol

If an agent cannot complete their task:

```markdown
## BLOCKER: {Agent Name}

**Project:** {project_id}
**Status:** 🔴 Blocked

### Issue
{Description of what's blocking progress}

### Waiting For
{What's needed to proceed}

### Impact
{What downstream agents are affected}

### Suggested Resolution
{Proposed solution or who can help}
```

---

## Quality Gates

Before any handoff is accepted, orchestrator verifies:

| Gate | Verification |
|------|--------------|
| **Completeness** | All required items delivered |
| **Quality** | Output meets standards |
| **Location** | Files saved in correct paths |
| **Documentation** | Handoff notes provided |

---

## Status Codes

| Code | Meaning | Action |
|------|---------|--------|
| ⚪ | Not started | Waiting for dependencies |
| 🟡 | In progress | Agent working |
| 🟢 | Complete | Ready for next agent |
| 🔴 | Blocked | Needs intervention |
| 🔵 | Under review | Quality check in progress |

---

## Communication Log

All handoffs are logged in:
```
/projects/{id}/build_log.md
```

Format:
```markdown
## Build Log - {Project Name}

### {Date} - {Time}
**Agent:** {agent_name}
**Action:** {what happened}
**Status:** {emoji}
**Notes:** {any details}

---
```
