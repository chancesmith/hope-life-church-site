# Hope Life Church Site — Agent Instructions

This is the canonical rules file for any AI agent working in this repo (Claude Code, GitHub Copilot, or otherwise). `CLAUDE.md` imports this file directly. `.github/copilot-instructions.md` points here and adds only Copilot-specific notes.

## Project

Static website for Hope Life Church, Jackson, Tennessee. Church-owned: GitHub repo + Netlify hosting. No CMS, no proprietary platform, no monthly platform fees.

## Workflow: design precedes implementation

`DESIGN.md` is a prerequisite, not documentation written after the fact. Before changing `index.html`, `shared.css`, or `card-page.css` in any way that affects layout, color, type, or section structure:

1. Update `DESIGN.md` first to describe the intended end state.
2. Then implement the site change to match it.
3. Commit the `DESIGN.md` change together with (or before) the implementation — never after.

Content-only edits (fixing a typo, updating a phone number, changing a service time) don't require a `DESIGN.md` change. Anything that changes what the site looks like or how it's structured does.

## Tech constraints

- Plain HTML5, CSS3, minimal JavaScript only — there is currently no JavaScript in the site at all
- No frameworks, no build tools, no package.json
- File structure: `shared.css` and `card-page.css` live at repo root (not in a `css/` folder); `images/` is the only subdirectory; no `js/` folder exists
- Semantic HTML, accessible patterns (labels, headings, ARIA where needed, proper contrast)
- Responsive: mobile-first, works on phone/tablet/desktop

## Design system

Colors, fonts, spacing, and layout tokens are defined in `DESIGN.md` §3 (Design tokens) and implemented in `shared.css`'s `:root` block. Do not hardcode or repeat those values here — read them from those two files directly, since duplicating them is exactly how this file went stale before.

**Current state: grayscale placeholder.** `shared.css` right now uses neutral grayscale values (`--ink: #111111`, `--evergreen: #1a1a1a`, `--sand: #f5f5f5`, `--brass: #555555`) with the intended brand colors noted in comments next to each token. The real brand palette has not been finalized — do not "restore" or introduce a colored palette on your own initiative. If asked to explore color options, treat it as a `DESIGN.md`-first change per the Workflow section above, and keep it easy to back out of (a branch, not straight to `main`).

## Church facts

- Name: Hope Life Church
- Location: 1980 Hollywood Dr, Jackson, Tennessee 38305
- Phone: (731) 668-2425
- Email: secretary@poplarheights.com
- Facebook: https://www.facebook.com/hopelifejackson/
- ~50 active members
- Services: Adult Sunday School 9:30 AM, Sunday Worship 10:15 AM, Breakthrough Service 6:00 PM (Sunday evening)
- No children's ministry currently; kids are welcome in service with parents
- Capitalize Him/His/He when referring to God or Jesus throughout the site
- Affiliation: Southern Baptist Convention (SBC); doctrine follows the Baptist Faith & Message 2000 (BF&M 2000)
- Mission: love God, love one another, share Christ's hope with the community

## Site structure

**Current state: single page.** The site is intentionally one page while the church establishes its web presence. Do not add pages without being asked.

| File | Purpose | Status |
|---|---|---|
| `index.html` | Welcome, Beliefs, Services, Location/Contact | Live |
| `404.html` | Not found page | Live |
| `poplarheights.html` | Redirect landing for old Poplar Heights domain | Live |
| `shared.css` | Variables, reset, body base, btn-primary | Live |
| `card-page.css` | Centered card layout (used by 404 + poplarheights) | Live |
| `sitemap.xml` | Sitemap for hopelifechurch.com | Live |
| `events.html` | Dated/time-limited upcoming events | Planned |
| `ministries.html` | Ongoing ministry programs (listing only) | Planned |
| `contact.html` | Dedicated contact form | Planned |

A ministry may reference an upcoming event (e.g., "Youth Group Fall Kickoff — see Events"), but the ministry listing itself is not date-driven.

See `UPDATES.md` for a plain-English guide on how non-technical church members can make edits — either directly on GitHub or by prompting an AI.

## Forms (contact, registration)

**Decision: stub HTML forms now, wire up later.**

Recommended implementation when ready: **Netlify Forms** — free up to 100 submissions/month, no backend, no Google dependency. Just add `netlify` attribute to the `<form>` tag.

Do not use Google Forms. Do not add any external form service without checking back here.

```html
<!-- Netlify Forms — add when ready to go live -->
<form name="contact" method="POST" data-netlify="true">
```

Until then: render the form fields in HTML with a visible note that the form is not yet active.

## Images

