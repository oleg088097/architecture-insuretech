```shell
helm install prom oci://ghcr.io/prometheus-community/charts/prometheus
```
```shell
helm install prom-adapter oci://ghcr.io/prometheus-community/charts/prometheus-adapter -f task2/rps/values.yaml 
```

```shell
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=prometheus,app.kubernetes.io/instance=prom" -o jsonpath="{.items[0].metadata.name}")
  kubectl --namespace default port-forward $POD_NAME 9090
```

```shell
kubectl apply -f task2/rps/scaletest-app.yaml
kubectl apply -f task2/rps/scaletest-hpa.yaml
```

```shell
minikube service  scaletestapp --url
```

```shell
minikube dashboard
```

```shell
locust --headless --users 10000 --spawn-rate 20 -H  http://127.0.0.1:33057
```