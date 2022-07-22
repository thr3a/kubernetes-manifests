```
kubectl apply -k ./ -n argocd
``` 


[ArgoCDのコンソールにALB経由でアクセスする定義をkustomizeでさっと作る - Qiita](https://qiita.com/Ichi0124/items/bc37ad6f4aad9c3b9360)


openssl req -nodes -newkey rsa:2048 -keyout server.key -out server.csr -subj "/C=JP/ST=Hokkaido/L=Sapporo/O=Example INC./OU=IT Department/CN=*.turai.work"
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt

kubectl create -n istio-system secret generic oreore-turaiwork-credential \
  --from-file=key=server.key \
  --from-file=cert=server.crt
secret/oreore-turaiwork-credential created


kubectl -n argocd patch svc argocd-server -p '{[{"name":"http","nodePort":30599,"port":80,"protocol":"TCP","targetPort":8080},{"name":"grpc","nodePort":32477,"port":443,"protocol":"TCP","targetPort":8080}]}'


{"ports":[{"name":"http","nodePort":30599,"port":80,"protocol":"TCP","targetPort":8080},{"name":"https","nodePort":32477,"port":443,"protocol":"TCP","targetPort":8080}]}
