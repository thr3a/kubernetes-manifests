# 作成方法

```sh
k create ns line-chatbot-api
k label namespace line-chatbot-api istio-injection=enabled

k create secret generic my-secret -n line-chatbot-api --from-env-file=.env

argocd app create line-chatbot-api --repo https://github.com/thr3a/kubernetes-manifests.git \
  --dest-namespace line-chatbot-api \
  --dest-server https://kubernetes.default.svc \
  --path ./argo/line-chatbot-api

argocd app set line-chatbot-api --sync-policy automated --auto-prune --allow-empty

kubectl create secret generic my-secret -n line-chatbot-api --from-env-file=.env --dry-run=client -o yaml | kubectl apply -f -
```

https://github.com/thr3a/chatgpt-linebot
