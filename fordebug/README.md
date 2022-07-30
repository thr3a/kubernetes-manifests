# インストール

```
k apply -f deployment.yaml -n default
```

# デバッガー起動

```
kubectl exec -it deploy/debugger -n default -- sh
```
