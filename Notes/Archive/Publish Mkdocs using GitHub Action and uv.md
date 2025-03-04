# Publish `Mkdocs` Using `GitHub Action` and `uv`

It's way easier to setup and deploy `mkdocs` sites using `uv` in `GitHub Action` thanks to the official action from `astral-sh`.

```yaml
name: MkDocs Publish

on:
  push:
    branches:
      - main # Change this to your main branch name
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Install uv
        uses: astral-sh/setup-uv@v5

      - name: "Set up Python"
        uses: actions/setup-python@v5
        with:
          python-version-file: ".python-version"

      - name: Install the project
        run: uv sync --all-extras --dev

      - name: Build and deploy
        run: |
          uv run mkdocs build --verbose
          uv run mkdocs gh-deploy --verbose --force
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```

---

- [astral-sh/setup-uv](https://github.com/astral-sh/setup-uv)
- [Using uv in GitHub Actions](https://docs.astral.sh/uv/guides/integration/github/)
