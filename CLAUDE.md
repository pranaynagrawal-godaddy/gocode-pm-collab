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
