# NI 360 Static Ad Framework — team hub

A static-HTML team hub for the NI 360 static ad testing framework. Six pages:

- `index.html` — Home (tracker embed + current round status)
- `playbook.html` — The framework, gates, exit conditions
- `roles.html` — Jordan / Ryan / Parm / Leo
- `competitor.html` — Scan set, gaps, candidates to add
- `templates.html` — Approach templates and briefs
- `results.html` — Round-by-round results

Styles live in `assets/style.css`. Dark theme, NI orange accent. No build step — open `index.html` directly in a browser to preview locally.

---

## Publishing to GitHub Pages

The site is designed to be hosted on GitHub Pages. One-time setup:

### 1. Push to a new repo

```bash
cd /Users/jordan.kennard/Documents/Claude/Projects/Work/NI_360_Ad_Framework/site
git init
git add .
git commit -m "Initial NI 360 framework hub"
git branch -M main
# Create the repo on github.com first (private is fine)
git remote add origin https://github.com/<your-username>/ni-360-framework.git
git push -u origin main
```

### 2. Enable Pages

- Go to the repo → **Settings** → **Pages**
- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Save

The site will be live at `https://<your-username>.github.io/ni-360-framework/` within a minute or two.

### 3. (Optional) Custom domain

If NI has a `ni360.native-instruments.com` style subdomain, add a `CNAME` file with the domain name and point DNS at GitHub Pages per [the GitHub docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

---

## Sharing the tracker Sheet

The home page embeds the Google Sheet at:

```
https://docs.google.com/spreadsheets/d/1p_AmG7aTjeJiSifNN6ovVn6mrYgyHlk9WPwjsRECyRQ/preview?rm=minimal
```

For the iframe to actually render for the team, **the Sheet must be shared**:

- Open the Sheet
- Click **Share**
- Either share with the NI domain (native-instruments.com) with **Viewer** access, or share with specific team emails (Ryan, Parm, Leo, plus anyone else who needs view access)
- Copy the share link if you want a fallback "open in new tab" route (already linked from the home page)

If the team isn't signed into their NI Google account when they visit the hub, the iframe will show a sign-in prompt. The "Open full Sheet" link gives them a direct route.

---

## Updating the site

### Content updates (most common)

Edit the HTML files directly. Each page is self-contained — no templating, no includes. If the nav links change, update each file's `<nav>` block (or refactor into a shared include later).

### Rollup changes

1. Edit locally
2. `git add . && git commit -m "Update playbook gates" && git push`
3. GitHub Pages rebuilds automatically within a minute

### Round recap workflow (per round)

When a round closes:

1. Update `results.html` — move the closed round from "live" to "closed", fill in the recap card, add the retired approach to the "Retired approaches" section
2. Update `index.html` — update the KPI block (current round number) and the Round table (new approaches)
3. Update `competitor.html` — append the new round's scan block above the previous one
4. Commit and push

---

## Files in this folder

```
site/
├── README.md                 (this file)
├── index.html                Home
├── playbook.html             How a round runs
├── roles.html                Jordan / Ryan / Parm / Leo
├── competitor.html           Scan set + gaps
├── templates.html            Approach briefs + templates
├── results.html              Round history
└── assets/
    └── style.css             Shared stylesheet
```

---

## Why static HTML (not Google Sites / Notion / Confluence)

- **Version controlled.** Round recaps and framework changes live in git history.
- **Fast iteration.** Edit a file, commit, done. No WYSIWYG lag, no plugin fights.
- **Embeds work.** The Google Sheet iframe renders cleanly with full permissions.
- **No vendor friction.** Pages is free, and the site is portable to any static host if we ever move.

---

## Owner

Jordan Kennard — Native Instruments paid media. For access issues or framework questions, ping Jordan directly.
