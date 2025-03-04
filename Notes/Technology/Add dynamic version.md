# Add dynamic version

#issue

> [!error]
> The `uv build` is adding more than tag to the `whl` files. Need to find a workaround.

By default, when a new project is created using `uv init`, a static version is added.

```toml
[project]
# version = "0.1.0" # Don't use it
dynamic = ["version"]

[build-system]
requires = ["hatchling", "hatch-vcs"]
build-backend = "hatchling.build"

[tool.hatch.version]
source = "vcs"
```

Git tags can be used to determine the version of a package.

```shell
git checkout main
git pull
git tag v1.2.3
git push --tags
```

- [[Steps to publish package to pypi.org]]
- [[Automated build and release workflow with GitHub Actions]]

---

- [Source Code - Hatch VCS](https://github.com/ofek/hatch-vcs)
