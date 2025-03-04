# Setting A Preferred Namespace

By default, we have the `default` namespace and if any resource is running in a different namespace, it won't show up.

Example:

```bash
kubectl get pods # in default namespace

# no outout (presuming we didn't run any pods in default namespace)
```

But if we have a different namespace (for example `linkding`), then, normally we have to do the following to get the pods.

```bash
kubectl get pods --namespace=linkding

# Some outputs are here (presuming we have some pods in this namespace)
```

And after a while, it will be irritating. So, we can edit the config and set another namespace.

```bash
kubectl config set-context --current --namespace=linkding
```

---

- [Setting the namespace preference](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/#setting-the-namespace-preference)
