# Azure CLI Login

In WSL2, it won't open any browser. So, instead of login in using `az login`, use the following.

```shell
az login --use-device-code
```

To check if you already have logged in, try the following.

```shell
az account show
```

If you are not logged in, you will see an error message.

---

- [github.com/Azure/azure-cli/issues/14656#issuecomment-668987828](https://github.com/Azure/azure-cli/issues/14656#issuecomment-668987828)
- [Sign in with a browser](https://learn.microsoft.com/en-us/cli/azure/authenticate-azure-cli-interactively#sign-in-with-a-browser)
