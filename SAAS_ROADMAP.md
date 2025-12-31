# Agentic Sites: SaaS Product Roadmap

**Version:** 1.0  
**Created:** December 30, 2025  
**Status:** Planning

---

## Product Vision

Transform the validated multi-agent website factory into a full SaaS product with two revenue layers:

- **Layer 1:** Done-for-you website service for SMBs
- **Layer 2:** Agent tooling sold to agencies and developers

This roadmap focuses on Layer 1 — the foundation that proves revenue and sets up Layer 2 expansion.

---

## Layer 1: Done-For-You Website Service

### Target Customer
Small business owners who need a professional website but lack technical skills or time. They want quality output without managing the process.

### Value Proposition
"Professional websites built by AI agents, delivered in days not weeks, at a fraction of agency costs."

---

## Tech Stack Recommendations

| Component | Recommendation | Rationale |
|-----------|---------------|-----------|
| Frontend | Next.js + Tailwind | Fast development, great DX, Vercel-native |
| Auth | Clerk or NextAuth | Quick implementation, handles edge cases |
| Database | Supabase or PlanetScale | Managed, scalable, good free tiers |
| Payments | Stripe | Industry standard, excellent docs |
| Email | Resend or SendGrid | Transactional emails, notifications |
| Hosting | Vercel | Seamless Next.js deployment |
| File Storage | Cloudflare R2 or S3 | Deliverable assets, project files |

---

## Phase 1: Foundation

**Objective:** Get the core application structure live with auth and brief submission.

### 1.1 Marketing Site
Public-facing pages that sell the service.

**Pages:**
- Homepage (hero, how it works, pricing preview, CTA)
- How It Works (3-step process visual)
- Pricing (packages/tiers)
- FAQ
- Contact

**Key Messaging:**
- Speed: "Your website in days, not weeks"
- Quality: "AI-powered, human-polished"
- Simplicity: "Answer a few questions, we handle the rest"

**Product-Ready Criteria:**
- [ ] Clear value proposition above the fold
- [ ] Pricing visible and understandable
- [ ] Mobile responsive
- [ ] Fast load times (<3s)
- [ ] Analytics installed (Plausible or Vercel Analytics)

### 1.2 Authentication System
Secure customer accounts.

**Features:**
- Email/password signup
- Email verification
- Password reset
- OAuth optional (Google)

**Product-Ready Criteria:**
- [ ] Signup/login flows tested
- [ ] Email verification working
- [ ] Password reset working
- [ ] Session management secure
- [ ] Rate limiting on auth endpoints

### 1.3 Client Brief Submission
Convert the standardized intake template to a web form.

**Form Sections:**
1. Business Basics (name, industry, location)
2. Services/Products (what they offer)
3. Target Audience (who they serve)
4. Brand Preferences (colors, tone, competitors they like)
5. Content Inputs (existing copy, images if available)
6. Contact/CTA Goals (what action visitors should take)

**UX Considerations:**
- Multi-step form (not one long page)
- Progress indicator
- Save draft functionality
- File upload for logos/images
- Clear helper text for each field

**Product-Ready Criteria:**
- [ ] All fields from standardized brief captured
- [ ] Validation on required fields
- [ ] File uploads working (size limits, type restrictions)
- [ ] Draft saving functional
- [ ] Submission confirmation screen
- [ ] Data stored securely in database

### 1.4 Customer Dashboard (Basic)
Where customers track their project.

**Initial Features:**
- View submitted brief
- See project status
- Access to support/contact

**Product-Ready Criteria:**
- [ ] Dashboard loads after login
- [ ] Brief summary displayed
- [ ] Status indicator visible
- [ ] Navigation intuitive

---

## Phase 2: Payments & Orders

**Objective:** Accept payments and connect payment to project creation.

### 2.1 Pricing Structure

**Recommended Model: Tiered Packages**

