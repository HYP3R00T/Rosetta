# Poetry Shell Changed to Env Activate

For some mysterious reason, `poetry` decided to drop the `shell` subcommand. 

## Before

It was simple to use. To switch to the virtual environment created by `poetry` just use the following.

```shell
poetry shell
```

## Now

Now, we need to leverage `env` subcommand.

```shell
eval $(poetry env activate)
```

There is another problem here. For now, VSCode doesn't recognize any poetry virtual environment.

---

- [Activating the environment](https://python-poetry.org/docs/managing-environments/#activating-the-environment)
- [Request for more info on the removal of poetry shell command](https://github.com/orgs/python-poetry/discussions/10000)
