# 作成方法

```sh
k create ns httpbin-argo
k label namespace httpbin-argo istio-injection=enabled

argocd app create httpbin --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace httpbin-argo \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/httpbin

argocd app set httpbin --sync-policy automated --auto-prune --allow-empty
```
