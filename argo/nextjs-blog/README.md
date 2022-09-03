
```
k create ns nextjs-blog
k create secret generic my-secret --from-env-file=.env
argocd app create nextjs-blog --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace nextjs-blog \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/nextjs-blog
```
