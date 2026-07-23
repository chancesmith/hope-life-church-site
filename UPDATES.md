# How to Update This Website

This site is plain HTML files stored in a GitHub repository and published automatically to the web via Netlify. You do not need to know how to code to make updates.

---

## Seeing Your Changes Live

After any change is made to the **main** branch, Netlify automatically rebuilds and publishes the site. This usually takes about 60 seconds. Just visit [hopelifechurch.com](https://hopelifechurch.com) and refresh the page.

If a change was made to a separate branch (not main), it will not appear on the live site until that branch is merged in. A collaborator with access can review and approve the change first — this is the safer workflow when you're not sure about a change.

---

## Two Ways to Make Changes

### Option 1 — Ask an AI Agent (easiest, ~$10/month)

GitHub has a built-in AI agent that can make changes for you. No coding required.

1. Go to the repo on GitHub.
2. Click the **Agents** tab.
3. Describe what you want changed in plain language. For example:
   > "Update the Sunday service time to 10:30 AM in the services section."
4. The agent will automatically create a new branch with the change.
5. A collaborator can then review it and merge it into the live site when ready.

This option requires a GitHub Copilot subscription (~$10/month per account). If cost is a barrier, Option 2 is always free.

---

### Option 2 — Edit Files Directly on GitHub (free)

1. Go to the repo on GitHub (ask your site contact for the link if you don't have it).
2. Click the **Code** tab.
3. Click the file you want to edit — usually `index.html`.
4. Click the pencil icon (✏️) in the top-right corner of the file.
5. Find the text you want to change and edit it.
6. Scroll to the bottom. You have two choices:

   **Commit directly to main** — the change goes live in about 60 seconds. Use this for small, confident corrections (fixing a typo, updating a phone number).

   **Create a new branch** — the change is saved but does not go live yet. Someone with access can review it first and decide when to merge it. This is the safer choice when you're not sure.

You do not need to install anything. If you can edit a Word document, you can edit this site.

---

### Option 3 — Describe a Change to an AI, Then Paste It In

Open [Claude.ai](https://claude.ai) and describe what you want changed. For example:

> "Update the Sunday service time from 10:00 AM to 10:30 AM."

The AI will give you updated code. Then use Option 2 above to paste it into the file on GitHub.

If you share the `DESIGN.md` file with the AI, it will match the existing style more accurately.

---

## What Lives Where

| What you want to change | Where to find it |
|---|---|
| Church name, tagline | `index.html` — top of file |
| Beliefs / statement of faith | `index.html` — Beliefs section |
| Service times | `index.html` — Services section |
| Address, phone, email | `index.html` — Location section |
| Page colors, fonts | `shared.css` |
| Images | `images/` folder |

---

## Adding Images

1. Keep images under 300 KB. Use [squoosh.app](https://squoosh.app) to compress — free, runs in your browser.
2. Upload the image to the `images/` folder in the GitHub repo.
3. Reference it in HTML: `<img src="images/your-photo.jpg" alt="Describe the photo">`

---

## Inviting Others to Help

Anyone can be added as a collaborator so they can make changes too.

1. Go to the repo on GitHub.
2. Click the **Settings** tab.
3. Click **Collaborators** in the left menu.
4. Enter the person's GitHub username or email and send the invite.

We want this site to be something the whole church can contribute to. The more hands, the better.

---

## What NOT to Change

- Do not delete `<!DOCTYPE html>` or lines at the very top of the file.
- Do not remove `<head>`, `<body>`, or closing tags.
- If something breaks, use GitHub's history to restore a previous version: go to the file, click **History**, and find the last working version.

---

## Design Reference

See `DESIGN.md` for color codes, font choices, and layout decisions. Share that file with an AI when asking for design changes so it matches the existing style.

If you're asking for a look-and-feel change (new colors, fonts, layout, section order), ask the AI to update `DESIGN.md` as part of that same request, not just the page itself. `DESIGN.md` is meant to describe the site's intended design before the code matches it — if it goes out of date, the next person (human or AI) is working from a wrong picture of the site.
