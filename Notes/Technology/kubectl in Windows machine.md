# `kubectl` In Windows Machine

We can install `kubectl` in windows machine using winget or curl.

```shell
curl.exe -LO "https://dl.k8s.io/release/v1.32.0/bin/windows/amd64/kubectl.exe"

# OR

winget install -e --id Kubernetes.kubectl
```

Create a `.kube` directory in the `%USERPROFILE%` folder. This is where we will keep track of all the configs. 

- To deal with multiple configs from different clusters refer to [[Merge Kubernetes configs in Windows machine|Merge Kubernetes configs in Windows machine.md]].
- To switch between different contexts (to use different clusters), refer to [[Change context in kubectl|Change context in kubectl.md]].

---

- [Install and Set Up kubectl on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)
