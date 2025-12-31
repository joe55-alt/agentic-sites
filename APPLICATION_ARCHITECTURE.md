# Agentic Sites: Application Architecture

**Version:** 1.0  
**Created:** December 30, 2025  
**Purpose:** Technical specification for SaaS application layer

---

## Overview

This document defines the database schema, authentication setup, and brief submission form for the Agentic Sites SaaS application.

**Tech Stack:**
- Database: Supabase (PostgreSQL)
- Auth: Supabase Auth
- Frontend: Next.js (generated via Bolt/Lovable)
- Payments: Stripe (Phase 2)
- Hosting: Vercel

---

## Part 1: Supabase Setup

### 1.1 Create Supabase Project

1. Go to https://supabase.com
2. Create new project
3. Name: `agentic-sites`
4. Choose region closest to target customers (US West or US East)
5. Save the project URL and anon key

### 1.2 Environment Variables Needed

```
NEXT_PUBLIC_SUPABASE_URL=your_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key (server-side only)
```

---

## Part 2: Database Schema

### 2.1 Tables Overview

| Table | Purpose |
|-------|---------|
| profiles | Extended user data (linked to auth.users) |
| projects | Website projects (one per purchase) |
| briefs | Client brief submissions |
| project_status_history | Audit log of status changes |
| files | Uploaded assets and deliverables |

### 2.2 SQL Schema

Run this in Supabase SQL Editor:

