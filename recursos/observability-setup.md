# Observability Stack Setup (Grafana, Loki, Tempo, Mimir, Alloy)

## Namespaces

```bash
kubectl create namespace observability

kubectl create namespace app
```

## Add Helm Repositories

```bash
helm repo add grafana https://grafana.github.io/helm-charts

helm repo update
```

## Deploy Grafana

```bash
helm upgrade --install grafana grafana/grafana -n observability -f ./observability/values-grafana.yaml

kubectl port-forward -n observability svc/grafana 3000:80 &
```

## Deploy Loki

```bash
helm upgrade --install loki grafana/loki -n observability -f ./observability/values-loki.yaml
```

## Deploy Tempo

```bash
helm upgrade --install tempo grafana/tempo-distributed -n observability -f ./observability/values-tempo.yaml
```

## Deploy Mimir

```bash
helm upgrade --install mimir grafana/mimir-distributed -n observability -f ./observability/values-mimir.yaml

kubectl port-forward -n observability svc/mimir-nginx 9009 &
```

## Deploy Your App

```bash
minikube addons enable ingress

kubectl apply -f ./eu-kubernetes-workload-example/deployment.yaml

kubectl apply -f ./eu-kubernetes-workload-example/ingress.yaml

kubectl apply -f ./eu-kubernetes-workload-example/ingress-controller.yaml
```

## Deploy Alloy

```bash
helm upgrade --install alloy grafana/alloy -n app -f ./eu-kubernetes-workload-example/alloy/values-alloy.yaml

kubectl port-forward -n app svc/alloy 12345 &
```