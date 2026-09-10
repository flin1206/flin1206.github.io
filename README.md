# Yu-Fan Lin — Personal Website

Single-page portfolio (GPU/parallel systems research), built as a static `index.html`
with no build step or dependencies.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deployment (CI/CD)

`.github/workflows/deploy.yml` deploys `index.html` to GitHub Pages automatically:

- **Trigger:** every push to `main` (or manually via the Actions tab → "Run workflow").
- **Build step:** validates that every in-page anchor link (`#research`, `#projects`, ...)
  resolves to a real section id, so a broken nav link fails CI instead of shipping.
- **Deploy step:** publishes the checked-out files via GitHub's official Pages actions
  (`upload-pages-artifact` + `deploy-pages`) — no external hosting account needed.

### One-time setup after the first push

1. Repo → **Settings → Pages → Source** → select **GitHub Actions**.
2. Push to `main`; the workflow runs and prints the live URL in the Actions run summary
   (`https://<username>.github.io/<repo>/`).

Every subsequent push to `main` redeploys automatically.
