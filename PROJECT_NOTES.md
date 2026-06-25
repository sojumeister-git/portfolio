# Portfolio Site Project Notes

## Overview

- Site: `박상화 | 올라운더 디자이너`
- Type: static portfolio site (HTML/CSS/JavaScript in a single page)
- Repository: `https://github.com/sojumeister-git/portfolio.git`
- Published site: `https://www.designwelsh.com/resume/test2.html`
- Deployment target: GitHub Pages

## Repository Layout

```text
.
├─ index.html       # Main portfolio page: markup, styles, and scripts
├─ background.html  # Background/visual resource page
├─ img/             # Images and icon assets referenced by index.html
├─ favicon.ico
├─ .gitignore
└─ PROJECT_NOTES.md
```

## Editing Rules

- Use `index.html` as the current source of truth. Older `test.html` and `test2.html` files are intentionally removed.
- Keep image and icon references relative to the repository root, for example: `img/profile.jpg`.
- Do not use `../img/...` paths. They break after publishing the repository root through GitHub Pages.
- The profile section is positioned between the intro and career sections. When adding/removing full-page sections, update the bullet navigation and its JavaScript index values together.
- Preserve the existing Korean UTF-8 encoding when editing files.
- Do not commit personal editor settings. `.vscode/`, `Thumbs.db`, and `.DS_Store` are ignored.

## Local Preview

This is a static site. For a quick check, open `index.html` in a browser.

For a server-based check, run this from the repository root:

```powershell
python -m http.server 8000
```

Then open `http://localhost:8000/`.

## Multi-PC Git Workflow

Before editing on any PC:

```powershell
git status
git pull --ff-only origin main
```

After checking the page locally:

```powershell
git add index.html img PROJECT_NOTES.md
git commit -m "Describe the change"
git push origin main
```

Guidelines:

- Do not begin new work with uncommitted changes from another task unless they are deliberate.
- Use `git pull --ff-only` to avoid creating an accidental merge commit. If it fails, inspect `git status` and resolve the local work first.
- Keep commits small and describe the visible change in Korean or English consistently.
- Before a risky HTML/CSS edit, use `git diff` to confirm only intended changes are staged.

## Deployment Check

1. Push the intended commit to `origin/main`.
2. Wait for the GitHub Pages deployment to finish.
3. Reload the public page with cache bypass (`Ctrl+F5`) and verify images, navigation, desktop layout, and mobile layout.
4. If an asset fails to load, first verify its filename casing and its `img/...` path in `index.html`.