# Publish Image to GitHub Container Registry

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

Then you can simply go for `docker push`.

```shell
docker push ghcr.io/hyp3r00t/server:latest
```

---

- [Working with the Container registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)
- [YouTube - Pushing Docker Images to GitHub Container Registry](https://www.youtube.com/watch?v=eupw4r_6H3g)
