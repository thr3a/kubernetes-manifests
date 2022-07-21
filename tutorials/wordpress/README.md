# やり方

```
❯ kubectl apply -k ./
secret/mysql-pass-kdgbgfchf7 created
service/wordpress created
service/wordpress-mysql created
persistentvolumeclaim/mysql-pv-claim created
persistentvolumeclaim/wp-pv-claim created
deployment.apps/wordpress created
deployment.apps/wordpress-mysql created
```

```
❯ kubectl get secrets
NAME                    TYPE     DATA   AGE
mysql-pass-kdgbgfchf7   Opaque   1      34s
```


# pv

```
k apply -f pv.yaml


```
❯ k get sc                                                           
NAME                 PROVISIONER               RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
standard (default)   kubernetes.io/host-path   Delete          Immediate           false                  11s
```


```
❯ k get pvc                                                          
NAME             STATUS    VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS    AGE
mysql-pv-claim   Pending                                                                        local-storage   29m
pvc01            Bound     pv01                                       1Gi        RWO            standard        16m
pvc02            Bound     pvc-0c0219ba-87d3-470e-85bd-04c536b9bde9   1Gi        RWO            standard        21s
```
