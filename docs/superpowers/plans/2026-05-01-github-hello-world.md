# GitHub Hello World Exercise Page — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the GoCode PM Week 3 exercise — a GitHub Pages cohort wall where each PM adds a name card via PR.

**Architecture:** Four static files at the repo root. No build tools, no dependencies. GitHub Actions deploys the root directory to Pages on every push to main. CLAUDE.md auto-loads in Claude Code so PMs can complete the exercise with plain-English prompts.

**Tech Stack:** Pure HTML/CSS, GitHub Actions (`actions/checkout@v4`, `actions/configure-pages@v5`, `actions/upload-pages-artifact@v3`, `actions/deploy-pages@v4`)

---

## File Map

| File | Action | Responsibility |
|---|---|---|
| `index.html` | Create | Cohort wall — header, intro, card grid, marker comments, demo card |
| `CLAUDE.md` | Create | Auto-loaded exercise instructions + card template for Claude Code |
| `.github/workflows/deploy.yml` | Create | GitHub Actions Pages deploy on push to main |
| `README.md` | Create | Facilitator one-time setup guide |

---

## Task 1: Create `index.html`

**Files:**
- Create: `index.html`

- [ ] **Step 1: Write the file**

Create `/index.html` with the full content below:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GoCode PM Cohort — Week 3</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: #0F1923;
      color: #E2E8F0;
      min-height: 100vh;
      padding: 48px 24px;
    }
    .header { text-align: center; margin-bottom: 40px; }
    .header h1 {
      font-size: 2rem; font-weight: 800;
      color: #fff; letter-spacing: -0.02em;
    }
    .header .subtitle { font-size: 1rem; color: #94A3B8; margin-top: 8px; }
    .teal { color: #00D9A0; }
    .intro {
      max-width: 640px; margin: 0 auto 48px;
      background: rgba(0, 217, 160, 0.07);
      border: 1px solid rgba(0, 217, 160, 0.25);
      border-radius: 12px; padding: 20px 24px;
      font-size: 0.92rem; line-height: 1.7; color: #CBD5E1;
    }
    .intro strong { color: #00D9A0; }
    .section-label {
      text-align: center; font-size: 0.72rem; font-weight: 800;
      letter-spacing: 0.12em; text-transform: uppercase;
      color: #64748B; margin-bottom: 24px;
    }
    .card-grid {
      max-width: 900px; margin: 0 auto;
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 16px;
    }
    .card {
      background: #1E2A38; border: 1px solid #2D3F52;
      border-radius: 12px; padding: 20px 16px;
      transition: border-color 0.2s;
    }
    .card:hover { border-color: #00D9A0; }
    .card-name { font-size: 1rem; font-weight: 700; color: #F1F5F9; margin-bottom: 4px; }
    .card-title { font-size: 0.82rem; color: #94A3B8; }
    .footer {
      text-align: center; margin-top: 64px;
      font-size: 0.78rem; color: #475569;
    }
  </style>
</head>
<body>
  <div class="header">
    <h1>GoCode PM Cohort <span class="teal">·</span> Week 3</h1>
    <p class="subtitle">The GitHub Hello World — your first contribution to a shared repo.</p>
  </div>

  <div class="intro">
    This page is built by the cohort, one pull request at a time.
    <strong>Your job:</strong> add your card below. Clone this repo, create a branch,
    tell Claude your name and title, commit, push, and open a PR.
    Once the facilitator merges it, your card goes live here automatically.
  </div>

  <p class="section-label">The Cohort</p>

  <div class="card-grid">

    <!-- ADD YOUR CARD BELOW THIS LINE -->

    <div class="card">
      <div class="card-name">Pranay Agrawal</div>
      <div class="card-title">Product Manager</div>
    </div>

    <!-- ADD YOUR CARD ABOVE THIS LINE -->

  </div>

  <div class="footer">
    GoCode PM Accelerator &mdash; GoDaddy Commerce
  </div>
</body>
</html>
```

- [ ] **Step 2: Verify in browser**

Open `index.html` directly in a browser (double-click the file or drag it into Chrome).

Expected:
- Dark background (`#0F1923`)
- "GoCode PM Cohort · Week 3" header with teal dot
- Teal-bordered intro box with exercise description
- "THE COHORT" section label
- One card: "Pranay Agrawal / Product Manager" with hover highlight

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "add cohort wall index.html"
```

---

## Task 2: Create `CLAUDE.md`

**Files:**
- Create: `CLAUDE.md`

- [ ] **Step 1: Write the file**

Create `/CLAUDE.md` with the full content below:

```markdown
# CLAUDE.md — GoCode PM Cohort Wall

This repo is the Week 3 GitHub exercise for the GoCode PM Accelerator.
Your job is to help a product manager add their card to the cohort wall in `index.html`.

## Exercise Steps

Walk the PM through these steps in order:

### Step 1 — Create a branch

When the PM says "create a branch" or similar, run:

```bash
git checkout -b add/firstname-lastname
```

Replace `firstname-lastname` with their actual name in lowercase, hyphenated
(e.g., `add/alex-chen`, `add/maria-santos`).

### Step 2 — Add their card

When the PM says "add me to the cohort page" (or similar), edit `index.html`.

Find the section between these two comments:

```html
<!-- ADD YOUR CARD BELOW THIS LINE -->
<!-- ADD YOUR CARD ABOVE THIS LINE -->
```

Insert their card **after the last existing card** and **before**
`<!-- ADD YOUR CARD ABOVE THIS LINE -->`, using this exact template:

```html
    <div class="card">
      <div class="card-name">First Last</div>
      <div class="card-title">Their Title</div>
    </div>
```

### Step 3 — Commit and push

When the PM says "commit and push" or similar, run:

```bash
git add index.html
git commit -m "add [Name] card"
git push origin add/firstname-lastname
```

Replace `[Name]` with their first name and `add/firstname-lastname` with their branch name.

### Step 4 — Open a PR

Tell the PM:

> Go to the repo on GitHub. You should see a yellow banner:
> **"Compare & pull request"** — click it and submit.
> Don't merge it yourself — the facilitator will review and merge.

## Rules

- **Only edit `index.html`** — specifically the card section between the two marker comments
- Do not modify any other file
- Do not change or remove existing cards
- Branch name format: `add/firstname-lastname` (lowercase, hyphenated)
- Commit message format: `add [Name] card`
```

- [ ] **Step 2: Verify content**

Read through the file and confirm:
- All 4 steps are present
- The card template exactly matches the one in `index.html`
- Branch naming rule is explicit (`add/firstname-lastname`)
- Scope constraint ("only edit `index.html`") is clearly stated

- [ ] **Step 3: Commit**

```bash
git add CLAUDE.md
git commit -m "add CLAUDE.md with exercise instructions for Claude Code"
```

---

## Task 3: Create `.github/workflows/deploy.yml`

**Files:**
- Create: `.github/workflows/deploy.yml`

- [ ] **Step 1: Create the directory and file**

```bash
mkdir -p .github/workflows
```

Create `.github/workflows/deploy.yml` with this exact content:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

- [ ] **Step 2: Verify YAML is valid**

```bash
python3 -c "import yaml; yaml.safe_load(open('.github/workflows/deploy.yml'))" && echo "YAML valid"
```

Expected output: `YAML valid`

- [ ] **Step 3: Commit**

```bash
git add .github/workflows/deploy.yml
git commit -m "add GitHub Actions Pages deploy workflow"
```

---

## Task 4: Create `README.md`

**Files:**
- Create: `README.md`

- [ ] **Step 1: Write the file**

Create `/README.md` with the full content below:

```markdown
# GoCode PM Cohort Wall

GitHub Pages site for the Week 3 exercise in the GoCode PM Accelerator.
Each PM adds their card to this page as their first GitHub contribution.

---

## One-Time Setup (Facilitator)

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, select **GitHub Actions**
4. Done — the workflow deploys automatically on every push to `main`

**Live URL:** `https://<your-org>.github.io/gocode-pm-collab/`

---

## Reviewing PRs

When a PM opens a PR:

1. Click **Files changed** — you should see one `<div class="card">` block added between the two marker comments in `index.html`
2. Check the name and title look correct
3. Click **Merge pull request**
4. Watch the **Actions** tab — the page goes live within ~30 seconds

---

## Exercise Flow (What PMs Do)

1. Clone this repo via GitHub Desktop
2. Open Claude Code in the cloned folder
3. Tell Claude: *"create a branch called add-[their-name]"*
4. Tell Claude: *"add me to the cohort page — my name is X, my title is Y"*
5. Tell Claude: *"commit and push my changes"*
6. Go to GitHub → click **Compare & pull request** → submit
7. Facilitator merges → card goes live automatically

---

## Troubleshooting

**PM gets a merge conflict:** Have them pull the latest main and re-apply their card.
Run: `git pull origin main` then re-add the card and push again.

**Actions workflow not running:** Confirm Pages source is set to **GitHub Actions**
(not "Deploy from a branch") in Settings → Pages.
```

- [ ] **Step 2: Verify content**

Read through and confirm:
- One-time Pages setup steps are correct (Settings → Pages → GitHub Actions)
- PR review steps match the actual workflow
- Troubleshooting covers the two most likely failure modes

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "add facilitator README"
```

---

## Task 5: Final verification

- [ ] **Step 1: Check all four files exist**

```bash
ls index.html CLAUDE.md README.md .github/workflows/deploy.yml
```

Expected: all four paths listed with no errors.

- [ ] **Step 2: Check git log**

```bash
git log --oneline
```

Expected output (newest first):
```
<hash> add facilitator README
<hash> add GitHub Actions Pages deploy workflow
<hash> add CLAUDE.md with exercise instructions for Claude Code
<hash> add cohort wall index.html
<hash> add design spec for GitHub Hello World exercise page
<hash> Initial commit
```

- [ ] **Step 3: Open index.html one final time**

Open `index.html` in a browser and confirm the page looks correct end-to-end before pushing to GitHub.

- [ ] **Step 4: Note for facilitator — push and enable Pages**

After pushing to GitHub, complete the one-time Pages setup:

1. `git remote add origin https://github.com/<org>/gocode-pm-collab.git`
2. `git push -u origin main`
3. Go to **Settings → Pages → Source → GitHub Actions**
4. The first deploy triggers automatically on push — watch the **Actions** tab
