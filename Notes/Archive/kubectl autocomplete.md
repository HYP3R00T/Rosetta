# `kubectl` Autocomplete

- For `zsh`, add the following to `.zshrc`

    ```bash
    source <(kubectl completion zsh)
    ```

- For `pwsh`, use the following

    ```shell
    kubectl completion powershell >> $PROFILE
    ```

    - However, it's not as useful as we have for `zsh` or `bash`.

---

- [Enable shell autocompletion](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#enable-shell-autocompletion)
