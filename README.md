# Pixel Pulse Analytics

An independent consulting practice by Amy Laird. AI implementation, process design, research, and data tooling for small teams.

Deployed via GitHub Pages with a custom domain at [pixelpulseanalytics.com](https://pixelpulseanalytics.com).

## Site structure

Single-page consulting site, six sections:

- **Hero** — Practice positioning + current availability status + primary CTA (book a strategy call)
- **01 Capabilities** — Four overlapping disciplines (AI implementation, process/SOP design, research/analysis, data tooling). Visitors self-identify which fits their problem.
- **02 Work with me** — Four service tiers from $350 strategy call to $2,000/mo retainer. Each applies across any capability.
- **03 Process** — Three-step explanation of how engagements actually run. Builds trust before the inquiry.
- **04 Selected work** — ProcessPilot, Voynich research, civic data tooling, MaskCoreCost. Framed as evidence of range, not as portfolio for sale.
- **05 FAQ** — Honest answers to the questions prospects actually have (nonprofit work? bigger agencies? tools?)
- **Close** — Big "messy problems are a good sign" CTA + email + LinkedIn

## File inventory

- **`index.html`** — main page, all CSS inline, no build step
- **`404.html`** — custom not-found page matching the site's design
- **`CNAME`** — points the repo at pixelpulseanalytics.com via GitHub Pages
- **`robots.txt`** + **`sitemap.xml`** — basic SEO

No framework, no npm, no dependencies. Plain HTML + Google Fonts.

## Design choices

- **Typography:** Fraunces (variable serif, used at multiple optical sizes for editorial credibility) paired with JetBrains Mono (utility text and labels)
- **Palette:** warm off-white paper (`#faf8f3`), deep ink, single muted-teal accent (`#2f5d54`), with rust and plum as secondary status colors
- **Layout:** asymmetric editorial grid; left-rail section numbers; alternating section backgrounds for rhythm; sticky top nav with subtle blur backdrop
- **Motion:** restrained — one choreographed entrance on page load, subtle hover states only
- **Tone:** confident, understated. No "AI transforming the future of work" platitudes. No live chat widget. No exit-intent popups. The site reads as a practitioner, not a sales funnel.

## Positioning rationale

This is a generalist consulting site, deliberately. The "niche down" advice is good for cold marketing but wrong for the actual shape of an experienced solo practice. The site:

- Presents Amy as the practitioner across four overlapping capabilities
- Lets clients self-select their entry point
- Uses tier pricing (call → audit → sprint → retainer) so different buyer sizes can engage at appropriate levels
- Treats existing independent work (ProcessPilot, Voynich, civic data, MaskCoreCost) as proof of capability rather than as a portfolio of products for sale

The trade-off: lower SEO rank for any single keyword (a niche site would rank better for "AI consultant for nonprofits"). The compensation: clients who arrive via referral, recognition, or organic search are usually warmer and better-paying. Appropriate for "site live but not actively promoting yet" launch posture.

## Pre-deploy checklist

Before going live, you should:

1. **Replace `ProcessPilot`'s `#` link** with a real URL when you have one (or leave as-is — the card still works without a clickable destination)
2. **Confirm your LinkedIn URL** is correct (currently `linkedin.com/in/amy-laird`)
3. **Set up email forwarding in Porkbun** for `hello@pixelpulseanalytics.com` → your real inbox. This is the primary contact path.
4. **Verify pricing feels right** to you. The $350 / $2,500 / $7,500 / $2,000/mo tiers are calibrated to 2026 market for newer indie AI consultants. You can raise prices after 3-5 happy clients; you shouldn't lower them.
5. **Update the "Accepting 2 new clients this quarter" copy** if that number changes. This is one of the few pieces of copy that requires periodic updating.

## How to deploy

### 1. Create the GitHub repo

1. Go to [github.com/new](https://github.com/new)
2. Repository name: `pixelpulseanalytics` (or anything — the CNAME file controls the domain)
3. **Public** ✓ (required for free GitHub Pages)
4. Create

### 2. Upload these files

The web-upload path: on the empty repo page, click **uploading an existing file** and drag all six files in. Commit directly to main.

Or via terminal:

```bash
git init
git add .
git commit -m "Initial consulting site"
git branch -M main
git remote add origin https://github.com/amy2213/pixelpulseanalytics.git
git push -u origin main
```

### 3. Enable GitHub Pages

Settings → Pages → Source: **Deploy from a branch** → **main / root** → Save. Site builds within 60 seconds.

### 4. Update DNS at Porkbun

In Porkbun DNS for `pixelpulseanalytics.com`, **before adding GitHub Pages records, disable any URL Forwarding** (you mentioned it was configured). Then add four A records on the root:

| Type | Host | Answer | TTL |
|---|---|---|---|
| A | (blank) | 185.199.108.153 | 600 |
| A | (blank) | 185.199.109.153 | 600 |
| A | (blank) | 185.199.110.153 | 600 |
| A | (blank) | 185.199.111.153 | 600 |

And one CNAME:

| Type | Host | Answer | TTL |
|---|---|---|---|
| CNAME | www | amy2213.github.io | 600 |

DNS propagates in 10–60 minutes.

### 5. Verify in GitHub

Settings → Pages → Custom domain: `pixelpulseanalytics.com` → Save. Once DNS verification clears (green check), tick **Enforce HTTPS**.

## When to update the site

Most content can stay static for a year+. The only piece that needs periodic updating:

- **"Accepting N new clients this quarter"** — keep this accurate. If you're fully booked, change to "Currently fully booked — limited availability for Q[X]" or similar. Lying about availability is the fastest way to lose credibility when a prospect emails and you can't actually take them.

Everything else (capabilities, tiers, process, FAQ, work) only needs updates when something materially changes about how you work.

## What's intentionally NOT on this site

- **Testimonials** — you don't have client testimonials yet, and fake ones poison trust. Add them when you have real ones.
- **Hourly rates** — pricing is per engagement, not per hour. Hourly billing creates the consultant-as-employee trap.
- **A blog** — easy to start, hard to maintain, hurts credibility when it goes stale. Add it later if you actually want to write regularly.
- **Mailing list signup** — same logic. Add it when you have something to send.
- **Calendar booking embed** — initially, route everything through email. Embedded Calendly looks like a low-end coaching site. Once volume justifies it, embed it on a separate `/book` page.
- **A physical address** — online-only positioning, as you specified.

These are all *intentional omissions*. Resist consultant-site advice that says "you need testimonials, a blog, a lead magnet, a chatbot." Most of that advice is for a different consultant than you.

---

*Built once. Edit when reality changes.*
