# 作成方法

```sh
k create ns gpt-article-generator
k label namespace gpt-article-generator istio-injection=enabled

k create secret generic my-secret -n gpt-article-generator --from-env-file=.env

argocd app create gpt-article-generator --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace gpt-article-generator \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/gpt-article-generator

argocd app set gpt-article-generator --sync-policy automated --auto-prune --allow-empty
```

kubectl create secret generic my-secret -n gpt-article-generator --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
