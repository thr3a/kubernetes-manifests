kubectl exec -it deploy/debugger -- sh


kubernetes-rails-example-load-balancer.myrails.svc.cluster.local


mysql.mysql.svc.cluster.local


Serviceへは service.namespace.svc.cluster.local で名前解決ができ、アクセスできます。 こちらは基礎的なことなので知っている方も多いかと思います。もし知らなかったという方は、デバッグに非常に役立ちますのでぜひ理解しておくといいです。 (公式ドキュメント: ServiceとPodに対するDNS - Kubernetes)


mynginx.default.svc.cluster.local