| Package | Price | Includes |
|---------|-------|----------|
| Starter | $497 | 1-page landing site, basic SEO, 1 revision |
| Growth | $997 | 5-page site, SEO, contact form, 2 revisions |
| Professional | $1,997 | 10-page site, SEO, forms, analytics, 3 revisions |

**Add-ons:**
- Additional pages: $97/page
- Logo design: $197
- Monthly maintenance: $97/month
- Rush delivery (48hr): +50%

**Why This Model:**
- Clear value ladder
- Room for upsells
- Competitive with freelancers, undercuts agencies
- Margins support automation investment

### 2.2 Stripe Integration

**Payment Flow:**
1. Customer selects package
2. Redirected to Stripe Checkout
3. Payment processed
4. Webhook confirms payment
5. Project created in system
6. Customer redirected to dashboard
7. Confirmation email sent

**Product-Ready Criteria:**
- [ ] Stripe account configured (test + live)
- [ ] Checkout session creation working
- [ ] Webhook handler processing events
- [ ] Payment success creates project record
- [ ] Payment failure handled gracefully
- [ ] Receipts sent automatically
- [ ] Refund process documented

### 2.3 Order Confirmation Flow

**Automated Sequence:**
1. Payment success → Create project in database
2. Send confirmation email with:
   - Order summary
   - Expected timeline
   - What happens next
   - Support contact
3. Update dashboard status to "Submitted"
4. Notify admin (you) of new project

**Product-Ready Criteria:**
- [ ] Project record created on payment
- [ ] Confirmation email sends immediately
- [ ] Dashboard reflects new project
- [ ] Admin notification working

---

## Phase 3: Operations & Delivery

**Objective:** Build the backend systems to manage and deliver projects.

### 3.1 Admin Dashboard

**Your Control Center:**
- View all projects (queue)
- Filter by status (New, In Progress, Review, Delivered)
- Access customer brief for each project
- Trigger agent workflows
- Update project status
- Add internal notes
- Upload deliverables

**Product-Ready Criteria:**
- [ ] All projects visible in list view
- [ ] Status filtering works
- [ ] Brief details accessible
- [ ] Status updates reflect on customer dashboard
- [ ] File upload for deliverables working
- [ ] Secure (admin-only access)

### 3.2 Project Status Workflow

**Status Stages:**

```
Submitted → In Progress → Internal Review → Client Review → Revisions → Delivered → Complete
```

**Status Definitions:**
- **Submitted:** Payment received, brief complete
- **In Progress:** Agent workflow running
- **Internal Review:** You reviewing output before client sees it
- **Client Review:** Preview sent to customer
- **Revisions:** Customer requested changes
- **Delivered:** Final files sent
- **Complete:** Project closed

**Automated Transitions:**
- Payment → Submitted (automatic)
- Others triggered manually from admin dashboard initially
- Future: Agent completion → Internal Review (automated)

### 3.3 Customer Notification System

**Email Triggers:**
| Event | Email |
|-------|-------|
| Payment confirmed | Order confirmation |
| Status → In Progress | "We've started building" |
| Status → Client Review | "Your preview is ready" |
| Status → Delivered | "Your website is complete" |
| Revision submitted | "We received your feedback" |

**Product-Ready Criteria:**
- [ ] Email templates created for each trigger
- [ ] Emails send reliably
- [ ] Unsubscribe option included
- [ ] Links in emails work correctly

### 3.4 Deliverable Handoff

**Delivery Package:**
- Preview link (staging URL)
- Source code (GitHub repo or ZIP)
- Deployment instructions
- Asset files (logos, images)
- Documentation (how to update content)

**Revision Workflow:**
1. Customer views preview
2. Submits feedback via dashboard form
3. Feedback logged to project
4. Admin notified
5. Revisions made (within package limits)
6. Updated preview sent
7. Approval requested

**Product-Ready Criteria:**
- [ ] Preview link generation working
- [ ] Feedback form captures structured input
- [ ] Revision count tracked against package limit
- [ ] Final deliverable download available
- [ ] Sign-off/approval mechanism

---

