```
kubectl create namespace httpbin
kubectl label namespace httpbin istio-injection=enabled
wget https://raw.githubusercontent.com/istio/istio/release-1.17/samples/httpbin/httpbin.yaml
wget https://raw.githubusercontent.com/istio/istio/release-1.17/samples/httpbin/httpbin-gateway.yaml
kubectl apply -f httpbin.yaml -n httpbin
kubectl apply -f httpbin-gateway.yaml -n httpbin
```

確認

```
❯ kubectl get pods,deployments,svc,virtualservice -n httpbin
NAME                           READY   STATUS    RESTARTS   AGE
pod/httpbin-847f64cc8d-dgb89   2/2     Running   0          8m47s

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/httpbin   1/1     1            1           38m

NAME              TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
service/httpbin   ClusterIP   10.96.125.29   <none>        8000/TCP   38m

NAME                                         GATEWAYS                     HOSTS                     AGE
virtualservice.networking.istio.io/httpbin   ["httpbin-gateway","mesh"]   ["httpbin1.turai.work"]   51s
```

ポートフォワードで確認 http://localhost:3000/

```
k port-forward svc/httpbin 3000:8000 -n httpbin
```

```sh
export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
```

確認

```
curl -H 'Host: httpbin1.turai.work' "http://$INGRESS_HOST:$INGRESS_PORT/headers"
```
