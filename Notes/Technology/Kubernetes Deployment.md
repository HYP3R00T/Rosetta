# Kubernetes Deployment

To create a sample deployment, run the following command.

```shell
kubectl create deployment <name-of-the-deployment> --image=nginx --namespace=<name-of-the-namespace> --dry-run=client -o yaml > deployment.yml
```

- We use `--dry-run-client` to ensure that we actually deploy the deployment.
- We can use any image. I picked something similar, just to generate the template. Of course, we will change to the image we need in the `.yml` file.
    - Checkout [[../Containerization/Container Registry|Container Registry]].

It's recommended to have separate namespace for separate deployment (basically for each app). Of course, the purpose of namespace is to have a logical grouping of resources.

---

- [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
