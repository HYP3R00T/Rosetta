# Connect to k3s Server from Windows

Ensure that `kubectl` in installed in the Windows machine.

```shell
winget install --id=Kubernetes.kubectl  -e
```

Make sure you can connect to the remote server using `ssh`.

Create a `.kube` folder in the home directory in Windows, if it doesn't exist.

In Windows, open PowerShell and use the following command to leverage `scp` to move the file from the server to the Windows machine.

```shell
scp root@192.168.1.3:/etc/rancher/k3s/k3s.yaml C:\Users\hyperoot\.kube\config
```

Now open the `config` file in any text editor and change the server IP address accordingly.

```yaml
# from
server: https://127.0.0.1:6443
# to
server: https://192.168.1.3:6443
```

Make sure `k3s` is running in the server. And now you can connect to cluster from your Windows machine.

---