## Phase 4: Polish & Scale Prep

**Objective:** Refine the experience and prepare for growth.

### 4.1 Revision & Feedback System

**Structured Feedback Form:**
- Page-by-page comments
- Screenshot annotation (nice-to-have)
- Priority ranking
- Clear scope boundaries (what's included vs. out of scope)

**Product-Ready Criteria:**
- [ ] Feedback organized by page/section
- [ ] Customer understands revision limits
- [ ] Out-of-scope requests handled gracefully
- [ ] Revision history tracked

### 4.2 Customer Support

**Initial Setup:**
- Support email (support@agenticsites.com)
- FAQ page (reduces tickets)
- Dashboard contact form
- Response SLA defined (24-48 hrs)

**Future:**
- Help center with guides
- Chat widget (Intercom/Crisp)
- Video tutorials

### 4.3 Beta Testing

**Before Public Launch:**
- 3-5 beta customers (discounted or free)
- Full workflow tested end-to-end
- Feedback collected on:
  - Brief submission experience
  - Communication clarity
  - Deliverable quality
  - Overall satisfaction

**Product-Ready Criteria:**
- [ ] Beta projects completed successfully
- [ ] Major friction points resolved
- [ ] Testimonials/case studies captured
- [ ] Pricing validated

### 4.4 Launch Checklist

**Technical:**
- [ ] All environments production-ready
- [ ] SSL certificates active
- [ ] Error monitoring (Sentry)
- [ ] Backup systems confirmed
- [ ] Load testing passed

**Legal:**
- [ ] Terms of Service
- [ ] Privacy Policy
- [ ] Refund Policy
- [ ] Service Agreement template

**Marketing:**
- [ ] Launch announcement ready
- [ ] Social profiles set up
- [ ] Initial content/posts scheduled
- [ ] Email list for prospects

---

## Agent Integration Points

**Where the multi-agent system connects:**

| Phase | Integration |
|-------|-------------|
| Brief Submission | Form data feeds into Orchestrator input format |
| In Progress | Admin triggers Orchestrator → agent workflow executes |
| Internal Review | Output from Frontend Agent → preview generation |
| Revisions | Feedback routed to appropriate agent for updates |

**Current State:** Manual trigger from admin dashboard
**Future State:** Automated orchestration on project creation

---

## Metrics to Track

**Business:**
- Projects completed
- Revenue per month
- Average project value
- Customer acquisition cost
- Time from payment to delivery

**Product:**
- Brief completion rate
- Revision requests per project
- Customer satisfaction score
- Support ticket volume

**Technical:**
- Agent success rate
- Build errors
- Page load times
- Uptime

---

## Timeline Estimate

| Phase | Estimated Duration |
|-------|-------------------|
| Phase 1: Foundation | 2-3 weeks |
| Phase 2: Payments | 1-2 weeks |
| Phase 3: Operations | 2-3 weeks |
| Phase 4: Polish | 2-4 weeks |
| Beta Testing | 2-4 weeks |

**Total to Product-Ready:** 9-16 weeks depending on scope decisions and testing cycles.

*Note: Timeline is estimate only — quality over speed per project requirements.*

---

## Layer 2 Preview

Once Layer 1 is stable and generating revenue, Layer 2 expands the business:

**Layer 2: Agency/Developer Tooling**
- API access to agent system
- White-label dashboard
- Bulk project pricing
- Custom agent configuration
- Partner program

This becomes viable once Layer 1 proves:
- Agent system handles diverse projects
- Operations workflow is solid
- Pricing model works

---

## Next Actions

1. **Finalize tech stack decisions** — Confirm Next.js + Supabase + Stripe + Vercel
2. **Set up development environment** — New repo for SaaS app (separate from agent system)
3. **Begin Phase 1.1** — Marketing site design and copy
4. **Domain selection** — Secure agenticsites.com or alternative

---

## Document History

| Date | Version | Changes |
|------|---------|---------|
| Dec 30, 2025 | 1.0 | Initial roadmap created |
