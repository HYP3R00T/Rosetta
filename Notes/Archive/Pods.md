# Pods

This is the smallest deployable unit in Kubernetes. 

Sample: `nginx.yml`

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
  name: nginx-storage
spec:
  containers:
    - image: nginx
      name: nginx
```

To run this pod use the `apply` command.

```
kubectl apply -f nginx.yml
```

If we modify the `nginx.yml` file further and try to `apply` it again (when the old pod is still running with the same name), it won't work.

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
  name: nginx-storage
spec:
  containers:
    - image: nginx
      name: nginx
    - image: busybox
      name: busybox
      command: ["/bin/sh", "-c"]
      arg: ["sleep 1000"]
```

First, delete the old pod and then apply the changes.

---

- [Pod - Reference](https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/)
- [Pods](https://kubernetes.io/docs/concepts/workloads/pods/)
