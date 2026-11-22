---
name: update-fin-site
description: How to update the Fiduciary Integrity Network (FIN) website in this repo. Use whenever the user wants to add, replace, rename or remove a document, change wording on the page, or check that the live site is correct. The account holder is NOT technical, so follow the communication rules in this file.
---

# Updating the FIN website

## Who you are working with

The account holder has **no software or technical background**. She publishes briefings for the Fiduciary Integrity Network and will normally ask for updates in plain English, usually by attaching new PDFs. Treat her as an expert in the *content* and a complete beginner in *how the site works*.

### Communication rules (follow every time)

1. **No jargon.** Do not say commit, branch, push, merge, PR, repo, deploy, fast-forward, HTML, or 403 without a plain-English replacement. Say "publish to the live site", "save your changes", "the page", "the link".
2. **Never ask her to use a terminal, edit code, or use git.** You do all of that. If something truly needs her to click in GitHub or Claude settings, give numbered steps: exactly where to click, the exact words on the button, and what she should see afterwards.
3. **One question at a time**, with a recommended answer. Prefer yes/no or "A or B" questions.
4. **Say what you are about to do before doing it**, in one sentence, then say what happened in one or two sentences.
5. **Never guess what is new versus a replacement.** Read the first page of each attached PDF and compare with the files already on the site. Tell her your reading in plain terms ("This looks like an updated Paper 3, so I'll replace the old one; this one looks brand new, so I'll add it") and ask her to confirm before changing anything. If her description does not match what you see, say so gently and ask.
6. **Always confirm before publishing to the live site.** Publishing is public. Ask: "Ready for me to publish this to the live site? Anyone with the link will be able to see it." Only publish after a clear yes.
7. **Finish by telling her exactly what to look at**: the live link, what she should see, and what to tell you if it looks wrong. If you cannot check the live site yourself (this environment's network may block it), say so clearly rather than implying it is verified.
8. **Be honest about failures.** If something did not work, say so in plain words, say what it means for her, and say what you will do next. Do not pretend it worked.
9. Keep replies short. No long summaries or tables unless she asks.

## How the site works (for you, not to explain unless asked)

- Static site on GitHub Pages: `index.html` plus a logo PNG plus PDFs, all at the repo root. No build step.
- Live address: `https://fin-2026.github.io/briefings/`
- The live site updates **only when changes reach the `main` branch**, then takes about 1–2 minutes. Work done on any other branch is invisible on the live site.
- Do not rebuild this on Wix, WordPress, Squarespace or Elementor. Do not redesign the page unless she asks. Do not move files into subfolders.
- Existing documents are linked from outside (emails, other sites). **When replacing a document, overwrite the file under its existing filename** so old links keep working.
- Filenames follow the pattern `Name_FIN.pdf`. Links in `index.html` are URL-encoded (spaces become `%20`).
- The PDFs and page are **public**. Never add anything she has not clearly approved for publication, and never suggest a private repo makes the site private.

## Current contents

Press release, suite cover sheet, Paper 1, Paper 2, Paper 3, Paper 3 companion (Developments and Sources), and the E1 settlement finance briefing note (Nov 2026). Papers are labelled "Paper N"; other items get a short label such as "Press release", "Cover sheet", "Paper 3 companion", "Briefing note". The suite is described as "three papers", so extra notes are **not** numbered as papers.

## Recipes

### Replace an existing document
1. Confirm which document it replaces (see rule 5).
2. Copy the new PDF over the old file, keeping the old filename.
3. If the title changed, update the title text for that row in `index.html`.
4. Preview, confirm with her, publish.

### Add a new document
1. Decide a clear filename ending `_FIN.pdf` and a short label and title.
2. Put the PDF at the repo root.
3. Add one `<li>` block in `index.html` copying an existing one, with the URL-encoded `href`.
4. Add a row to the file table in `README.md`.
5. Preview, confirm with her, publish.

### Remove a document
Ask whether anyone might still have the old link (removing breaks it). If yes, suggest replacing it rather than deleting. Only delete after a clear yes.

### Change wording or order on the page
Edit `index.html` only. Show her the new wording in plain text and get a yes before publishing.

## Checking your work before publishing

- Confirm every `href` in `index.html` matches a real file in the folder (run a quick script, do not eyeball it).
- Render the page to an image with Playwright and look at it. Check it on a phone width too (about 390px).
- Open the first page of any PDF you added to make sure it is the right document, not a draft or an older version.

## Publishing (you do this; she should not need to)

Changes must reach `main`. If a normal push is refused with a permissions error (403), the Claude GitHub App has probably lost access to the repo. Tell her in plain words and give these steps:
1. Open https://github.com/apps/claude/installations/select_target
2. Choose the FIN-2026 organisation and make sure the `briefings` repository is allowed.
Or reconnect GitHub at https://claude.ai/customize/connectors?auth_start=github&auth_start_force=1
If she cannot do this herself, she should ask her nephew, who set up the account.

Fallback if publishing from here is impossible: give her step-by-step instructions for GitHub's web upload ("Add file" → "Upload files" → "Commit changes") and tell her which files to drop in.

## After publishing

Wait about two minutes. Then either check the live links yourself (if the network allows) or give her the live link and the checklist: page loads, the new row appears, each new link opens the right PDF. If the page has not changed after five minutes, check that GitHub Pages is on (repo Settings → Pages → Deploy from a branch → `main` → root) and look at the Actions tab for a failed build.

## Escalation

If anything is unclear, risky or goes wrong twice, stop and tell her plainly, and suggest she contact her nephew. Do not experiment on the live site.
