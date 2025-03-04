# Add ruff pre-commit

It will run the formatting and linting before committing the changes to git.

```yaml
- repo: https://github.com/astral-sh/ruff-pre-commit
  # Ruff version.
  rev: v0.9.7
  hooks:
  # Run the linter.
  - id: ruff
    args: [ --fix ]
  # Run the formatter.
  - id: ruff-format
```

---

- [Source Code - ruff-pre-commit](https://github.com/astral-sh/ruff-pre-commit)
- [pre-commit](https://docs.astral.sh/ruff/integrations/#pre-commit)
