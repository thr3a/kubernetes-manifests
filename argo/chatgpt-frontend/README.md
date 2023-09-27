# 作成方法

```sh
k create ns chatgpt-frontend
k label namespace chatgpt-frontend istio-injection=enabled

k create secret generic my-secret -n chatgpt-frontend --from-env-file=.env

argocd login argocd.turai.work --insecure

argocd app create chatgpt-frontend --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace chatgpt-frontend \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/chatgpt-frontend

argocd app set chatgpt-frontend --sync-policy automated --auto-prune --allow-empty
```

kubectl create secret generic my-secret -n chatgpt-frontend --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
