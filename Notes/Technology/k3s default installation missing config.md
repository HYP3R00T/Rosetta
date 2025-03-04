# k3s Default Installation Missing Config

If the `k3s` is installed using the default curl command, then it's running as a server without much access. The default access is 600 to `/etc/rancher/k3s/k3s.config`. You need access to this to run `kubectl` commands. 

The best way to deal with this is to create a config (for now in the `etc` dir). First switch to sudo.

```shell
sudo su -
vim /etc/rancher/k3s/config.yaml

# Add the following to the yaml file
write-kubeconfig-mode: "0644"
```

Then stop and restart the service to enforce this new config. 

```shell
sudo systemctl stop k3s
sudo systemctl start k3s
```

---

- [docs.k3s.io/installation/configuration#configuration-file](https://docs.k3s.io/installation/configuration#configuration-file)
