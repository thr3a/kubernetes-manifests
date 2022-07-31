# インストール

```
kubectl create -n istio-system secret generic oreore-turaiwork-credential \
  --from-file=key=server.key \
  --from-file=cert=server.crt
kubectl create ns argocd
kubectl apply -k ./ -n argocd
```

# 参考リンク

- https://thr3a.hatenablog.com/entry/20220724/1658610521
