デフォルト ClusterIP

curl 10.109.30.239


/ # nslookup mynginx.test.svc.cluster.local
Server:         10.96.0.10
Address:        10.96.0.10#53

Name:   mynginx.test.svc.cluster.local
Address: 10.109.30.239


# podのIP
/ # nslookup mynginx.test.svc.cluster.local
Server:         10.96.0.10
Address:        10.96.0.10#53

Name:   mynginx.test.svc.cluster.local
Address: 10.100.3.219


```
❯ k get pod -n test -o wide
NAME                     READY   STATUS    RESTARTS   AGE     IP             NODE       NOMINATED NODE   READINESS GATES
nginx-5d98ddb845-l4sbv   1/1     Running   0          3m24s   10.100.3.219   ubuntu01   <none>           <none>
```



mysql> SHOW GLOBAL VARIABLES like 'bind_address';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| bind_address  | *     |
+---------------+-------+
1 row in set (0.01 sec)
