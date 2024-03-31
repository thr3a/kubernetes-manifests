# インストール

```
openssl req -nodes -newkey rsa:2048 -keyout server.key -out server.csr -subj "/C=JP/ST=Hokkaido/L=Sapporo/O=Example INC./CN=*.turai.work"
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt
```

```
kubectl create -n istio-system secret generic oreore-turaiwork-credential \
  --from-file=key=server.key \
  --from-file=cert=server.crt
kubectl create ns argocd
kubectl apply -k ./ -n argocd
```

# 参考リンク

- https://blog.turai.work/entry/20220724/1658610521

# 初期パスワード取得

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

ログイン

```
argocd login argocd.turai.work --insecure
```

パスワード変更

```
argocd account update-password --account admin
```