```sql
-- =============================================
-- PROFILES TABLE
-- Extended user information beyond auth.users
-- =============================================

CREATE TABLE profiles (
  id UUID PRIMARY KEY REFERENCES auth.users(id) ON DELETE CASCADE,
  email TEXT NOT NULL,
  full_name TEXT,
  company_name TEXT,
  phone TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Enable RLS
ALTER TABLE profiles ENABLE ROW LEVEL SECURITY;

-- Users can read/update their own profile
CREATE POLICY "Users can view own profile" 
  ON profiles FOR SELECT 
  USING (auth.uid() = id);

CREATE POLICY "Users can update own profile" 
  ON profiles FOR UPDATE 
  USING (auth.uid() = id);

-- Auto-create profile on signup
CREATE OR REPLACE FUNCTION handle_new_user()
RETURNS TRIGGER AS $$
BEGIN
  INSERT INTO profiles (id, email, full_name)
  VALUES (
    NEW.id,
    NEW.email,
    NEW.raw_user_meta_data->>'full_name'
  );
  RETURN NEW;
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;

CREATE TRIGGER on_auth_user_created
  AFTER INSERT ON auth.users
  FOR EACH ROW EXECUTE FUNCTION handle_new_user();


-- =============================================
-- PROJECTS TABLE
-- One project per website purchase
-- =============================================

CREATE TYPE project_status AS ENUM (
  'draft',
  'submitted',
  'in_progress',
  'internal_review',
  'client_review',
  'revisions',
  'delivered',
  'complete',
  'cancelled'
);

CREATE TYPE project_package AS ENUM (
  'starter',
  'growth',
  'professional'
);

CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES profiles(id) ON DELETE CASCADE,
  
  -- Project info
  name TEXT NOT NULL,
  package project_package NOT NULL,
  status project_status DEFAULT 'draft',
  
  -- Pricing
  price_cents INTEGER NOT NULL,
  paid BOOLEAN DEFAULT FALSE,
  stripe_payment_id TEXT,
  
  -- Revisions
  revisions_allowed INTEGER NOT NULL DEFAULT 2,
  revisions_used INTEGER DEFAULT 0,
  
  -- Delivery
  preview_url TEXT,
  live_url TEXT,
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  submitted_at TIMESTAMP WITH TIME ZONE,
  delivered_at TIMESTAMP WITH TIME ZONE
);

-- Enable RLS
ALTER TABLE projects ENABLE ROW LEVEL SECURITY;

-- Users can view their own projects
CREATE POLICY "Users can view own projects" 
  ON projects FOR SELECT 
  USING (auth.uid() = user_id);

-- Users can create projects
CREATE POLICY "Users can create projects" 
  ON projects FOR INSERT 
  WITH CHECK (auth.uid() = user_id);

-- Users can update their own draft projects
CREATE POLICY "Users can update own draft projects" 
  ON projects FOR UPDATE 
  USING (auth.uid() = user_id AND status = 'draft');

-- Index for faster queries
CREATE INDEX idx_projects_user_id ON projects(user_id);
CREATE INDEX idx_projects_status ON projects(status);


-- =============================================
-- BRIEFS TABLE
-- Client questionnaire responses
-- =============================================

CREATE TABLE briefs (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID NOT NULL REFERENCES projects(id) ON DELETE CASCADE,
  
  -- Business Basics
  business_name TEXT NOT NULL,
  industry TEXT NOT NULL,
  business_description TEXT NOT NULL,
  location TEXT,
  years_in_business TEXT,
  
  -- Services & Products
  primary_services TEXT NOT NULL,
  service_areas TEXT,
  unique_selling_points TEXT,
  
  -- Target Audience
  target_audience TEXT NOT NULL,
  customer_pain_points TEXT,
  ideal_customer_description TEXT,
  
  -- Brand & Design
  existing_logo BOOLEAN DEFAULT FALSE,
  brand_colors TEXT,
  brand_personality TEXT,
  websites_they_like TEXT,
  design_preferences TEXT,
  
  -- Content
  tagline TEXT,
  key_messages TEXT,
  existing_content BOOLEAN DEFAULT FALSE,
  content_notes TEXT,
  
  -- Goals & CTAs
  primary_goal TEXT NOT NULL,
  secondary_goals TEXT,
  primary_cta TEXT NOT NULL,
  contact_methods TEXT,
  
  -- Technical
  existing_domain TEXT,
  need_domain BOOLEAN DEFAULT FALSE,
  integrations_needed TEXT,
  special_requirements TEXT,
  
  -- Additional
  competitor_websites TEXT,
  additional_notes TEXT,
  
  -- Timestamps
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Enable RLS
ALTER TABLE briefs ENABLE ROW LEVEL SECURITY;

-- Users can view briefs for their projects
CREATE POLICY "Users can view own briefs" 
  ON briefs FOR SELECT 
  USING (
    EXISTS (
      SELECT 1 FROM projects 
      WHERE projects.id = briefs.project_id 
      AND projects.user_id = auth.uid()
    )
  );

-- Users can create briefs for their projects
CREATE POLICY "Users can create briefs" 
  ON briefs FOR INSERT 
  WITH CHECK (
    EXISTS (
      SELECT 1 FROM projects 
      WHERE projects.id = briefs.project_id 
      AND projects.user_id = auth.uid()
    )
  );

-- Users can update briefs for draft projects
CREATE POLICY "Users can update own briefs" 
  ON briefs FOR UPDATE 
  USING (
    EXISTS (
      SELECT 1 FROM projects 
      WHERE projects.id = briefs.project_id 
      AND projects.user_id = auth.uid()
      AND projects.status = 'draft'
    )
  );


-- =============================================
-- PROJECT STATUS HISTORY
-- Audit log of all status changes
-- =============================================

CREATE TABLE project_status_history (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID NOT NULL REFERENCES projects(id) ON DELETE CASCADE,
  old_status project_status,
  new_status project_status NOT NULL,
  changed_by UUID REFERENCES profiles(id),
  notes TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Enable RLS
ALTER TABLE project_status_history ENABLE ROW LEVEL SECURITY;

-- Users can view history for their projects
CREATE POLICY "Users can view own project history" 
  ON project_status_history FOR SELECT 
  USING (
    EXISTS (
      SELECT 1 FROM projects 
      WHERE projects.id = project_status_history.project_id 
      AND projects.user_id = auth.uid()
    )
  );

-- Auto-log status changes
CREATE OR REPLACE FUNCTION log_project_status_change()
RETURNS TRIGGER AS $$
BEGIN
  IF OLD.status IS DISTINCT FROM NEW.status THEN
    INSERT INTO project_status_history (project_id, old_status, new_status)
    VALUES (NEW.id, OLD.status, NEW.status);
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;

CREATE TRIGGER on_project_status_change
  AFTER UPDATE ON projects
  FOR EACH ROW EXECUTE FUNCTION log_project_status_change();


-- =============================================
-- FILES TABLE
-- Uploaded assets and deliverables
-- =============================================

CREATE TYPE file_type AS ENUM (
  'logo',
  'image',
  'document',
  'deliverable',
  'other'
);

CREATE TABLE files (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  project_id UUID NOT NULL REFERENCES projects(id) ON DELETE CASCADE,
  
  file_name TEXT NOT NULL,
  file_type file_type NOT NULL,
  file_path TEXT NOT NULL,
  file_size INTEGER,
  mime_type TEXT,
  
  uploaded_by UUID REFERENCES profiles(id),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Enable RLS
ALTER TABLE files ENABLE ROW LEVEL SECURITY;

-- Users can view files for their projects
CREATE POLICY "Users can view own project files" 
  ON files FOR SELECT 
  USING (
    EXISTS (
      SELECT 1 FROM projects 
      WHERE projects.id = files.project_id 
      AND projects.user_id = auth.uid()
    )
  );

-- Users can upload files to their projects
CREATE POLICY "Users can upload files to own projects" 
  ON files FOR INSERT 
  WITH CHECK (
    EXISTS (
      SELECT 1 FROM projects 
      WHERE projects.id = files.project_id 
      AND projects.user_id = auth.uid()
    )
  );


-- =============================================
-- ADMIN VIEWS
-- For admin dashboard (service role access)
-- =============================================

-- View all projects with user info (admin only, use service role)
CREATE VIEW admin_projects_view AS
SELECT 
  p.*,
  pr.email,
  pr.full_name,
  pr.company_name,
  pr.phone
FROM projects p
JOIN profiles pr ON p.user_id = pr.id;

-- View project queue by status
CREATE VIEW project_queue AS
SELECT 
  p.id,
  p.name,
  p.package,
  p.status,
  p.created_at,
  p.submitted_at,
  pr.email,
  pr.company_name
FROM projects p
JOIN profiles pr ON p.user_id = pr.id
WHERE p.status NOT IN ('draft', 'complete', 'cancelled')
ORDER BY p.submitted_at ASC;
```

