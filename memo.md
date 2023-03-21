kube-prometheus-stack


kubectl create namespace monitoring


$ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
$ helm repo update


helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring

```
❯ kubectl get deployment -n monitoring
NAME                                       READY   UP-TO-DATE   AVAILABLE   AGE
kube-prometheus-stack-grafana              1/1     1            1           61s
kube-prometheus-stack-kube-state-metrics   1/1     1            1           61s
kube-prometheus-stack-operator             1/1     1            1           61s
```

```
❯ kubectl get svc -n monitoring
NAME                                             TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                      AGE
alertmanager-operated                            ClusterIP   None            <none>        9093/TCP,9094/TCP,9094/UDP   67s
kube-prometheus-stack-alertmanager               ClusterIP   10.96.101.95    <none>        9093/TCP                     77s
kube-prometheus-stack-grafana                    ClusterIP   10.96.67.32     <none>        80/TCP                       77s
kube-prometheus-stack-kube-state-metrics         ClusterIP   10.96.1.62      <none>        8080/TCP                     77s
kube-prometheus-stack-operator                   ClusterIP   10.96.236.225   <none>        443/TCP                      77s
kube-prometheus-stack-prometheus                 ClusterIP   10.96.252.238   <none>        9090/TCP                     77s
kube-prometheus-stack-prometheus-node-exporter   ClusterIP   10.96.107.171   <none>        9100/TCP                     77s
prometheus-operated                              ClusterIP   None            <none>        9090/TCP                     66s
```
