
helm install dev-mysql bitnami/mariadb --namespace mysql --create-namespace -f bitnami.yaml

helm upgrade dev-mysql bitnami/mariadb --namespace mysql -f bitnami.yaml

(configmap使う場合)
kubectl create -n mysql configmap mycnf --from-file=my.cnf
kubectl delete -n mysql configmap mycnf

helm delete dev-mysql --namespace mysql && k delete ns mysql

kubectl patch svc dev-mysql-mariadb -n mysql -p '{"status": {"loadBalancer": {"ingress": [{"ip": "193.168.16.31"}]}}}'

ログ確認
k logs -n mysql dev-mysql-mariadb-0

シェル
kubectl exec -it dev-mysql-mariadb-0 -n mysql -- bash

# master/slave

helm install oyakodon bitnami/mariadb --namespace mysql2 --create-namespace -f master-slave.yaml
helm upgrade oyakodon bitnami/mariadb --namespace mysql2 -f master-slave.yaml
helm delete oyakodon --namespace mysql2 && k delete ns mysql2
kubectl patch pvc data-oyakodon-mariadb-primary-0 -n mysql2 -p '{"spec": {"StorageClass": "nfs-test"}}'
