# Container Registry

Not all registries are **publicly available like Docker Hub**. Registries can be categorized based on their accessibility and purpose.

|Registry|Publicly Accessible?|Notes|
|---|---|---|
|Docker Hub|✅ Yes|Widely used, hosts official and community images.|
|Kubernetes Registry|✅ Yes|Hosts Kubernetes-related public images.|
|Google Container Registry|🟡 Partially|Some public images; most are private to GCP projects.|
|Amazon ECR Public|✅ Yes|Public ECR provides public images.|
|Amazon ECR|❌ No|Private by default for AWS accounts.|
|Azure Container Registry|❌ No|Private by default for Azure customers.|
|GitHub Container Registry|✅ Yes (for public repos)|Authentication required for private repositories.|
|GitLab Container Registry|❌ No (unless public)|Images tied to GitLab projects; private by default.|
|Quay.io|✅ Yes (for public repos)|Public and private repositories supported.|
|Harbor|🟡 Depends|Can be public or private, based on deployment.|
|JFrog Artifactory|❌ No (typically private)|Enterprise-grade; public access depends on setup.|
|IBM Cloud Registry|❌ No|Typically private to an IBM Cloud organization.|

### **Publicly Accessible Registries**

- [Docker Hub](https://hub.docker.com/)
- [Kubernetes Registry](https://kubernetes.io/docs/reference/image-registry/) - No direct browsing interface, used programmatically
    - `registry.k8s.io`
- [Quay.io](https://quay.io/)
- [GitHub Container Registry (GHCR) - Documentation](https://docs.github.com/en/packages/working-with-a-github-container-registry)
    - `ghcr.io`
- [Google Artifact Registry - Documentation](https://cloud.google.com/artifact-registry/docs)
    - `gcr.io`
- [Amazon Elastic Container Registry Public (ECR Public)](https://gallery.ecr.aws/)
- [Harbor](https://goharbor.io/)

### **Private Or Restricted Registries**

- [Azure Container Registry (ACR)](https://azure.microsoft.com/en-us/products/container-registry/)
- [GitLab Container Registry - Documentation](https://docs.gitlab.com/ee/user/packages/container_registry/)
    - `registry.gitlab.com`
- [Amazon Elastic Container Registry (ECR)](https://aws.amazon.com/ecr/)
- [IBM Cloud Container Registry](https://www.ibm.com/cloud/container-registry)
