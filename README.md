# pyscaffold-gh-pages-deploy

Build and deploy documentation for Pyscaffold-based projects on GitHub Pages.

[![Project generated with PyScaffold](https://img.shields.io/badge/-PyScaffold-005CA0?logo=pyscaffold)](https://pyscaffold.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

[GitHub Action](https://docs.github.com/en/actions/) to automatically build the documentation of a Python project based on 
[Pyscaffold](https://pyscaffold.org/) and publish it on [GitHub Pages](https://docs.github.com/en/pages).

Individual steps used by this GitHub Action:
1. Install dependencies (tox)
2. Configure git
3. Create branch gh-pages in the repository if it doesn't exist. *Warning: if the branch exists already, it will be overwritten*
4. Checkout the main branch
5. Build documentation using `tox -e docs`
6. Push the documentation to the gh-pages branch


## Installation

Create a YAML file with the name `gh-pages-deploy.yml` in the folder `.github/workflows` of your repo with following content:

```
name: gh-pages-deploy
on: 
  push:
    branches:
      - main
jobs:
  gh-pages-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
      - name: Setup Python
        uses: actions/setup-python@v4
        with:
          python-version: 3.8
      - name: Deploy docs to GitHub Pages
        uses: Kopfstein/pyscaffold-gh-pages-deploy@v0.0.1
```

**Note:** Replace `Kopfstein/pyscaffold-gh-pages-deploy@v0.0.1` to use the latest version.


## Ackowledgements

This project was developed using information and/or code snippets from following projects. Thanks to the authors of these
projects for creating open source software!
- [simple-github-pages-deploy-action](https://github.com/rdarida/simple-github-pages-deploy-action)
- [action-sphinx-docs-to-gh-pages](https://github.com/uibcdf/action-sphinx-docs-to-gh-pages/)
