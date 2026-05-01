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
3. Tell Claude: *"create a branch for my name"*
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
