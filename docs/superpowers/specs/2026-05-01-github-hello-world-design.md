# Design: GoCode PM GitHub "Hello World" Exercise Page

**Date:** 2026-05-01  
**Repo:** `gocode-pm-collab`  
**Context:** Week 3 of the GoCode PM Accelerator — introductory GitHub exercise for PMs who are new to version control.

---

## Goal

A GitHub Pages site where each PM in the cohort adds a name card as their first GitHub contribution. The exercise teaches: clone → branch → edit (via Claude Code) → commit → push → pull request → facilitator merges → live deploy.

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The live cohort wall page |
| `CLAUDE.md` | Auto-loaded instructions so Claude knows exactly what to do on clone |
| `.github/workflows/deploy.yml` | GitHub Actions: deploy to Pages on push to main |
| `README.md` | Facilitator setup guide |

---

## `index.html`

### Structure
- **Header**: "GoCode PM Cohort — Week 3" + one-line subtitle
- **Intro box**: 2–3 sentences explaining what the page is and what the PM will add
- **Card grid**: CSS grid, pure HTML + inline CSS, no JS, no dependencies
- **Insertion markers**:
  ```html
  <!-- ADD YOUR CARD BELOW THIS LINE -->
  ...cards go here...
  <!-- ADD YOUR CARD ABOVE THIS LINE -->
  ```
- **Starter card**: One pre-filled demo card (e.g., "Pranay Agrawal — Product Manager") so PMs see the expected pattern

### Card template
```html
<div class="card">
  <div class="card-name">First Last</div>
  <div class="card-title">Title</div>
</div>
```

### CSS principles
- Self-contained in a `<style>` block — no external stylesheets
- Card grid: `display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr))`
- Clean, professional look consistent with GoCode PM Accelerator visual style (dark background, teal accents)
- No JavaScript

---

## `CLAUDE.md`

Loaded automatically when a PM opens the cloned repo in Claude Code. Contains:

1. **What this repo is** — one sentence
2. **Exercise steps** — numbered, copy-pasteable prompts the PM can say to Claude:
   - Step 1: Clone (done before opening Claude Code)
   - Step 2: `create a branch called add-[your-name]`
   - Step 3: `add me to the cohort page — my name is [Name], my title is [Title]`
   - Step 4: `commit and push my changes`
   - Step 5: Open PR on GitHub (instruction with URL)
3. **Card insertion rule**: Claude adds the card inside the marker comments, after the last existing card
4. **Exact card HTML template** (so Claude produces consistent output)
5. **Branch naming convention**: `add/firstname-lastname`
6. **Commit message format**: `add [Name] card`
7. **Scope constraint**: Only touch the card section between the markers — do not modify anything else

---

## `.github/workflows/deploy.yml`

- **Trigger**: `push` to `main`
- **Action**: Official GitHub Pages deployment using `actions/configure-pages`, `actions/upload-pages-artifact`, and `actions/deploy-pages`
- **Source**: Repo root (static files, no build step)
- **Permissions**: `pages: write`, `id-token: write`
- **Result**: Site live at `https://<org>.github.io/gocode-pm-collab/` within ~30 seconds of merge

---

## `README.md`

Facilitator-facing. Covers:
- One-time GitHub Pages setup (Settings → Pages → Deploy from branch: main / root)
- How to review and merge a PM's PR
- Expected live URL after deploy

---

## Exercise Flow (end-to-end)

1. PM clones `gocode-pm-collab` via GitHub Desktop
2. Opens Claude Code in the cloned folder
3. Claude reads `CLAUDE.md` automatically
4. PM says: *"create a branch called add-[name]"*
5. PM says: *"add me to the cohort page — my name is X, my title is Y"*
6. Claude edits `index.html` between the markers using the card template
7. PM says: *"commit and push my changes"*
8. PM opens a PR on GitHub
9. Facilitator reviews and merges
10. GitHub Actions deploys → card is live on the cohort wall

---

## Constraints

- No npm, no build tools, no dependencies — pure static HTML
- Single file edit per PR (reduces conflict surface to the card section only)
- Sequential PR merging by facilitator eliminates merge conflicts in practice
- Card section markers make the insertion point unambiguous for Claude
