GitHub Pages deployment — what I changed and what you need to do
=============================================================

What I did
----------

- Added a GitHub Actions workflow to build the site using your repository's Jekyll setup and deploy the generated static site to GitHub Pages.
  - Workflow path: `.github/workflows/pages.yml`
  - The workflow builds the site with Bundler (so custom plugins in `_plugins` are supported) and uses the GitHub Pages deployment actions to publish.
- Fixed a YAML indentation problem in `_config.yml` that prevented Jekyll from building locally.

What you need to do to publish
-----------------------------

1. Commit and push the current changes to your `main` branch if they are not already pushed. From the repo root (in zsh):

```bash
git add -A
git commit -m "ci(pages): add Pages workflow and fix config"
git push origin main
```

2. After pushing, GitHub Actions will run the workflow `Build and deploy Jekyll site to GitHub Pages`.

3. Open your repository in GitHub → Settings → Pages and confirm the site is published. With the `actions/deploy-pages` action used, the Pages deployment is done via the Pages API — GitHub usually auto-enables Pages when a deployment is created, but confirm the URL and make sure your domain/CNAME settings are correct if you use a custom domain.

4. Monitor the Actions run (Actions tab) and the Pages deployment status on the Pages settings page for any build errors.

If you want, I can push the changes for you and watch the first deployment — do you want me to push the commits now? (I may need your permission / CI credentials if the environment blocks pushes.)

---
If you'd like, I can also add a short GitHub Actions status badge to the README or set up a CNAME file for a custom domain.
