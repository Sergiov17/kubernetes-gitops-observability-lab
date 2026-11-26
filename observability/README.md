# Optional observability stack

The lab's alert example uses the Prometheus Operator CRD provided by kube-prometheus-stack. Install that chart before applying `alerts/app-alerts.yaml`.

A local setup can add Grafana for dashboards and Loki with Promtail for log aggregation. Keep chart values in version control, pin chart versions deliberately, and avoid exposing dashboards outside the local cluster.

Example alert rule:

```sh
kubectl apply -f observability/alerts/app-alerts.yaml
kubectl get prometheusrules -n monitoring
```

The alert queries kube-state-metrics and warns when fewer than two demo replicas remain available for five minutes. It is a teaching example; tune it for the service's actual SLO and alert routing.
