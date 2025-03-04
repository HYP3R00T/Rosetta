# FluxCD Setup

You need to be in a system that is connected to some Kubernetes cluster. For instance, I am on my WSL2 while the cluster is installed in my old laptop. But I can interact with the Kubernetes cluster from WSL2 as `kubectl` is configured properly.

## Installing Flux

Install flux in your machine. You don't need to SSH into the server. You can install it in your machine as long as you can access the cluster through `kubectl`.

```shell
curl -s https://fluxcd.io/install.sh | sudo bash
```

To check if the `flux` can reach the cluster, run the following.

```shell
flux check --pre
```

## Setting up GitHub

For the GitOps to work, we need a GitHub token. Generate one and store then to environment variables.

```shell
export GITHUB_TOKEN=<your-token>
export GITHUB_USER=<your-username>
```

Of course, there is a need of a GitHub repo. You can use GitHub CLI to create one. Or simply create a GitHub repo in the browser and clone that to the workstation.

## Install Flux onto Cluster

Leverage the `bootstrap` command of Flux to do the installation.

```shell
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=<repo-name> \
  --branch=main \
  --path=./clusters/<cluster-name> \
  --personal
```

---

- [Get Started with Flux](https://fluxcd.io/flux/get-started/)
