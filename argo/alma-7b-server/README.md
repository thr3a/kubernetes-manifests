# 作成方法

```sh
k create ns alma-7b-server
k label namespace alma-7b-server istio-injection=enabled

k create secret generic my-secret -n alma-7b-server --from-env-file=.env

argocd app create alma-7b-server --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace alma-7b-server \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/alma-7b-server

argocd app set alma-7b-server --sync-policy automated --auto-prune --allow-empty
```

kubectl create secret generic my-secret -n alma-7b-server --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
