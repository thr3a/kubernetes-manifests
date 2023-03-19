# 作成方法

```sh
k create ns auto-namer-sensei

k create secret generic my-secret -n auto-namer-sensei --from-env-file=.env

argocd app create auto-namer-sensei --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace auto-namer-sensei \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/auto-namer-sensei

argocd app set auto-namer-sensei --sync-policy automated --auto-prune --allow-empty
```

# 詳しく

https://github.com/thr3a/auto-namer-sensei/blob/master/.github/workflows/build.yml
