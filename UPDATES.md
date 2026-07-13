# How to Update This Website

This site is plain HTML files stored in a GitHub repository and published automatically to the web. You have two ways to make changes.

---

## Option 1 — Ask an AI (easiest)

Open [Claude.ai](https://claude.ai) or [claude.ai/code](https://claude.ai/code) and describe what you want changed. For example:

> "Update the Sunday service time from 10:00 AM to 10:30 AM on the Hope Life Church website."

Then paste the updated code into the file on GitHub (see Option 2 below), or ask someone with access to commit the change.

If the church has a Claude Code setup connected to this repo, an AI agent can make the change directly without anyone writing code.

---

## Option 2 — Edit directly on GitHub

1. Go to the repo on GitHub (ask your site contact for the link if you don't have it).
2. Click the file you want to edit — usually `index.html`.
3. Click the pencil icon (✏️) in the top-right corner of the file.
4. Find the text you want to change and edit it directly.
5. Scroll to the bottom and click **Commit changes**.
6. The site will update automatically within about 60 seconds.

You do not need to install anything or know how to code. If you can edit a Word document, you can edit this site.

---

## What lives where

| What you want to change | Where to find it |
|---|---|
| Church name, tagline | `index.html` — top of file |
| Beliefs / statement of faith | `index.html` — Beliefs section |
| Service times | `index.html` — Services section |
| Address, phone, email | `index.html` — Location section |
| Page colors, fonts | `css/styles.css` (or `<style>` block in `index.html`) |
| Images | Upload to the `images/` folder, then reference as `images/filename.jpg` |

---

## Adding images

1. Keep images under 300KB. Use [squoosh.app](https://squoosh.app) to compress if needed — it's free and runs in your browser.
2. Upload the image to the `images/` folder in the GitHub repo.
3. Reference it in HTML like this: `<img src="images/your-photo.jpg" alt="Describe the photo here">`

---

## What NOT to change

- Do not delete `<!DOCTYPE html>` or other lines at the very top of the file.
- Do not remove `<head>`, `<body>`, or closing tags.
- If something breaks, use GitHub's history to restore a previous version: go to the file, click **History**, and find the last working version.

---

## Design reference

See `design.md` in this repo for color codes, font choices, and layout patterns. If you're asking an AI to redesign something, share that file with it so it matches the existing style.

---

## Questions?

Contact the person who set up this site or open an issue in the GitHub repo.
