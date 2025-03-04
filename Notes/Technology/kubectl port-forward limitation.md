# `kubectl port-forward` Limitation

```shell
kubectl port-forward pod/mypod 8080:80
```

`kubectl port-forward` creates a connection from the local machine \[8080] and to a pod \[80] in the cluster. It binds to `172.0.0.1` (localhost) by default. Which means, we can't access it in another machine even in the subnet. 

We have 2 options to resolve this.

1. Modify the address of `port-forward` command.

    ```shell
    kubectl port-forward --address 0.0.0.0 pod/mypod 8080:80
    ```

2. Create a service instead.

    ```yaml
    apiVersion: v1
    kind: Service
    metadata:
        name: mealie
        namespace: mealie
    spec:
        selector:
            app: mealie
        type: NodePort
        ports:
            - protocol: TCP
              port: 80 # Service port
              targetPort: 9000 # Pod's containerPort
              nodePort: 32000 # Optional: Specify a NodePort (otherwise, Kubernetes will assign one dynamically)
    ```

Use `kubectl get svc` to figure out which port is assigned to which service.

---

- [port-forward](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward)
- [Service](https://kubernetes.io/docs/concepts/services-networking/service/)
- [Use Port Forwarding to Access Applications in a Cluster](https://kubernetes.io/docs/tasks/access-application-cluster/port-forward-access-application-cluster/)
