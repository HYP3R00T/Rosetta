---
tags:
  - github-action
  - mkdocs
  - poetry
  - python
date: 2024-11-26
---

# GitHub Action for Mkdocs

Create a new `.yml` file in `.github/workflows` in the root directory. Goto GitHub Pages ensure that the source for build and deployment is "Deploy from a branch". Then change the branch and set it as "gh-pages" after triggering the github action.  

In the snippet we are using python-poetry to manage the project. 

```yaml
name: MkDocs Publish

on:
  workflow_dispatch:
  push:
    branches:
      - main # Change this to your main branch name

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: "3.12"

      - name: Install Poetry
        run: |
          curl -sSL https://install.python-poetry.org | python3 -

      - name: Install dependencies
        run: |
          poetry install --no-root

      - name: Build and deploy
        run: |
          poetry run mkdocs build --verbose
          poetry run mkdocs gh-deploy --verbose --force
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```
