# Church Website Design Spec

A build-ready design guide for a small-to-midsize local church. Newcomer-first. Swap the tokens in section 3 for your brand, keep the structure in sections 2 and 4.

**This file is a prerequisite, not a record.** Update it to describe the intended end state *before* changing `index.html` or `shared.css` to match — see `AGENTS.md`'s Workflow section.

---

## 1. What this site is for

Rank every decision against these jobs, in order:

1. **A newcomer can answer "when and where do I go?" in under 5 seconds.** This is the whole game. If service time and address are not visible without scrolling, the design failed. *(Today: service times are in the hero; the address is not — it lives in the footer. See [§8 Future Capabilities](#8-future-capabilities).)*
2. **A newcomer can picture walking in.** What to wear and where to park are answered today; what happens to their kids is not yet covered.
3. **A visitor can find what you believe.** The current site publishes the full statement of faith on the homepage rather than a short teaser — thorough, but longer than "short, honest."
4. **A regular can give, watch a sermon, or find an event.** None of these exist yet. The closest equivalent is an external link to the church's bulletin tool for "what's happening this week."

Everything else (staff bios, history, ministry sub-pages) is secondary. Do not let it crowd the top.

---

## 2. Site structure

One page. Home *is* the site — no separate pages for Plan Your Visit, Sermons, Events, or Give exist. Sections live on the homepage as anchors; nav links scroll to them.

```
Home (single page)
├── #expect     (What to Expect — anchor)
├── #beliefs    (What We Believe — anchor)
├── #services   (Service Times — anchor)
└── This Week   (external link, opens in new tab — inthebulletin.com bulletin)
```

A legacy-domain redirect page (`poplarheights.html`) exists for the church's former name. It is `noindex, nofollow` and not part of the navigable sitemap — just a bounce-through for old links and search results.

**Home page section order (top to bottom):**

```
┌─────────────────────────────────────┐
│ Church name       Nav (anchors)      │  ← no persistent Give button
├─────────────────────────────────────┤
│                                       │
│   HERO                                │
│   [Logo]                              │  ← logo image, not a text headline
│   "Sunday School 9:30 • Worship      │
│    10:15 • Breakthrough 6:00"        │  ← all three times, one line
│   [Plan Your Visit]                  │  ← scrolls to #expect, not a separate page
│                                       │
├─────────────────────────────────────┤
│  What to Expect  (3 cards)           │  ← How long? / Who goes here? / What to wear?
│  + Parking & Accessibility notes     │
├─────────────────────────────────────┤
│  What We Believe                     │  ← full statement of faith, not a teaser
├─────────────────────────────────────┤
│  Service Times  (3 cards)            │  ← restates hero times + link to bulletin
├─────────────────────────────────────┤
│  Footer: address, map, times,        │
│  phone, email, social                │
└─────────────────────────────────────┘
```

There is no address in the hero — it lives only in the footer. There is no sermon embed and no events section on the homepage; "what's happening this week" is handled by an external link to the church's bulletin tool, not by content built into the site.

---

## 3. Design tokens

These are the **default direction** — the intended brand palette once one is chosen — not what's live today. **Current state: `shared.css` uses neutral grayscale placeholders** (see the "Current implementation" column below), with the intended brand hex noted in comments next to each token. Do not treat the grayscale values as final, and do not swap in a color palette on your own initiative — that's a `DESIGN.md`-first decision (see Workflow at the top of this file).

### Color

| Token            | Intended brand hex | Current implementation | Use                                        |
|------------------|---------------------|-------------------------|--------------------------------------------|
| `--ink`          | `#1B2A26`           | `#111111`               | Body text, headings on light               |
| `--evergreen`    | `#25443B`           | `#1a1a1a`                | Primary surfaces, footer, hero background  |
| `--sand`         | `#F3EEE3`           | `#f5f5f5`                | Page background, cards                      |
| `--paper`        | `#FFFFFF`           | `#ffffff`                | Card surfaces on sand                       |
| `--brass`        | `#B8863B`           | `#555555`                | Buttons, links, the one accent             |
| `--brass-dark`   | `#8F6829`           | `#222222`                | Button hover / active                       |

Rule: **brass is the only accent.** If everything is highlighted, nothing is. Give buttons get brass; use it nowhere decorative.

### Type

Two faces, three roles. Pick faces with real character but load them from a reliable source (Google Fonts is fine).

- **Display** (headings): a humanist serif with warmth. Currently implemented: `Fraunces` (loaded via Google Fonts, with `Georgia, serif` fallback). Used at large sizes only.
- **Body** (paragraphs, nav, buttons): a clean sans. Currently implemented: `Inter` (with `system-ui, sans-serif` fallback). Do not set body in the display face.

Type scale (rem, 16px base):

```
Hero heading   3.0    weight 600
H2 section     2.0    weight 600
H3 card        1.25   weight 600
Body           1.0    weight 400   line-height 1.6
Small / meta   0.875  weight 500
```

### Spacing & shape

- Space scale: `8, 16, 24, 40, 64, 96` px. Pick from this list, do not freehand.
- Section vertical padding: `64px` mobile, `96px` desktop.
- Border radius: `8px` on cards and buttons. Not zero (feels cold for a church), not pill-round (feels like a startup).
- Max content width: `1120px`, centered.

---

## 4. Section patterns

### Header / nav
Sticky, evergreen background. Church name left (plain text link), anchor links right (`#expect`, `#beliefs`, `#services`) plus one external link, "This Week," to the bulletin tool. No persistent Give button — there's no Give flow to link to. On mobile, links collapse behind a hamburger toggle; the toggle itself stays visible in the bar.

### Hero
Evergreen background, sand text. A centered logo image stands in for a text headline. One subtitle line lists all three service times together ("Sunday School at 9:30 • Worship at 10:15 • Breakthrough at 6:00"). One button, "Plan Your Visit," scrolls down to the What to Expect anchor rather than linking to a separate page. There is no street address in the hero — a newcomer has to reach the footer for that.

### What to expect (3 cards)
Cards ask: **How long?**, **Who goes here?**, **What do I wear?** There is no kids/nursery card — the site doesn't describe child care. Below the cards, two short notes cover **Parking** and **Accessibility**.

### What we believe
The full statement of faith lives on the homepage: an intro paragraph plus an eight-item list (Scripture, God, Man, Salvation, Baptism, The Church, Priesthood of Believers, Eternity). This is the complete statement, not a teaser with a link elsewhere.

### Service times
A dedicated section restates the three service times as cards (name, time, one-line note), plus a link to the current week's bulletin. This exists in addition to the hero's service-time line, not instead of it.

### Footer
Address (linked to Google Maps), all three service times, phone, email, Facebook link, copyright line. This is the second-most-viewed area after the hero, same as before — people scroll here for directions and contact info.

---

## 5. Copy guidance

- Write to the newcomer, not the insider. Avoid unexplained jargon ("small groups" is fine; name-drop your internal program names only after explaining them). Note: "Breakthrough Service" is used as a label without explanation today — fine as a name, but don't let more of these creep in unexplained.
- Buttons say what happens: "Plan Your Visit" is the only button the site has today. If Give or sermon buttons are added later, follow the same pattern ("Give now," "Watch the sermon"), not "Submit" or "Click here."
- Say things plainly. "Sunday School at 9:30 • Worship at 10:15 • Breakthrough at 6:00" beats "Join us as we gather to worship."
- The full statement of faith runs on the home page today, not a one-paragraph teaser. If it grows past what a newcomer will read in one sitting, move it to its own page and leave a short paragraph + link on the home page.

---

## 6. Non-negotiable quality floor

- **Responsive to mobile.** Over half your traffic is a phone in a parking lot on Sunday morning. The site collapses nav into a hamburger and resizes the hero below 768px — verified in the current CSS.
- **Accessible.** Text contrast on the current grayscale placeholder: ink-on-sand and sand-on-evergreen both pass comfortably (17.3:1 and 16.0:1). The primary button (paper text on `--brass`) also passes today at ~7.5:1 — but that's a property of the current grayscale value, not a guarantee. The two brand-brass candidates evaluated so far (`#B8863B` and a burgundy-branch variant) both measured around 3.2-3.3:1, below the 4.5:1 floor for normal-size text. **Recheck contrast against the 4.5:1 floor whenever a real brand palette is chosen** — don't assume it still passes once `--brass` stops being gray. Keyboard focus rings are unstyled but not suppressed, so the browser default still shows. Alt text is present on the logo image.
- **Fast.** Compress images. The one image in use (`hlc-logo.png`) is 22KB — well within budget.
- **Reduced motion respected.** `shared.css` already sets `scroll-behavior: auto` under `prefers-reduced-motion: reduce`.

---

## 7. Build notes

- Static site is enough for most churches (plain HTML/CSS, or a builder like Astro, Eleventy, or even a hosted platform). You do not need a database. This site is plain HTML/CSS, no build step.
- The current site links out to a third-party bulletin tool (inthebulletin.com) rather than embedding a giving platform, sermon host, or calendar directly. If any of those get embedded later, do it the same way: link straight to the tool you already use, don't build a payment system or video host from scratch.
- Keep the whole thing something one volunteer can update. If updating service times requires a developer, the design failed.

---

## 8. Future capabilities

These are described in earlier sections as the design's intent but are not built yet. Not todos, not a backlog with owners or dates, just documented gaps between the spec and the live site so nobody mistakes their absence for an oversight.

- **Brand color palette.** `shared.css` currently uses grayscale placeholders. A real brand palette has not been finalized — see §3.
- **Give.** No Give button, no Give page, no link to a giving platform anywhere on the site.
- **Latest sermon.** No video/audio embed and no link to a sermon archive.
- **Events / calendar.** No on-page events list. The "This Week" nav link points to an external bulletin tool instead of a built-in calendar section.
- **Kids / nursery info.** The What to Expect cards don't answer "what happens to my kids" — there's no nursery or children's ministry card.
- **Multi-page structure.** Plan Your Visit, About/Beliefs, Sermons, Events, and Contact are all anchors on the single homepage today, not separate pages. Worth splitting out if any one section's content grows past what fits in a homepage scroll.
- **Address in the hero.** The street address lives only in the footer; a newcomer has to scroll past several sections to find it.