### 2.3 Storage Buckets

Create these buckets in Supabase Storage:

```sql
-- Run in SQL Editor or create via Dashboard

-- Bucket for client uploads (logos, images)
INSERT INTO storage.buckets (id, name, public)
VALUES ('client-uploads', 'client-uploads', false);

-- Bucket for deliverables
INSERT INTO storage.buckets (id, name, public)
VALUES ('deliverables', 'deliverables', false);

-- RLS policies for client-uploads
CREATE POLICY "Users can upload to own folder"
ON storage.objects FOR INSERT
WITH CHECK (
  bucket_id = 'client-uploads' AND
  auth.uid()::text = (storage.foldername(name))[1]
);

CREATE POLICY "Users can view own uploads"
ON storage.objects FOR SELECT
USING (
  bucket_id = 'client-uploads' AND
  auth.uid()::text = (storage.foldername(name))[1]
);
```

---

## Part 3: Package Configuration

### 3.1 Pricing & Features

```javascript
// config/packages.js

export const PACKAGES = {
  starter: {
    name: 'Starter',
    price: 497,
    price_cents: 49700,
    pages: 5,
    revisions: 2,
    support_days: 30,
    features: [
      'Up to 5 pages',
      'Mobile responsive design',
      'Contact form integration',
      'Basic SEO optimization',
      '2 rounds of revisions',
      '30 days of support'
    ]
  },
  growth: {
    name: 'Growth',
    price: 997,
    price_cents: 99700,
    pages: 10,
    revisions: 3,
    support_days: 90,
    popular: true,
    features: [
      'Up to 10 pages',
      'Custom design & branding',
      'Advanced SEO optimization',
      'Blog setup',
      'Contact & lead forms',
      '3 rounds of revisions',
      '90 days of support',
      'Google Analytics setup'
    ]
  },
  professional: {
    name: 'Professional',
    price: 1997,
    price_cents: 199700,
    pages: 20,
    revisions: -1, // unlimited
    support_days: 180,
    features: [
      'Up to 20 pages',
      'Premium custom design',
      'E-commerce capability',
      'Advanced integrations',
      'Content management system',
      'Unlimited revisions',
      '180 days of support',
      'Priority development',
      'Performance optimization'
    ]
  }
};
```

---

## Part 4: Brief Submission Form Specification

### 4.1 Form Flow

Multi-step form with 6 sections:

```
Step 1: Business Basics
Step 2: Services & Products  
Step 3: Target Audience
Step 4: Brand & Design
Step 5: Goals & Website Needs
Step 6: Review & Submit
```

### 4.2 Form Fields by Section

#### Step 1: Business Basics

| Field | Type | Required | Validation |
|-------|------|----------|------------|
| business_name | text | Yes | Min 2 chars |
| industry | select | Yes | From industry list |
| business_description | textarea | Yes | Min 50 chars, max 500 |
| location | text | No | City, State format |
| years_in_business | select | No | <1, 1-2, 3-5, 5-10, 10+ |

