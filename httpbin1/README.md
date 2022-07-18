# Base

https://github.com/istio/istio/blob/release-1.14/samples/httpbin/httpbin.yaml

# Command

```
kubectl create namespace httpbin
kubectl label namespace httpbin istio-injection=enabled
kubectl apply -f app.yaml -n httpbin
kubectl apply -f gateway.yaml -n httpbin
```

# 確認

```
❯ kubectl get pods,deployments,svc,virtualservice -n httpbin
NAME                           READY   STATUS    RESTARTS   AGE
pod/httpbin-847f64cc8d-btk28   2/2     Running   0          2m59s
pod/httpbin-847f64cc8d-v7hn8   2/2     Running   0          2m59s

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/httpbin   2/2     2            2           3m9s

NAME              TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/httpbin   ClusterIP   10.105.210.23   <none>        8000/TCP   3m9s

NAME                                         GATEWAYS                     HOSTS                     AGE
virtualservice.networking.istio.io/httpbin   ["httpbin-gateway","mesh"]   ["httpbin1.turai.work"]   2m55s
```

```
curl --resolve httpbin1.turai.work:80:10.0.0.210 http://httpbin1.turai.work
```
