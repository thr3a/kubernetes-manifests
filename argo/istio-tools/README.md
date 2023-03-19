# 作成方法

```sh
argocd app create istio-tools --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace istio-system \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/istio-tools
argocd app set istio-system --sync-policy automated
```
