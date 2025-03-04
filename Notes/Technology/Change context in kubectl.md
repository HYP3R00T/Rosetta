# Change Context in `kubectl`

To change and config context in `kubectl`, first list out all the clusters.

```shell
kubectl config get-contexts
```

Then change the context using

```shell
kubectl config use-context <cluster_name>
```

To verify current context, use

```shell
kubectl config current-context
```

---

- [kubectl config](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_config/)
