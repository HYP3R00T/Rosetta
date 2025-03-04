# WSL2 Permission Denied for Docker Commands

When I run a docker command like `docker push`, it throws the following error.

```shell
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.47/images/ghcr.io/hyp3r00t/server/push?tag=latest": dial unix /var/run/docker.sock: connect: permission denied
```

The quick solution is to use `sudo`. But it's not the best way. So, we can simply modify the `docker` group.

Create `docker` group

```shell
sudo groupadd docker
```

Add current user to the group

```shell
 sudo usermod -aG docker $USER
```

Restart the WSL2 distro.

---
