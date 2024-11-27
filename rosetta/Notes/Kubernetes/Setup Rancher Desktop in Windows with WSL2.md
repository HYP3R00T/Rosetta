---
tags: 
date: 2024-11-26
---

# Setup Rancher Desktop in Windows with WSL2

- Ensure that wsl2 is enable and install some distro.
- Download the app and install it. Make sure competitive apps such as Docker Desktop is not running (I had to uninstall it completely).

```shell - wsl2
❯ kubectl version
Client Version: v1.31.3
Kustomize Version: v5.4.2
Unable to connect to the server: tls: failed to verify certificate: x509: certificate is valid for desktop-d4ctseb, gateway.rancher-desktop.internal, host.docker.internal, host.rancher-desktop.internal, kubernetes, kubernetes.default, kubernetes.default.svc, kubernetes.default.svc.cluster.local, localhost, not kubernetes.docker.internal
```

---

### References:

- https://docs.rancherdesktop.io/
