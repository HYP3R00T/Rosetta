# `.kube/config` Is Insecure

When I executed the following, I got some warnings.

```shell
helm repo list
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /home/hyperoot/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /home/hyperoot/.kube/config
```

To resolve this, we will modify the `config` file and change the permission.

```shell
chmod 600 ~/.kube/config
```

---

- [GitHub Issue Solution](https://github.com/helm/helm/issues/9115#issuecomment-742604901)
