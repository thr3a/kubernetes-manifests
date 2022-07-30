
helm install dev-mysql bitnami/mariadb --namespace mysql --create-namespace -f bitnami.yaml

helm upgrade dev-mysql bitnami/mariadb --namespace mysql -f bitnami.yaml


helm delete dev-mysql --namespace mysql && k delete ns mysql


helm install oyakodon bitnami/mariadb --namespace mysql2 --create-namespace -f master-slave.yaml
helm upgrade oyakodon bitnami/mariadb --namespace mysql2 -f master-slave.yaml
helm delete oyakodon --namespace mysql2 && k delete ns mysql2


kubectl patch pvc data-oyakodon-mariadb-primary-0 -n mysql2 -p '{"spec": {"StorageClass": "nfs-test"}}'