**Industry Options:**
- Restaurant & Food Service
- Retail & E-commerce
- Professional Services
- Healthcare & Wellness
- Home Services
- Beauty & Personal Care
- Fitness & Sports
- Real Estate
- Automotive
- Construction & Trades
- Technology
- Education
- Non-Profit
- Other

#### Step 2: Services & Products

| Field | Type | Required | Validation |
|-------|------|----------|------------|
| primary_services | textarea | Yes | Min 20 chars |
| service_areas | text | No | - |
| unique_selling_points | textarea | No | Max 500 chars |

**Helper Text:**
- primary_services: "List your main products or services. What do you offer to customers?"
- unique_selling_points: "What makes you different from competitors? Why should customers choose you?"

#### Step 3: Target Audience

| Field | Type | Required | Validation |
|-------|------|----------|------------|
| target_audience | textarea | Yes | Min 20 chars |
| customer_pain_points | textarea | No | Max 500 chars |
| ideal_customer_description | textarea | No | Max 500 chars |

**Helper Text:**
- target_audience: "Who are your ideal customers? (Age, location, interests, etc.)"
- customer_pain_points: "What problems do your customers face that you solve?"

#### Step 4: Brand & Design

| Field | Type | Required | Validation |
|-------|------|----------|------------|
| existing_logo | boolean | Yes | - |
| logo_upload | file | If has logo | jpg/png, max 5MB |
| brand_colors | text | No | - |
| brand_personality | multiselect | No | From list |
| websites_they_like | textarea | No | URLs |
| design_preferences | textarea | No | Max 500 chars |

**Brand Personality Options:**
- Professional & Corporate
- Friendly & Approachable
- Bold & Energetic
- Calm & Trustworthy
- Modern & Innovative
- Traditional & Established
- Playful & Fun
- Luxurious & Premium
- Minimalist & Clean
- Warm & Personal

#### Step 5: Goals & Website Needs

| Field | Type | Required | Validation |
|-------|------|----------|------------|
| primary_goal | select | Yes | From list |
| secondary_goals | multiselect | No | From list |
| primary_cta | select | Yes | From list |
| contact_methods | multiselect | Yes | At least one |
| existing_domain | text | No | Valid domain format |
| need_domain | boolean | No | - |
| integrations_needed | multiselect | No | From list |
| special_requirements | textarea | No | Max 500 chars |

**Primary Goal Options:**
- Generate leads / inquiries
- Sell products online
- Showcase portfolio / work
- Provide information
- Build brand awareness
- Book appointments
- Other

**Primary CTA Options:**
- Call us
- Fill out contact form
- Request a quote
- Book an appointment
- Shop now
- Learn more
- Get started

**Contact Methods:**
- Phone
- Email
- Contact form
- Live chat
- WhatsApp
- Social media

**Integrations:**
- Google Analytics
- Facebook Pixel
- Google Maps
- Calendly / Booking
- Mailchimp / Email marketing
- Social media feeds
- Payment processing
- Other

#### Step 6: Review & Submit

Display summary of all entered information with edit buttons for each section.

Final fields:

| Field | Type | Required |
|-------|------|----------|
| competitor_websites | textarea | No |
| additional_notes | textarea | No |
| agree_to_terms | checkbox | Yes |

---

## Part 5: Prompt for Bolt/Lovable

Use this prompt to generate the brief submission form:

---

Create a multi-step client brief submission form for "Agentic Sites" — a website building service. This form collects information from small business owners to build their websites.

