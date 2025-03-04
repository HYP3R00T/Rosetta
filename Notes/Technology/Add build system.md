# Add build system

If there is a plan to deploy a package to pypi.org, configuring a build system is required. In the official guide, there are 4 different build backends that can be used. 

- `Hatchling` (Best for speed, automation, and future-proofing)
- `PDM` (If you want Poetry-like dependency + build management)
- `Flit` (For small, simple Python packages)
- `setuptools` (Only if you need legacy compatibility)

It's recommended to use `Hatchling`.

Add the following to the `pyproject.toml`.

```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"
```

As it's evident, `uv` doesn't have any build backend released, yet. 

---

- [Declaring the build backend](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/#declaring-the-build-backend)
- [Python Packaging User Guide](https://packaging.python.org/en/latest/)
- [Source Code - Hatchling](https://github.com/pypa/hatch/tree/master/backend)
