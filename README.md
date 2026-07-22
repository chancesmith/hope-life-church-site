# Hope Life Church Website

Welcome! This is the source code for [hopelifechurch.com](https://hopelifechurch.com).

You don't need to know how to code to help keep this site up to date. If you can edit a document, you can edit this site.

**Want to make a change?** See [UPDATES.md](./UPDATES.md) for step-by-step instructions.

**Want to understand the design?** See [DESIGN.md](./DESIGN.md) for color, font, and layout decisions.

We welcome contributions from anyone in the church. Every update helps people find us.

---

## Pending Updates

- When the church email moves to `@hopelifechurch.com`, update it in 3 spots in `index.html`:
  - JSON-LD contact email (top of file, inside the `<script>` block)
  - Location section mailto link
  - Footer mailto link
- The primary button (`.btn-primary` in `shared.css`) fails contrast: paper text on brass background measures ~3.2:1, below the 4.5:1 floor for normal-size text. True for both the original brand brass (`#B8863B`) and the current burgundy-branch brass. Darken the button text or the brass background.
