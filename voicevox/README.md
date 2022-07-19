# command

```
k apply -f namespace.yaml
k apply -f main.yaml -n voicevox
k apply -f gateway.yaml -n voicevox
```

# test

```
kubectl get pods,deployments,svc,virtualservice -n voicevox
NAME                            READY   STATUS    RESTARTS   AGE
pod/voicevox-58c7557db8-5jt84   2/2     Running   0          5m1s

NAME                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/voicevox   1/1     1            1           25m

NAME               TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/voicevox   ClusterIP   10.110.157.67   <none>        8000/TCP   25m

NAME                                          GATEWAYS                      HOSTS                     AGE
virtualservice.networking.istio.io/voicevox   ["voicevox-gateway","mesh"]   ["voicevox.turai.work"]   25m
```

```
curl --resolve voicevox.turai.work:80:10.0.0.210 http://voicevox.turai.work/version
"latest"
```
