# copilot-docs-demo

This repository hosts a simple **CS Wiki** website built with **MkDocs Material**.

## Local development

```bash
pip install -r requirements.txt
mkdocs serve
```

## Build

```bash
mkdocs build
```

## Deployment

A GitHub Actions workflow at `.github/workflows/deploy.yml` automatically builds and deploys the site to **GitHub Pages** from the `gh-pages` branch on pushes to `main`.
Pull requests against `main` also get a preview deployment link posted in the PR.
