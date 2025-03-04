# Steps to publish package to pypi.org

Presuming we have created a separate branch to do development of the source code. Once done, we can do a pull request to merge the changes to the `main` branch.

Once merge is approved, the GitHub Action will be triggered (if conditions are met). Unless we push a tag.

Do the following locally, after merging.

```shell
git checkout main
git pull
git tag v1.2.3
git push --tags
```

This will trigger the pipeline once again but this time it go to the point where it actually publish the package.

[[Automated build and release workflow with GitHub Actions|Automated build and release workflow with GitHub Actions]]

---
