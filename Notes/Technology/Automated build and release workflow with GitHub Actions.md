# Automated build and release workflow with GitHub Actions

```yaml
name: Build and Release

on:
  push:
    branches:
      - main
    tags:
      - 'v*'  # Trigger on tag pushes following the vX.Y.Z pattern

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      # Check out the repository with full history for VCS version detection
      - name: Checkout repository
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      # Set up uv
       - name: Install uv
        uses: astral-sh/setup-uv@v5

      #   
        - name: "Set up Python"
        uses: actions/setup-python@v5
        with:
          python-version-file: ".python-version"
        
      # Install uv and any other dependencies
      - name: Install the project
        run: uv sync --all-extras --dev

      # Optionally run tests (if you have them)
      #- name: Run tests
      #  run: pytest

      # Build the distribution using uv (ensure uv is configured to derive the version as needed)
      - name: Build package
        run: uv build

      # Publish to PyPI when a tag is pushed; ensure you have set PYPI_USERNAME and PYPI_PASSWORD in secrets
      - name: Publish package to PyPI
        if: startsWith(github.ref, 'refs/tags/')
        env:
          PYPI_TOKEN: ${{ secrets.PYPI_TOKEN }}
        run: uv publish --username __token__ --password $POETRY_PYPI_TOKEN

```

---

- [Publishing your package](https://docs.astral.sh/uv/guides/package/#publishing-your-package)
