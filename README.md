# Kubernetes Monitoring & Alerting Stack

Full observability stack deployed on Kubernetes using Prometheus, Grafana, and AlertManager.

## Architecture

Spring Boot App → Prometheus (scrapes metrics) → Grafana (dashboards)
                                                → AlertManager (alerts)

## Components

| Component | Purpose | Port |
|-----------|---------|------|
| Spring Boot App | Application being monitored | 30080 |
| Prometheus | Metrics collection and storage | 30090 |
| Grafana | Metrics visualization and dashboards | 30030 |
| AlertManager | Alert routing and Slack notifications | 30093 |

## Project Structure

- `app/` — Spring Boot application Kubernetes manifests
- `prometheus/` — Prometheus config, alert rules, deployment
- `grafana/` — Grafana deployment and service
- `alertmanager/` — AlertManager config and deployment

## Alert Rules

- App Down — triggers if Spring Boot app is unreachable for 1 minute
- High CPU Usage — triggers if CPU exceeds 80% for 2 minutes
- High Memory Usage — triggers if JVM memory exceeds 80% for 2 minutes
- Pod Restarting — triggers if pod restarts frequently

## How to Deploy

```bash
kubectl apply -f app/
kubectl apply -f prometheus/
kubectl apply -f grafana/
kubectl apply -f alertmanager/
```

## Tech Stack
- Kubernetes/Minikube
- Prometheus
- Grafana
- AlertManager
- Spring Boot (monitored app)
- AWS EC2 (hosting)
- Slack (alert notifications)
