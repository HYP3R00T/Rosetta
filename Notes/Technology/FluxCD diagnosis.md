# FluxCD Diagnosis

To check if Flux is installed properly in your k3s cluster, follow these steps:

### 1. Check FluxCD Components

Run:

```sh
kubectl get pods -n flux-system
```

Expected output:

```
NAME                                       READY   STATUS    RESTARTS   AGE
helm-controller-xxxx-yyyy                  1/1     Running   0          10m
kustomize-controller-xxxx-yyyy             1/1     Running   0          10m
notification-controller-xxxx-yyyy          1/1     Running   0          10m
source-controller-xxxx-yyyy                1/1     Running   0          10m
```

If any pod is **not in Running state**, check its logs:

```sh
kubectl logs -n flux-system <pod-name>
```

### 2. Check Flux Git Repository Sync

Run:

```sh
kubectl get gitrepositories -n flux-system
```

Expected output (example):

```
NAME           URL                                           READY   STATUS
flux-system   ssh://git@github.com/your/repo.git           True    Fetched revision: main@<commit-hash>
```

- If `READY=True`, Flux successfully pulled your repository.
- If `READY=False`, check `STATUS` for errors (e.g., authentication issues).

For detailed sync status:

```sh
kubectl describe gitrepository flux-system -n flux-system
```

### 3. Check Flux Kustomizations

List all `Kustomization` resources:

```sh
kubectl get kustomization -n flux-system
```

Expected output:

```
NAME           READY   STATUS
flux-system    True    Applied revision: main@<commit-hash>
metallb        True    Applied revision: main@<commit-hash>
```

- If `READY=True`, Flux successfully applied the manifests.
- If `READY=False`, describe the Kustomization to check for errors:

    ```sh
    kubectl describe kustomization flux-system -n flux-system
    ```

### 4. Check Flux Logs for Errors

If something is wrong, you can check logs from the controllers:

```sh
kubectl logs -n flux-system deployment/kustomize-controller
kubectl logs -n flux-system deployment/source-controller
kubectl logs -n flux-system deployment/helm-controller
```

Look for errors related to syncing, authentication, or repository issues.

### Next Steps

- If everything is running fine, Flux is installed properly.
- If any component is failing, share the error messages, and I'll help debug! 🚀

---
