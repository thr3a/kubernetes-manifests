```sh
k create ns twitter-profile
k create secret generic my-secret --from-env-file=.env

argocd app create twitter-profile --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace twitter-profile \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/twitter-profile

argocd app set twitter-profile --sync-policy automated --auto-prune --allow-empty
```
