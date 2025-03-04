# Add ruff for linting and formatting

Formatting and linting helps to maintain the consistency of any project. This helps to implement standardization to projects where there are potentially more than one contributor.

Add the following to `pyproject.toml`

```toml
[tool.ruff]
line-length = 120

[tool.ruff.format]
docstring-code-format = true

[tool.ruff.lint]
select = [
    "E", # pycodestyle errors
    "W", # pycodestyle warnings
    "F", # pyflakes
    "I", # isort
    "C", # flake8-comprehensions
    "B", # flake8-bugbear
]
ignore = [
    "E501", # line too long
    "C901", # too complex
]

[tool.ruff.lint.isort]
order-by-type = true
relative-imports-order = "closest-to-furthest"
extra-standard-library = ["typing"]
section-order = [
    "future",
    "standard-library",
    "third-party",
    "first-party",
    "local-folder",
]
```

---

- [Docs - Ruff](https://docs.astral.sh/ruff/)