**Technical Requirements:**
- Next.js with TypeScript
- Supabase for database and auth
- Tailwind CSS styling
- Form validation with react-hook-form + zod
- Match existing site design (deep blue #1e3a5f, teal #14b8a6 accent)

**Authentication:**
- User must be logged in to access form
- If not logged in, redirect to signup/login page
- Use Supabase Auth

**Form Structure (6 steps with progress indicator):**

**Step 1: Business Basics**
- Business name (required, text)
- Industry (required, dropdown with options: Restaurant, Retail, Professional Services, Healthcare, Home Services, Beauty, Fitness, Real Estate, Automotive, Construction, Technology, Education, Non-Profit, Other)
- Business description (required, textarea, 50-500 chars)
- Location (optional, text)
- Years in business (optional, dropdown: <1, 1-2, 3-5, 5-10, 10+)

**Step 2: Services & Products**
- Primary services/products (required, textarea)
- Service areas (optional, text)
- What makes you unique (optional, textarea)

**Step 3: Target Audience**
- Who are your ideal customers (required, textarea)
- Customer pain points (optional, textarea)
- Ideal customer description (optional, textarea)

**Step 4: Brand & Design**
- Do you have a logo? (required, yes/no toggle)
- If yes: logo upload (file input, jpg/png, max 5MB)
- Brand colors (optional, text or color picker)
- Brand personality (optional, multi-select: Professional, Friendly, Bold, Calm, Modern, Traditional, Playful, Luxurious, Minimalist, Warm)
- Websites you like (optional, textarea for URLs)
- Design preferences (optional, textarea)

**Step 5: Goals & Website Needs**
- Primary goal (required, dropdown: Generate leads, Sell products, Showcase portfolio, Provide information, Build brand, Book appointments, Other)
- Secondary goals (optional, multi-select same options)
- Main call-to-action (required, dropdown: Call us, Contact form, Request quote, Book appointment, Shop now, Learn more)
- Contact methods (required, multi-select: Phone, Email, Contact form, Live chat, WhatsApp, Social)
- Existing domain (optional, text)
- Need help with domain? (checkbox)
- Integrations needed (optional, multi-select: Google Analytics, Facebook Pixel, Google Maps, Calendly, Mailchimp, Social feeds, Payments)
- Special requirements (optional, textarea)

**Step 6: Review & Submit**
- Display summary of all entered data organized by section
- Edit button for each section to go back
- Competitor websites (optional, textarea)
- Additional notes (optional, textarea)
- Terms agreement checkbox (required)
- Submit button

**Form Behavior:**
- Save progress to localStorage on each step
- Show progress bar (Step X of 6)
- Back/Next navigation buttons
- Validation on each step before proceeding
- On submit: save to Supabase 'briefs' table linked to a new project
- After submit: redirect to dashboard with success message

**UI/UX:**
- Clean, professional design matching marketing site
- One question group visible at a time
- Helpful placeholder text and descriptions
- Mobile responsive
- Loading states on submit

---

*End of prompt*

---

## Part 6: Authentication Pages

### 6.1 Required Auth Pages

| Page | Route | Purpose |
|------|-------|---------|
| Sign Up | /signup | New user registration |
| Login | /login | Existing user login |
| Forgot Password | /forgot-password | Password reset request |
| Reset Password | /reset-password | Set new password |

### 6.2 Auth Prompt for Bolt/Lovable

---

Create authentication pages for "Agentic Sites" using Supabase Auth.

**Pages needed:**

**1. Sign Up (/signup)**
- Full name (required)
- Email (required)
- Password (required, min 8 chars)
- Confirm password
- "Sign Up" button
- Link to login page
- Google OAuth button (optional)

**2. Login (/login)**
- Email
- Password
- "Remember me" checkbox
- "Login" button
- "Forgot password?" link
- Link to sign up page
- Google OAuth button (optional)

**3. Forgot Password (/forgot-password)**
- Email input
- "Send Reset Link" button
- Success message after submission
- Link back to login

**4. Reset Password (/reset-password)**
- New password
- Confirm password
- "Update Password" button
- Redirect to login on success

**Technical:**
- Use Supabase Auth
- Handle errors gracefully (show user-friendly messages)
- Redirect authenticated users away from auth pages
- After signup, redirect to brief form
- After login, redirect to dashboard

**Design:**
- Centered card layout
- Match site colors (deep blue, teal accent)
- Clean, minimal design
- Mobile responsive

---

*End of prompt*

---

## Part 7: Implementation Order

### Phase 1: Foundation (Current)

1. ✅ Marketing site (complete)
2. ⬜ Set up Supabase project
3. ⬜ Run database schema SQL
4. ⬜ Generate auth pages
5. ⬜ Generate brief submission form
6. ⬜ Connect form to Supabase

### Phase 2: Payments (Next)

7. ⬜ Stripe account setup
8. ⬜ Package selection page
9. ⬜ Checkout flow
10. ⬜ Payment webhooks

### Phase 3: Operations

11. ⬜ Customer dashboard
12. ⬜ Admin dashboard
13. ⬜ Email notifications

---

## Next Actions

1. **Create Supabase project** at supabase.com
2. **Run the SQL schema** in Supabase SQL Editor
3. **Create storage buckets** for file uploads
4. **Generate auth pages** using the prompt above
5. **Generate brief form** using the prompt above
6. **Connect to Supabase** and test the flow

---

## Document History

| Date | Version | Changes |
|------|---------|---------|
| Dec 30, 2025 | 1.0 | Initial architecture spec |
