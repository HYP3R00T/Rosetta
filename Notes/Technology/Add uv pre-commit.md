# Add uv pre-commit

This will ensure that uv-lock file is up to date even if `pyproject.toml` file was changed via pre-commit.

```yaml
- repo: https://github.com/astral-sh/uv-pre-commit
  # uv version.
  rev: 0.6.3
  hooks:
  - id: uv-lock
```

---

- [Source Code - uv-pre-commit](https://github.com/astral-sh/uv-pre-commit)
- [Using uv in pre-commit](https://docs.astral.sh/uv/guides/integration/pre-commit/)
