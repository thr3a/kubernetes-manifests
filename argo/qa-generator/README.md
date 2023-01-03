# 作成方法

```sh
k create ns qa-generator

k create secret generic my-secret --from-env-file=.env

argocd app create qa-generator --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace qa-generator \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/qa-generator

argocd app set qa-generator --sync-policy automated --auto-prune --allow-empty
```

# 詳しく

https://github.com/thr3a/qa-generator/blob/master/.github/workflows/build.yml
