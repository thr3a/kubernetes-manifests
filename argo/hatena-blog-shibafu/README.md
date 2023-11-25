# 作成方法

```sh
k create ns hatena-blog-shibafu
k label namespace hatena-blog-shibafu istio-injection=enabled

k create secret generic my-secret -n hatena-blog-shibafu --from-env-file=.env

argocd app create hatena-blog-shibafu --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace hatena-blog-shibafu \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/hatena-blog-shibafu

argocd app set hatena-blog-shibafu --sync-policy automated --auto-prune --allow-empty
```

kubectl create secret generic my-secret -n hatena-blog-shibafu --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
