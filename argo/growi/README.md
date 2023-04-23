# 作成方法

```sh
k create ns growi
k label namespace growi istio-injection=enabled

k create secret generic my-secret -n growi --from-env-file=.env

argocd app create growi --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace growi \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/growi

argocd app set growi --sync-policy automated --auto-prune --allow-empty


kubectl create secret generic my-secret -n growi --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
```
