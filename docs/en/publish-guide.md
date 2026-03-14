# How to Publish This Repo as a Doc Site (GitHub Pages)

Right now the repo is just Markdown; on GitHub you see source. To turn it into **a doc-style site** (sidebar, main content, search), use **GitHub Pages**: GitHub will host a site for you at `https://YOUR_USERNAME.github.io/YOUR_REPO/`.

---

## Idea in two sentences

1. Use **MkDocs** to turn these `.md` files into a static site with navigation (HTML).
2. Use **GitHub Actions** so that on every `git push` it builds and pushes to the **gh-pages** branch; then in repo **Settings** enable **GitHub Pages** and select the gh-pages branch. The site goes live.

You **don’t need MkDocs locally**; just `git push`. The build runs on GitHub.

---

## Step 1: What’s already in the repo

The repo already has:

- **`docs/`**: All doc source Markdown lives here; MkDocs builds the site from this.
- **`mkdocs.yml`**: Tells MkDocs to use `docs_dir: docs`, which pages to use, site title, and Material theme.
- **`.github/workflows/docs.yml`**: On push to `main` (or `master`), runs `mkdocs build` on GitHub and pushes the result to **gh-pages**.

So you don’t need to create these; just enable Pages and push once.

---

## Step 2: Enable Pages on GitHub

1. Open your repo → **Settings**.
2. In the left sidebar find **Pages** (under “Code and automation”).
3. Under **Build and deployment**:
   - **Source**: **Deploy from a branch**.
   - **Branch**: **gh-pages**, folder **/(root)**.
4. Click **Save**.

The first time, the `gh-pages` branch may not exist yet. That’s fine—after you do Step 3 and push once, the Action will create it; wait a minute or two and refresh; once the branch is selected, the site will deploy.

---

## Step 3: Trigger a build (publish the site)

1. Make sure `mkdocs.yml` and `.github/workflows/docs.yml` are in the repo (pull latest or add them).
2. Commit and push, e.g.:
   ```bash
   git add .
   git commit -m "enable docs build"
   git push origin main
   ```
   (If your default branch is `master`, use that instead.)
3. Open the **Actions** tab on the repo; you should see a workflow running (e.g. “Deploy docs”). Wait until it turns green (about 1–2 minutes).
4. Go back to **Settings → Pages**, confirm Branch is **gh-pages**, then click **Visit site**, or open:  
   **`https://YOUR_USERNAME.github.io/YOUR_REPO/`**

That’s your doc site: sidebar from `nav` in `mkdocs.yml`, main area with the current note.

---

## Updating the docs later

- **Only change `.md`:** After editing, `git add`, `commit`, `push` to `main` (or `master`); Actions will rebuild and update gh-pages; the site updates in a few minutes.
- **Change navigation:** Edit **`mkdocs.yml`** `nav`, add or reorder pages, then push.

---

## FAQ

**Q: Visit site gives 404?**  
Wait 2–3 minutes; confirm the last workflow in Actions succeeded and Settings → Pages uses the **gh-pages** branch.

**Q: Site loads but layout is wrong or links 404?**  
Often the **base URL** is wrong. In `mkdocs.yml`, `site_url` (or Material’s `repo_url`) should match your real URL, e.g. `https://YOUR_USERNAME.github.io/YOUR_REPO/`. Repo name must match GitHub; trailing slash is optional.

**Q: Want to use something other than MkDocs (e.g. VuePress / Docusaurus)?**  
Yes. Same idea: in Actions, build with VuePress/Docusaurus, push the built output to gh-pages, and Pages still serves from gh-pages. This guide only covers MkDocs because it’s minimal and fits plain Markdown well.

**Q: Can I use my own domain?**  
Yes. In **Settings → Pages** set **Custom domain** and add the CNAME record as GitHub instructs.

---

## Summary

| Step | What to do |
|------|------------|
| 1 | Repo has `mkdocs.yml` and `.github/workflows/docs.yml` |
| 2 | Settings → Pages → Source: “Deploy from a branch”, Branch: **gh-pages** |
| 3 | `git push` to default branch, wait for Actions, open `https://USERNAME.github.io/REPO/` |

After that, any change to `.md` or `mkdocs.yml` plus push will update the doc site automatically.
