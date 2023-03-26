# 作成方法

```sh
k create ns debate-simulator
k label namespace debate-simulator istio-injection=enabled

k create secret generic my-secret -n debate-simulator --from-env-file=.env

argocd app create debate-simulator --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace debate-simulator \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/debate-simulator

argocd app set debate-simulator --sync-policy automated --auto-prune --allow-empty


kubectl create secret generic my-secret -n debate-simulator --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
```
