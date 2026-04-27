```shell
kubectl apply -f task2/memory/scaletest-app.yaml
kubectl apply -f task2/memory/scaletest-hpa.yaml
```

```shell
minikube service  scaletestapp --url
```

```shell
locust --headless --users 10000 --spawn-rate 20 -H  http://127.0.0.1:40979
```