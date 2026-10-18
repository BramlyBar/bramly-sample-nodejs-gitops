# GitOps Deployment Repository: bramly-sample-nodejs-gitops

This repository holds the declarative k8s configurations and Helm chart for the `bramly-sample-nodejs` application, managed via **GitOps** and **ArgoCD**.

---

## Why a Separate GitOps Repository?

I chose a separate GitOps repository over maintaining manifests in the application repository for the following reasons:
1. **No Infinite CI Loops:** Bumping the image tag in `values.yaml` will not trigger another application build/test pipeline.
2. **Separation of Concerns:** Developers manage app code; platform/deployment configs (replicas, limits) are managed here.
3. **Easy Rollbacks:** Every commit is a deployment state, so rolling back production is as simple as running `git revert`.

---

## How to Deploy via ArgoCD

To register this application in your Kubernetes cluster, apply the ArgoCD manifest:

```bash
kubectl apply -f argocd/application.yaml
```