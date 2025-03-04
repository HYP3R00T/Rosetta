# k3s In Ubuntu Server

- `ufw disable` - Not Recommended
- `curl -sfL https://get.k3s.io | sh -`
- `sudo k3s kubectl get node`
- `sudo chmod 644 /etc/rancher/k3s/k3s.yaml` - makes the file readable by all users
- `sudo chown $(whoami):$(whoami) /etc/rancher/k3s/k3s.yaml` - allows a specific group to access the file

## k3s With Docker

- By default `k3s` doesn't come with `docker` support. 
- `curl -sfL https://get.k3s.io | sh -s - --docker` - Install k3s with docker as container runtime.
    - `sudo /usr/local/bin/k3s-uninstall.sh` To uninstalled any previously installed `k3s`

## Copy the `k3s.yaml` to home Directory

```shell
sudo cp /etc/rancher/k3s/k3s.yaml ~
sudo chown hyperoot:hyperoot ~/k3s.yaml
```

And don't forget to change the ownership to current user instead of `root`. We will further copy this Kubernetes config to our workstation using `scp`.

```shell
cd
scp hyperoot@192.168.1.3:/home/hyperoot/k3s.yaml .
```

This will allow us to control the cluster from our workstation instead of SSHing into the server again and again.

---

- [docs.k3s.io](https://docs.k3s.io/)