- Store in `images/` folder in the repo
- Max file size: 300KB per image
- Max dimensions: 1200px wide (hero/full-width), 800px wide (content)
- Compress before committing: use [squoosh.app](https://squoosh.app) (free, no account)
- For images already hosted elsewhere (church's Facebook, etc.), link directly — do not copy into the repo
- Use descriptive filenames: `sunday-worship-2024.jpg`, not `IMG_4521.jpg`
- Always include `alt` text on every `<img>`

## Videos

- Never store video files in the repo
- Embed via YouTube or Vimeo responsive iframe only
- Wrap all embeds in a responsive container:

```html
<div class="video-wrapper">
  <iframe src="..." allowfullscreen></iframe>
</div>
```

```css
.video-wrapper {
  position: relative;
  padding-bottom: 56.25%; /* 16:9 */
  height: 0;
  overflow: hidden;
}
.video-wrapper iframe {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
}
```

## Live streaming

**Decision: undecided.** Reserve a placeholder section in `index.html` (commented out).

When decided, options to evaluate:

- **YouTube Live** — free, embed same as video above, no extra cost
- **Restream** — broadcast to YouTube + Facebook simultaneously
- **StreamingChurch.tv** — church-focused, paid, includes player embed
- **Facebook Live** — reaches existing FB audience, limited embed options

## Upcoming events vs ongoing ministries

**Events (`events.html`):** things with a specific date, time, and end. Sorted chronologically. Remove or archive after the date passes.

**Ministries (`ministries.html`):** ongoing programs with no end date — Youth Group, Women's Bible Study, Men's Fellowship, etc. Each listing has: name, brief description, when/where it meets, and a contact name or email.

A ministry card may include a callout for an upcoming event ("Youth Group is hosting a Fall Kickoff — [see Events](#)"), but the ministry page itself does not drive event logic.

## Location SEO and metadata

Apply to every page:

```html
<!-- Title pattern -->
<title>Page Name | Hope Life Church | Jackson, TN</title>

<!-- Basic meta -->
<meta name="description" content="[Page-specific description, 150 chars max]">

<!-- Open Graph (social sharing) -->
<meta property="og:title" content="Page Name | Hope Life Church">
<meta property="og:description" content="[Same as meta description]">
<meta property="og:type" content="website">
<meta property="og:url" content="https://hopelifechurch.com/page.html">

<!-- Local business schema — place in <head> of index.html only -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Church",
  "name": "Hope Life Church",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Hope Street",
    "addressLocality": "Jackson",
    "addressRegion": "TN",
    "postalCode": "38301",
    "addressCountry": "US"
  },
  "telephone": "+1-731-668-2425",
  "email": "secretary@poplarheights.com",
  "url": "https://hopelifechurch.com"
}
</script>
```

Also link to Google Business Profile from the contact page footer when one is created.

## Analytics

**Decision: undecided.** Do not add any analytics script without a final decision.

Options when ready:

| Option | Cost | Privacy | Setup |
|---|---|---|---|
| None | Free | Best | None |
| Netlify Analytics | $9/mo | Server-side, no cookies | Dashboard toggle |
| Plausible | $9/mo | No cookies, GDPR-clean | One `<script>` tag |
| Google Analytics 4 | Free | Tracks visitors, cookie consent required | `<script>` tag |

Church preference: no Google Forms — consider whether GA4 fits that same instinct before recommending it.

## Copyright year

The footer copyright year must match the current year. Check and update it on every edit session.

## Agent behavior rules

- Do not add features not explicitly requested (Give button, nav logo, office hours, analytics, etc.) without confirming first.
- When implementing a design spec, flag any elements that require third-party setup (payment platform, analytics, streaming service) before building them.
- For copy/headline changes, offer 3-4 options with previews rather than guessing and iterating.
- Scope changes to exactly what was asked — do not expand to adjacent elements without permission.

## Logo

- File: `images/hlc-logo.png` — white-on-black PNG
- Use `mix-blend-mode: screen` to drop the black background on dark surfaces
- Currently used in: hero h1, footer copyright bar

## Editing rules

- Shared styles live in `shared.css` (variables, reset, body, btn-primary) and `card-page.css` (centered card layout). Page-specific styles stay in an inline `<style>` block on each HTML file.
- Nav must stay consistent across all pages; active page gets `class="active"` on its nav link
- Footer is identical on every page
- Do not introduce external dependencies, CDN links, or JS frameworks
- Content updates (text, times, events) live in the HTML files directly — no templating
- Remove past events from `events.html` once they've passed; don't leave stale dates

## Hosting

- GitHub repo owned by the church
- Auto-deploys to Netlify on push to `main`
- No build step — Netlify serves static files as-is
