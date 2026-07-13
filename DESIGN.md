# Church Website Design Spec

A build-ready design guide for a small-to-midsize local church. Newcomer-first. Swap the tokens in section 3 for your brand, keep the structure in sections 2 and 4.

---

## 1. What this site is for

Rank every decision against these jobs, in order:

1. **A newcomer can answer "when and where do I go?" in under 5 seconds.** This is the whole game. If service time and address are not visible without scrolling, the design failed.
2. **A newcomer can picture walking in.** What to wear, where to park, what happens to their kids, how long it runs.
3. **A visitor can find what you believe.** Short, honest, not a doctrinal thesis.
4. **A regular can give, watch a sermon, or find an event.** Fast, no login gymnastics.

Everything else (staff bios, history, ministry sub-pages) is secondary. Do not let it crowd the top.

---

## 2. Site structure

Minimum viable sitemap. Do not add pages until these work.

```
Home
├── Plan Your Visit      (the most important page after Home)
├── About / Beliefs
├── Sermons / Watch
├── Events / Calendar
├── Give
└── Contact
```

**Home page section order (top to bottom):**

```
┌─────────────────────────────────────┐
│ Logo            Nav        [Give]    │  ← Give button always visible
├─────────────────────────────────────┤
│                                       │
│   HERO                                │
│   "Sundays at 9 & 11am"              │  ← time + place first, not a slogan
│   123 Main St, Your Town             │
│   [Plan Your Visit]                  │
│                                       │
├─────────────────────────────────────┤
│  What to expect  (3 short cards)     │  ← kills newcomer anxiety
├─────────────────────────────────────┤
│  Latest sermon   (embed + link)      │
├─────────────────────────────────────┤
│  This week's events  (2–3 items)     │
├─────────────────────────────────────┤
│  Who we are  (one paragraph + link)  │
├─────────────────────────────────────┤
│  Footer: address, map, times, social│
└─────────────────────────────────────┘
```

The hero leads with logistics, not a mission statement. A slogan makes an anxious first-time visitor work; a time and an address answers their actual question.

---

## 3. Design tokens

These are the **default direction**, chosen to avoid the generic "warm cream + serif + terracotta" look that reads as templated. Deep evergreen suggests stability and rootedness; warm sand keeps it welcoming; brass is the one accent for calls to action. **Swap these for your church's brand colors and fonts.** Keep the roles and the ratios.

### Color

| Token            | Hex        | Use                                        |
|------------------|------------|--------------------------------------------|
| `--ink`          | `#1B2A26`  | Body text, headings on light               |
| `--evergreen`    | `#25443B`  | Primary surfaces, footer, hero background  |
| `--sand`         | `#F3EEE3`  | Page background, cards                      |
| `--paper`        | `#FFFFFF`  | Card surfaces on sand                       |
| `--brass`        | `#B8863B`  | Buttons, links, the one accent             |
| `--brass-dark`   | `#8F6829`  | Button hover / active                       |

Rule: **brass is the only accent.** If everything is highlighted, nothing is. Give buttons get brass; use it nowhere decorative.

### Type

Two faces, three roles. Pick faces with real character but load them from a reliable source (Google Fonts is fine).

- **Display** (headings): a humanist serif with warmth. Default: `Fraunces` or `Source Serif 4`. Used at large sizes only.
- **Body** (paragraphs, nav, buttons): a clean sans. Default: `Inter` or `Public Sans`. Do not set body in the display face.

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
Sticky. Logo left, links center or right, **Give button always visible** (brass). On mobile, collapse links to a hamburger but keep Give in the bar.

### Hero
Evergreen background, sand text. Heading is the service time. One line for address. One button: "Plan Your Visit" (brass). Optional: a real photo of your actual congregation, not stock. Stock photos of generic worshippers read as inauthentic and newcomers notice.

### What to expect (3 cards)
Answers the unspoken questions. Suggested cards: **How long?** ("About 70 minutes"), **My kids?** ("Check-in for nursery through 5th grade"), **What do I wear?** ("Come as you are"). Plain answers, no marketing.

### Latest sermon
Embed the most recent video or audio. One click to the full archive. Do not gate it behind a form.

### Events
Two or three upcoming items with date, time, and a one-line description. Link to the full calendar. An empty calendar is worse than none, so if events are sparse, show fewer and keep them current.

### Give
A dedicated page and a persistent button. State clearly what giving supports. Link straight to your existing giving platform. Do not build a payment system; embed the one you already use.

### Footer
Address (linked to a map), all service times, phone, email, social links. This is the second-most-viewed area after the hero because people scroll here to find directions. Treat it as primary content, not an afterthought.

---

## 5. Copy guidance

- Write to the newcomer, not the insider. Avoid unexplained jargon ("small groups" is fine; name-drop your internal program names only after explaining them).
- Buttons say what happens: "Plan Your Visit," "Watch the sermon," "Give now." Not "Submit," not "Click here."
- Say things plainly. "Sundays at 9 and 11am" beats "Join us as we gather to worship."
- One paragraph of beliefs on the home page, full statement on its own page for those who want it.

---

## 6. Non-negotiable quality floor

- **Responsive to mobile.** Over half your traffic is a phone in a parking lot on Sunday morning. Test the hero and directions on a narrow screen first.
- **Accessible.** Text contrast at least 4.5:1 (evergreen-on-sand and ink-on-sand both pass; check any brand swap). Visible keyboard focus on every link and button. Alt text on images.
- **Fast.** Compress images. A church site should load in under 3 seconds on mobile data.
- **Reduced motion respected.** If you add scroll animations, disable them for users who set `prefers-reduced-motion`.

---

## 7. Build notes

- Static site is enough for most churches (plain HTML/CSS, or a builder like Astro, Eleventy, or even a hosted platform). You do not need a database.
- Embed third-party tools rather than building them: giving platform, sermon host (YouTube / Vimeo / a podcast host), calendar.
- Keep the whole thing something one volunteer can update. If updating service times requires a developer, the design failed.
