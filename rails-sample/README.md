```
argocd app create rails-sample --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace rails-sample \
  --path 'rails-sample'
```
