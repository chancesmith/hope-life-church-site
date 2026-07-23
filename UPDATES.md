# How to Update This Website

This site is plain files that update automatically when changes are saved. You don't need to know how to code.

---

## New to This? Start Here

1. **Get access.** Ask whoever manages the site to add you (see "Inviting Others to Help" below). Without this you can suggest changes but not save them.
2. **Pick your path**, based on budget and comfort:
   - Want an AI to make the change for you, hands-off, $10/month is fine → **Option 1**. Recommended for most people.
   - Free, comfortable following on-screen steps → **Option 2**.
   - Already chat with an AI day-to-day and just want help wording or coding the change → **Option 3**.
3. **Changing colors, fonts, or layout** (not just wording or a time)? Read `DESIGN.md` first, or share it with your AI. See Design Reference below.

---

## New to AI? Try It Risk-Free First

Before your first real edit, ask an AI something small to get a feel for it. Try one of these in Claude.ai, ChatGPT, or GitHub Copilot Chat:

> "Here's a file from my church's website. Can you explain what this section does?" (paste in a chunk of `index.html`)

> "If I wanted to change the Sunday service time, what would I need to tell you?"

None of these change the site, so there's nothing to get wrong. Once it feels comfortable, move to Option 1, 2, or 3 below.

---

## Seeing Your Changes Live

Saved changes go live in about 60 seconds. Visit [hopelifechurch.com](https://hopelifechurch.com) and refresh.

If a change was saved for review instead of going live right away, it won't appear until someone with access approves it. That's the safer path when you're not sure about a change.

---

## Three Ways to Make Changes

### Option 1: Ask GitHub Copilot's Agent (recommended, ~$10/month)

An AI built into GitHub that makes changes for you. No coding required.

1. Go to the repo on GitHub.
2. Click the **Agents** tab.
3. Describe what you want in plain language, e.g.:
   > "Update the Sunday service time to 10:30 AM in the services section."
4. The agent saves the change for review.
5. Someone with access reviews it and publishes it live.

Requires a Copilot subscription (~$10/month). If cost is a barrier, Option 2 is free.

---

### Option 2: Edit Files Directly on GitHub (free)

1. Go to the repo on GitHub (ask your site contact for the link if needed).
2. Click **Code**, then click the file you want (usually `index.html`).
3. Click the pencil icon (✏️) top-right.
4. Edit the text.
5. Scroll down and choose:
   - **Save directly**: goes live in about 60 seconds. Use for small, confident fixes (typo, phone number).
   - **Save for review**: someone with access checks it before it goes live. Safer when unsure.

No install needed. If you can edit a Word document, you can edit this site.

---

### Option 3: Describe the Change to Any AI Chatbot, Then Paste It In (free)

Already use Claude.ai, ChatGPT, GitHub Copilot Chat, or similar? Describe the change, e.g.:

> "Update the Sunday service time from 10:00 AM to 10:30 AM."

The AI gives you updated code. Paste it in using Option 2 above.

Share the `DESIGN.md` file with the AI so it matches the site's style.

---

**Technical volunteer using Claude Code or a terminal-based coding tool?** They can edit and publish directly, similar to Option 1, but it needs a technical setup. Good fit if your church has someone comfortable with that. `AGENTS.md` has the rules they should follow.

---

## What Lives Where

| What you want to change | Where to find it |
|---|---|
| Church name, tagline | `index.html`, top of file |
| Beliefs / statement of faith | `index.html`, Beliefs section |
| Service times | `index.html`, Services section |
| Address, phone, email | `index.html`, Location section |
| Page colors, fonts | `shared.css` |
| Images | `images/` folder |

---

## Adding Images

1. Keep images under 300 KB. Use [squoosh.app](https://squoosh.app) to compress. Free, runs in your browser.
2. Upload the image to the `images/` folder in the repo.
3. Reference it in HTML: `<img src="images/your-photo.jpg" alt="Describe the photo">`

---

## Inviting Others to Help

1. Go to the repo on GitHub.
2. Click **Settings** → **Collaborators**.
3. Enter the person's GitHub username or email and send the invite.

The more hands, the better.

---

## What NOT to Change

- Don't delete anything at the very top of `index.html` or its opening/closing structure.
- If something breaks, GitHub keeps history. Open the file, click **History**, and restore the last working version.

---

## Design Reference

See `DESIGN.md` for color codes, font choices, and layout decisions. Share it with an AI when asking for design changes so it matches the existing style.

Asking for a look-and-feel change (new colors, fonts, layout, section order)? Ask the AI to update `DESIGN.md` as part of the same request, not just the page. Otherwise the next person is working from an outdated picture of the site.
