helm repo add grafana https://grafana.github.io/helm-charts


helm repo update


helm install --values loki-values.yaml loki grafana/loki -n loki-stack
