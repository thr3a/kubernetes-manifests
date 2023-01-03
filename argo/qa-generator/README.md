# 作成方法

```sh
k create ns qa-generator2

k create secret generic my-secret --from-env-file=.env

argocd app create qa-generator2 --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace qa-generator2 \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/qa-generator

argocd app set qa-generator2 --sync-policy automated --auto-prune --allow-empty
```

# 詳しく

https://github.com/thr3a/qa-generator/blob/master/.github/workflows/build.yml
