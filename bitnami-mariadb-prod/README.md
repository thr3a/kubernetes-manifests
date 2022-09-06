```
helm install nfs-production-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
  --set nfs.server=192.168.16.7 \
  --set nfs.path=/data/kube/ \
  --set storageClass.name=nfs-production
```

helm install mysql-production bitnami/mariadb --namespace mysql-production --create-namespace -f bitnami.yaml
kubectl patch svc mysql-production-mariadb -n mysql-production -p '{"status": {"loadBalancer": {"ingress": [{"ip": ""}]}}}'
export MARIADB_ROOT_PASSWORD=$(kubectl get secret --namespace "mysql-production" mysql-production-mariadb -o jsonpath="{.data.mariadb-root-password}" | base64 -d)
helm upgrade mysql-production bitnami/mariadb --namespace mysql-production -f bitnami.yaml --set auth.rootPassword=$MARIADB_ROOT_PASSWORD

ログ確認
k logs -n mysql mysql-production-mariadb-0 -n mysql-production

シェル
kubectl exec -it mysql-production-mariadb-0 -n mysql-production -- bash

kubectl get secret --namespace "mysql-production" mysql-production-mariadb -o jsonpath="{.data.mariadb-root-password}" | base64 -d
