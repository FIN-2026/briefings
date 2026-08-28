# Fiduciary Integrity Network — document site

A very simple static website for sharing these briefings. No Wix, no Elementor, no paid host. The whole site is one HTML page plus a logo and PDFs.

**If you are an AI:** follow [Instructions for an AI assistant](#instructions-for-an-ai-assistant) exactly. Do not rebuild this as a WordPress, Wix, Squarespace, or Elementor site.

---

## What is in this folder

| File | Role |
| --- | --- |
| `index.html` | Landing page. Leave this at the repo root. |
| `FINANCIAL INTEGRITY NETWORK plus.png` | Logo used at the top of the page |
| `Settlement and Sovereign Debt Exposure Briefings Release.pdf` | Press release |
| `Settlement and Sovereign Exposure Suite Cover Sheet_FIN.pdf` | Cover sheet |
| `Paper 1 - The Regulatory Landscape_FIN.pdf` | Paper 1 |
| `Paper 2 - Corporate Holdings_FIN.pdf` | Paper 2 |
| `Paper 3 - Israeli Sovereign Debt_FIN.pdf` | Paper 3 |
| `README.md` | These instructions |

Do not rename the PDFs or the logo unless you also update the matching links in `index.html`.

---

## Copy this prompt into Claude, Cursor, or ChatGPT

Paste the block below, then attach or point the AI at this downloaded folder.

```
I downloaded this folder. It is a finished static website.

Please host it on MY GitHub account with GitHub Pages.

Rules:
- Do not rebuild it on Wix, Squarespace, WordPress, or Elementor.
- Do not rewrite the design unless I ask.
- Keep index.html, the PNG logo, and all PDFs at the repository root.
- Create a public GitHub repository named briefings (or ask me if that name is taken).
- Upload every file in this folder except .git and .cursor.
- Enable GitHub Pages: Settings → Pages → Deploy from a branch → main → / (root).
- When it is live, give me the URL. It will look like:
  https://MY-GITHUB-USERNAME.github.io/briefings/

Important privacy fact: a GitHub Pages website URL is public. Anyone with the link can open the PDFs. Making the GitHub repository private does NOT hide the live website.

If I say I want it completely private, do not enable GitHub Pages. Instead keep the repository private and tell me how to invite collaborators.
```

---

## Instructions for an AI assistant

Goal: publish this existing static site on the user's GitHub Pages. The site is already built.

### Do

1. Confirm `gh` is logged into the user's own GitHub account (`gh auth status`).
2. Create a new repository named `briefings` on that account. Use `--public` if they want a live website on a free plan.
3. Put these files at the repo root (not in a subfolder):
   - `index.html`
   - `FINANCIAL INTEGRITY NETWORK plus.png`
   - all `*.pdf` files in this folder
   - `README.md`
4. Commit and push to `main`.
5. Enable Pages from `main` and `/` (root):

   ```bash
   gh api -X POST repos/USERNAME/briefings/pages --input - <<'EOF'
   {
     "source": {
       "branch": "main",
       "path": "/"
     }
   }
   EOF
   ```

6. Wait until Pages status is `built`, then return:

   `https://USERNAME.github.io/briefings/`

7. Click-test the homepage and each PDF link.

### Do not

- Recreate this in Wix, Squarespace, WordPress, Elementor, or any site builder.
- Put the files in `/docs` unless the user asks.
- Change document filenames without updating `index.html`.
- Claim a private repository makes the Pages URL private. It does not.
- Enable Pages if the user asked for a completely private share. In that case, keep the repo private and invite people as collaborators instead.

### Privacy (read this before enabling Pages)

| What | Who can see it |
| --- | --- |
| Private GitHub repo, Pages **off** | Only people invited to the repo |
| Private GitHub repo, Pages **on** | Repo is hidden; **the website URL is still public** |
| Public GitHub repo, Pages on | Repo and website are both public |

GitHub Pages on a private repo also requires GitHub Pro (or Team/Enterprise). A free account can only publish Pages from a public repo.

### Add a new document later

1. Add the new PDF next to `index.html`.
2. Add one more `<li>` in `index.html` with a URL-encoded `href` (spaces become `%20`).
3. Commit and push to `main`. The live site updates in a minute or two.

---

## Host it yourself (no AI)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click **+** → **New repository**.
3. Name it `briefings`.
4. If you want a live website on a free account, make it **Public**.
5. Click **Create repository**.
6. Click **Add file** → **Upload files**.
7. Drag in everything from this folder except a `.git` folder if you see one.
8. Click **Commit changes**.
9. Go to **Settings** → **Pages**.
10. Under **Source**, choose **Deploy from a branch**.
11. Branch: **main**. Folder: **/ (root)**. Click **Save**.
12. Wait one or two minutes. Your site will be:

    `https://YOUR-USERNAME.github.io/briefings/`

To add more PDFs later, repeat step 6–8 and add a link in `index.html`.

---

## Completely private (no public website)

Do **not** turn on GitHub Pages.

1. Keep the repository **Private**.
2. On GitHub: **Settings** → **Collaborators** → add your people by email or username.
3. They sign in to GitHub and open the PDFs in the repo.

That is the only way this set of files stays fully private on GitHub.
