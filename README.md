# copilot-docs-demo

This repository hosts a simple **CS Wiki** website built with **MkDocs Material**.

## Local development

```bash
pip install mkdocs-material
mkdocs serve
```

## Build

```bash
mkdocs build
```

## Deployment

A GitHub Actions workflow at `.github/workflows/deploy.yml` automatically builds and deploys the site to **GitHub Pages** on pushes to `main`.
