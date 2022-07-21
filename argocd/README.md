```
kubectl apply -k ./ -n argocd
``` 


[ArgoCDのコンソールにALB経由でアクセスする定義をkustomizeでさっと作る - Qiita](https://qiita.com/Ichi0124/items/bc37ad6f4aad9c3b9360)


openssl req -new -newkey rsa:2048 -days 3650 -nodes -x509 \
  -keyout server.key -out server.crt \
  -subj "/CN=*.turai.work/"

kubectl create -n istio-system secret generic oreore-turaiwork-credential \
  --from-file=key=server.key \
  --from-file=cert=server.crt
secret/oreore-turaiwork-credential created
