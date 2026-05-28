# LPS Admin Dashboard — Setup Guide

Your website now has a built-in admin login and content management system (CMS)
at **loyalprofessionalservices.com/admin**

You can edit blog posts, team members, FAQs, testimonials, contact details, and
SEO — all without touching code. Every change you save updates the live website
automatically.

---

## ONE-TIME SETUP (do this once, ~15 minutes)

Your site must be connected to a **Git repository** (GitHub) and deployed via
Netlify for the admin login to work. The Git repo is what lets the CMS save your
edits. Here is the exact sequence:

### Step 1 — Put your site on GitHub
1. Create a free account at github.com
2. Create a new repository called `lps-website`
3. Upload all the website files into it (GitHub lets you drag-and-drop)

### Step 2 — Connect Netlify to GitHub
1. In Netlify, go to your site → **Site configuration → Build & deploy**
2. Click **Link repository** and choose your `lps-website` GitHub repo
3. Now Netlify rebuilds your site automatically whenever content changes

### Step 3 — Turn on Identity (the login system)
1. In Netlify: **Site configuration → Identity → Enable Identity**
2. Under **Registration**, set it to **Invite only** (so only you can log in)
3. Under **Services → Git Gateway**, click **Enable Git Gateway**

### Step 4 — Invite yourself as admin
1. In Netlify Identity, click **Invite users**
2. Enter your email address
3. Check your email, click the link, and set your password
4. That password is hashed and stored securely by Netlify — never in the code

### Step 5 — Log in
1. Go to **loyalprofessionalservices.com/admin**
2. Log in with your email and password
3. You'll see the dashboard. Start editing!

---

## WHAT YOU CAN EDIT FROM THE DASHBOARD

- **Blog Posts** — create, edit, delete, with categories, tags, featured images, SEO fields, and draft/publish control
- **Team Members** — add or update staff, photos, roles, bios
- **FAQs** — add, edit, categorize questions
- **Testimonials** — manage client reviews and star ratings
- **Site Settings** — phone, email, WhatsApp, address, hours, GSTIN
- **Homepage Content** — hero headline, subtext, CTA text, stats
- **SEO Metadata** — meta titles and descriptions
- **Footer** — description and copyright text
- **Images** — upload through the built-in media library

---

## SECURITY (already built in)

- **Password hashing** — handled by Netlify Identity (industry-standard bcrypt)
- **Session management** — secure tokens, auto-expiry
- **Forgot password** — built into the login screen
- **Admin hidden from Google** — noindex headers + robots.txt block
- **Security headers** — clickjacking, XSS, and MIME-sniffing protection via netlify.toml
- **Role-ready** — Netlify Identity supports roles for future multi-user access

---

## IMPORTANT LIMITATIONS (honest notes)

1. **Editing existing homepage text live**: The CMS saves homepage settings to a
   data file (`_data/homepage.json`). For those edits to *appear* on the live
   homepage, a developer needs to do a one-time wiring of the homepage HTML to
   read from that file (about 1-2 hours of work). Blog, team, FAQs and
   testimonials that use the CMS folder system work immediately once a developer
   connects the display templates.

2. **Lead management dashboard**: Use **Netlify Forms** — your contact form
   submissions appear free under Netlify → Forms. For a full CRM-style lead
   tracker with status stages, connect a tool like Airtable or Supabase
   (separate setup).

3. **Analytics dashboard**: GA4, Search Console, and Microsoft Clarity are their
   own dashboards — log into them directly. They cannot be safely rebuilt inside
   this admin without a backend server.

---

## NEED HELP?

This setup connects free tools (GitHub + Netlify Identity + Decap CMS). If you'd
rather have a developer do the one-time setup and wire the homepage fields, share
this guide with them — everything they need is in the `/admin` folder.
