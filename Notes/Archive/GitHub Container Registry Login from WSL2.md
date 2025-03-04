# GitHub Container Registry Login from WSL2

- First we need is an access token to authenticate to GitHub Packages. Make sure it has `write:packages` scope selected.
- Set the token as an environment variable.

```shell
# It's temporary. Once the session is terminated, we will need to do it again. Make sure you have the token saved somewhere else to be referred later.
export GH_TOKEN=<Actual token here> 
```

- Login using the following command. 

```shell
echo $GH_TOKEN | docker login ghcr.io -u USERNAME --password-stdin
```

If everything is fine, you will get `Login Succeeded` message. 

But if you try to go for `docker push`, it will throw an error.

```shell
unauthorized: unauthenticated: User cannot be authenticated with the token provided.
```

If you view the content of `~/.docker/config.json`, you will find the following.

```json
{
        "auths": {
                "ghcr.io": {}
        },
        "credsStore": "desktop.exe"
}
```

As you can see, the `auths` are empty for `ghcr.io`. 

To fix it, remove the `credsStore` key-value pair. And login again. This time, it will have the `auth` for `ghcr.io`
