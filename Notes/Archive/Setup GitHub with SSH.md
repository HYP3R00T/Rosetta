# Setup GitHub with SSH

- Check if you already have SSH key.

    ```shell
    ls ~/.ssh/id_*
    ```

- Generate new SSH key (if needed)

    ```shell
    ssh-keygen -t ed25519 -C "your-email@example.com"
    ```

- Add the SSH key to the SSH agent (you can trust this agent).
    - Start the agent

        ```shell
        eval "$(ssh-agent -s)"
        ```

    - Add your key

        ```shell
        ssh-add ~/.ssh/id_ed25519
        ```

- Add the public key to GitHub

```shell
cat ~/.ssh/id_ed25519.pub
```

---

- [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
