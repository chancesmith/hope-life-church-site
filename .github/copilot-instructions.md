# Copilot Instructions

See [`AGENTS.md`](../AGENTS.md) at the repo root for the full rules (project facts, workflow, tech constraints, design system, editing rules). This file only adds notes specific to GitHub Copilot's coding agent.

- No build, test, or lint step exists or should be added — this is plain static HTML/CSS, served as-is by Netlify.
- Non-technical church staff or volunteers review your pull requests. Keep diffs small, reversible, and easy to review in GitHub's file-diff view.
