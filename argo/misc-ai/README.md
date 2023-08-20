# 作成方法

```sh
k create ns misc-ai
k label namespace misc-ai istio-injection=enabled

k create secret generic my-secret -n misc-ai --from-env-file=.env

argocd app create misc-ai --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace misc-ai \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/misc-ai

argocd app set misc-ai --sync-policy automated --auto-prune --allow-empty
```

kubectl create secret generic my-secret -n misc-ai --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
