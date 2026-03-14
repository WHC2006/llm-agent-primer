# How to Publish This Doc Site (GitHub Pages)

[:cn: 中文版](../发布文档指南.md)

---

1. **Enable Pages:** Repo → Settings → Pages → Source: **Deploy from a branch** → Branch: **gh-pages** → Save.
2. **Trigger build:** Push to `main` (or `master`). The workflow runs `mkdocs build` and pushes the result to `gh-pages`.
3. **Open site:** `https://YOUR_USERNAME.github.io/YOUR_REPO/`

Doc source lives in `docs/`; `mkdocs.yml` and `.github/workflows/docs.yml` are in the repo root.
