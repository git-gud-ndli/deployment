# Manifests de déploiement dans Kubernetes.

Nécessite un Redis, Postgres et Prometheus, installable via helm:

```
helm install stable/postgresql --name ndli-db
helm install stable/prometheus --name ndli-prometheus -f prom.yml
helm install stable/redis --name ndli-redis
```

puis:

```
kubectl apply -f frontend.yml # sandhose/ndli-front
kubectl apply -f backend.yml  # sandhose/ndli-backend
kubectl apply -f metrics.yml  # sandhose/ndli-metrics
```

---

```
$ kubectl get pods
NAME                                                  READY   STATUS      RESTARTS   AGE
api-6bcc5786b4-d77hf                                  0/1     Init:0/1    0          8s
frontend-7d59f9c464-42kdg                             1/1     Running     0          115m
metrics-85974468c9-sx4g2                              1/1     Running     0          15m
ndli-db-postgresql-0                                  1/1     Running     0          113m
ndli-prometheus-alertmanager-7555655b49-5tncm         2/2     Running     0          24m
ndli-prometheus-pushgateway-6b4dc9bf8f-65l8k          1/1     Running     0          24m
ndli-prometheus-server-79ccd9577c-ksrbk               2/2     Running     0          24m
ndli-redis-master-0                                   1/1     Running     0          27m
```
