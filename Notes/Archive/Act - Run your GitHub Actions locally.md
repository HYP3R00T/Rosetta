# Act - Run Your GitHub Actions Locally

> "Think globally, `act` locally"

To test some of the steps of the pipeline, we can use `act`. A simple `.yml` file would look like the following.

```yaml
name: Test MkDocs Build
on:
  push:
    branches:
      - main
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

      - name: Install dependencies
        run: |
          python -m venv venv
          source venv/bin/activate
          pip install --upgrade pip
          pip install -r requirements.txt

      - name: Configure Git
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "github-actions[bot]@users.noreply.github.com"

      - name: Build and Deploy MkDocs site
        run: |
          source venv/bin/activate
          mkdocs build
```

## How to Install it Locally?

While `act` is available for [some platforms](https://nektosact.com/installation/index.html), the easiest way is to use the `curl` command.

```bash

cd ~

curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash

```

When we install it, it will create a `bin` folder in the current working directory. So, it's recommended to change directory to home first and then run the `curl` command piped with `sudo bash`. Also, dont' forget to add the `bin` directory to the `$PATH`.

Before we use `act` to run the workflow locally, we also need Docker. As `act` will build and run everything in a docker container, it needs the docker engine. Make sure you have it installed.

But it's not enough to test a workflow. The project need to be synced to GitHub as well. You can checkout a sample repo that I have created [here](https://github.com/HYP3R00T/act_with_mkdocs). You can create something similar or fork it and then you can test the workflow using `act` in your local machine.

### Execution

Create a workflow in `.github/workflows` directory. Then you can run `act` as following.

```shell

# act -W <path-to-workflow>

act -W .github/workflows/mkdocs_test.yml

```

If everything is fine, you will see job completed message at the end. Otherwise, fix the issues and rerun the tool.

## The Problem

But still, there is one problem. While `act` is working, it's still very limited. There are no other tools or methods to test the pipeline before committing the changes to GitHub. To know more check out the [Unsupported functionality](https://nektosact.com/not_supported.html).

---

- [`act_with_mkdocs` - Sample repo](https://github.com/HYP3R00T/act_with_mkdocs)
- [Act - Documentation](https://nektosact.com/)
- [Act - GitHub](https://github.com/nektos/act)
- [Docker](https://www.docker.com/)
- [How can I run GitHub Actions workflows locally?](https://stackoverflow.com/questions/59241249/how-can-i-run-github-actions-workflows-locally)
