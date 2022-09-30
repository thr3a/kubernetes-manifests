デプロイメモ

argocd app create twitter-profile --repo https://github.com/thr3a/kubernetes-manifests.git --dest-server https://kubernetes.default.svc --dest-namespace twitter-profile --path ./twitter-profile
