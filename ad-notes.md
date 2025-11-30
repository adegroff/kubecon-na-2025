# https://github.com/adegroff/kubecon-na-2025/blob/main/.devcontainer/WEB_BASED_CODESPACE.md

```plaintext
export GITHUB_TOKEN="<token>"
export GITHUB_CLIENT_ID="Ov23liQTgqlrdvEn08mb"
export GITHUB_CLIENT_SECRET="<secret>"
export GITHUB_OWNER="adegroff"
export GITHUB_REPO="kubecon-na-2025"
```

# Retrieve the Admin Password

```plaintext
export ARGOCD_ADMIN_PASSWORD=`kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 --decode`
echo "ArgoCD Admin Password: ${ARGOCD_ADMIN_PASSWORD}"
```

# update argocd-cm or workflow-controller ConfigMap to use argocd-repo-server.argocd.svc.cluster.local:8081

kubectl rollout restart deployment -n argocd argocd-server argocd-repo-server
