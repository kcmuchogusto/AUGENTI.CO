# Augentico Website — Deployment Guide

*Everything you need to go from "file on your phone" to "live website" in about 15 minutes.*

---

## Part 1: Set Up GitHub (One Time — 5 mins)

GitHub is where your website files live. Think of it as a smart folder in the cloud that tracks every change you make.

### Step 1: Create a GitHub account
- Go to **github.com** and sign up (free)
- Verify your email

### Step 2: Create a new repository
- Click the **+** icon (top right) → **New repository**
- Name it: **augentico-site**
- Set to **Public** (required for free Cloudflare Pages)
- Tick **Add a README file**
- Click **Create repository**

### Step 3: Upload your website file
- Inside your new repo, click **Add file** → **Upload files**
- Drag in your **index.html** file
- Click **Commit changes**
- That's it — your code is now on GitHub

---

## Part 2: Set Up Cloudflare Pages (One Time — 10 mins)

Cloudflare Pages is what actually serves your website to the world. It's free, fast, and automatic.

### Step 4: Create a Cloudflare account
- Go to **dash.cloudflare.com** and sign up (free)
- Verify your email

### Step 5: Connect your GitHub repo
- In the Cloudflare dashboard, click **Workers & Pages** in the left sidebar
- Click **Create** → **Pages** → **Connect to Git**
- Sign in to GitHub when prompted and authorise Cloudflare
- Select your **augentico-site** repository
- Click **Begin setup**

### Step 6: Configure the build
- **Project name:** augentico
- **Production branch:** main
- **Build command:** leave blank (we don't need a build step)
- **Build output directory:** / (just a forward slash)
- Click **Save and Deploy**
- Wait about 30 seconds — Cloudflare will deploy your site
- You'll get a URL like **augentico.pages.dev** — click it to check your site is live

---

## Part 3: Connect Your Domain (One Time — 10 mins)

### Step 7: Add your custom domain
- In Cloudflare Pages, go to your **augentico** project
- Click **Custom domains** → **Set up a custom domain**
- Enter **augenti.co**
- Cloudflare will ask you to transfer your DNS to Cloudflare

### Step 8: Transfer DNS from GoDaddy to Cloudflare
- In Cloudflare, go to **Websites** → **Add a site** → enter **augenti.co**
- Choose the **Free plan**
- Cloudflare will scan your existing DNS records and show you two **nameservers** (something like `ada.ns.cloudflare.com`)
- Go to **GoDaddy** → **My Domains** → **augenti.co** → **DNS** → **Nameservers**
- Change nameservers from GoDaddy's to the two Cloudflare ones
- Save and wait (can take up to 24 hours, usually under 1 hour)
- Once active, go back to Cloudflare Pages and finish the custom domain setup

### Step 9: Verify it works
- Visit **augenti.co** in your browser
- You should see your Augentico site, with a free SSL certificate (the padlock icon)
- Done. You're live.

---

## Part 4: How to Update Your Site (Ongoing — 2 mins)

This is the workflow you'll use every time you want to make changes.

### Option A: Ask Claude (recommended)
1. Come back to this chat (or start a new one)
2. Tell me what you want changed (e.g. "update the hero headline to XYZ" or "add a new blog post about ABC")
3. I'll give you an updated **index.html**
4. Go to your **augentico-site** repo on GitHub
5. Click on **index.html** → click the **pencil icon** (edit) → **Replace file content** or delete and re-upload
6. Click **Commit changes**
7. Cloudflare auto-deploys in ~30 seconds. Done.

### Option B: Quick text edits yourself
1. Go to your repo on GitHub
2. Click **index.html** → click the **pencil icon**
3. Use Ctrl+F (or Cmd+F) to find the text you want to change
4. Edit it directly
5. Click **Commit changes**
6. Live in 30 seconds

### Option C: Claude Code (when you're ready to level up)
- Install Claude Code on your machine
- Connect it to your GitHub repo
- Describe changes in plain English
- It edits the code and pushes to GitHub automatically
- Cloudflare deploys. You never touch a file.

---

## Still To Do (Wire Up Before Sharing Widely)

These are placeholder features that need connecting to real services:

### Contact Form
- Sign up at **formspree.io** (free, 50 submissions/month)
- Create a new form, get your form endpoint URL
- Replace the `handleContact()` function in the HTML with a Formspree submission
- Or: ask Claude to wire it up for you

### Whitepaper Email Gate
- Sign up at **convertkit.com** or **mailchimp.com** (both have free tiers)
- Create a form/landing page for the whitepaper
- Get the form action URL
- Replace the `handleWP()` function
- Upload your PDF to the email service for auto-delivery

### Booking Links
- Set up **cal.com** (free) or **calendly.com**
- Create 3 event types: Discovery (15 min), Chaos Track Briefing (30 min), Partnership (30 min)
- Replace the `href="#"` on the three booking options with your actual booking URLs

### Blog Posts
- When ready, ask Claude to create individual blog post HTML pages
- Upload them to GitHub alongside index.html
- Update the blog card links on the homepage

---

## Quick Reference

| What | Where |
|------|-------|
| Your code | github.com/YOUR-USERNAME/augentico-site |
| Your hosting | dash.cloudflare.com → Workers & Pages |
| Your domain | GoDaddy (ownership) → Cloudflare (DNS) |
| Your site | augenti.co |
| Need changes? | Ask Claude → upload to GitHub → auto-deploys |

---

*Built with care by Claude. Last updated March 2026.*
