“Built as part of hands-on SRE practice to simulate real-world monitoring and incident response.”

# 🚀 SRE Monitoring Stack (Prometheus + Alertmanager + Grafana)

## 📌 Overview
This project demonstrates a complete end-to-end monitoring and alerting system built using Prometheus, Alertmanager, and Grafana.

The setup monitors multiple nodes (Linux server + MacBook) and triggers alerts based on system metrics like CPU usage.

---

## 🧱 Architecture

MacBook (node_exporter)
        ↓ (via ngrok)
Linux Server (Prometheus)
        ↓
Alertmanager
        ↓
Email Notifications (Gmail SMTP)
        ↓
Grafana Dashboards

---

## ⚙️ Tech Stack
- Prometheus (Metrics collection)
- Alertmanager (Alert routing)
- Grafana (Visualization)
- Node Exporter (System metrics)
- ngrok (Expose local MacBook metrics)
- stress (CPU load testing)

---

## 🔍 Features
- Multi-node monitoring (Linux + macOS)
- Real-time CPU, Memory, Disk metrics
- Alerting for high CPU usage
- Email notifications using SMTP
- Grafana dashboards for visualization
- Remote node monitoring via ngrok tunnel

---

## 🚨 Alert Rule Example

```promql
100 - (avg by (instance) (rate(node_cpu_seconds_total{mode="idle"}[2m])) * 100) > 80
