# Merge Kubernetes Configs in Windows Machine

Ensure that `kubectl` is installed in Windows machine ([[../Technology/kubectl in Windows machine]]).

Next job is to fetch all configs from different clusters. 

We can use `scp` to get that file in our workstation.

```shell
# Example
scp hyperoot@192.168.1.3:/home/hyperoot/k3s.yaml $HOME/.kube/k3s.yaml
```

*Note: if you are using k3s, then the config will be placed at `/etc/rancher/k3s/k3s.yaml`. Make sure to move it to home directory and change ownership to current user instead of `sudo chown hyperoot:hyperoot k3s.yaml`*

Once we have all the configs ready, we need to set `KUBECONFIG` to the PowerShell environment.

```shell
$env:KUBECONFIG = "$HOME/.kube/k3s.yaml;$HOME/.kube/another_config.yaml"
```

Now we can merge all these configs into one.

```shell
kubectl config view --merge --flatten > merged-config
```

A new file named `merged-config` will be created. Of course, we need to rename it to `config` as `kubectl` look for this by default. If you have an old `config` file, then take a backup before renaming the merged file.

Verify all the clusters using the following

```shell
kubectl config get-clusters
```

To switch clusters, refer to [[../Technology/Change context in kubectl]]

---

- [How to Merge Multiple kubeconfig Files into One](https://able8.medium.com/how-to-merge-multiple-kubeconfig-files-into-one-36fc987c2e2f)
