# Hope Life Church Site — Agent Context

## Project

Static website for Hope Life Church, Jackson, Tennessee. Church-owned: GitHub repo + Netlify hosting. No CMS, no proprietary platform, no monthly platform fees.

## Tech constraints

- Plain HTML5, CSS3, minimal JavaScript only
- No frameworks, no build tools, no package.json
- File structure: `css/`, `images/`, `js/` subdirectories
- Semantic HTML, accessible patterns (labels, headings, ARIA where needed, proper contrast)
- Responsive: mobile-first, works on phone/tablet/desktop

## Design system

- Primary color: `#2c5f2d` (forest green)
- Dark variant: `#1e4620`
- Light tint: `#f0f7f0`
- Body text: `#333`
- Muted text: `#555`
- Background: `#f9f9f9`
- Font stack: `'Segoe UI', Tahoma, Geneva, Verdana, sans-serif`
- Tone: warm, welcoming — not corporate
- Card style: white bg, `border-radius: 4px`, `box-shadow: 0 1px 3px rgba(0,0,0,0.1)`
- Section headings: green with 2px green bottom border

If a `design.md` file exists in the root, it overrides these defaults.

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
<meta property="og:url" content="https://hopelifechurch.org/page.html">

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
  "telephone": "+1-731-555-0101",
  "email": "hello@hopelifechurch.org",
  "url": "https://hopelifechurch.org"
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

The footer copyright year must match the current year. Check and update it on every edit session. Current year: 2026.

## Editing rules

- Keep all styles in `css/styles.css` (or inline `<style>` block if file not yet extracted)
- Nav must stay consistent across all pages; active page gets `class="active"` on its nav link
- Footer is identical on every page
- Do not introduce external dependencies, CDN links, or JS frameworks
- Content updates (text, times, events) live in the HTML files directly — no templating
- Remove past events from `events.html` once they've passed; don't leave stale dates

## Hosting

- GitHub repo owned by the church
- Auto-deploys to Netlify on push to `main`
- No build step — Netlify serves static files as-is
