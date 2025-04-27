# 📈 Monitoring with Prometheus & Grafana - Mind Map

---

## 🔹 Core Concepts
- **Monitoring**: Observing the state, health, and performance of systems.
- **Metrics**: Quantifiable measures to track system behavior.
- **Alerting**: Sending notifications when metrics cross thresholds.

---

## 🛠️ Key Technical Words
| Term | Definition |
|:---|:---|
| Prometheus | Open-source monitoring system and time-series database. |
| Grafana | Open-source analytics & interactive visualization platform. |
| Exporters | Tools that help gather metrics from systems/applications. |
| Time-Series Database | A database optimized for storing data indexed by time. |
| Alertmanager | Handles alerts sent by client applications like Prometheus. |

---

## 🛠️ Prometheus Core Concepts
- **Data Collection**:
  - Scrapes metrics from targets at given intervals.
  - Data is pulled via HTTP.
- **Metrics Format**:
  - `metric_name{label1="value1", label2="value2"} value timestamp`
- **PromQL** (Prometheus Query Language):
  - Powerful query language to extract meaningful insights.

- **Simple Example**:
  ```plaintext
  up{job="myapp"} == 1
  ```

- **Components**:
  - Server, Exporters, Pushgateway, Alertmanager.

---

## 🛠️ Grafana Core Concepts
- **Data Sources**:
  - Prometheus is commonly used as a data source.
- **Dashboards**:
  - Visualize time-series data.
  - Panels like graphs, tables, heatmaps, and alerts.
- **Templating**:
  - Use variables for dynamic dashboards.

- **Sample Setup**:
  - Add Prometheus as data source.
  - Create Dashboard > Add Panel > Query with PromQL.

---

## ⚙️ Basic Prometheus + Grafana Setup
1. Install Prometheus and Grafana.
2. Configure Prometheus to scrape target applications.
3. Start Prometheus and Grafana servers.
4. Connect Grafana to Prometheus as a data source.
5. Build dashboards using queries.

---

## 🎯 Best Practices
- Use consistent metric names and labeling.
- Set up efficient scraping intervals to balance granularity vs load.
- Group dashboards logically: application, infrastructure, security.
- Configure alerts properly to avoid alert fatigue.
- Document dashboard and metric usage.

---

## ❓ Common Interview Questions
- What is the role of Exporters in Prometheus?
- How does Prometheus store time-series data?
- What are key advantages of Grafana?
- How would you monitor API latency and database errors?

---

## 📋 Cheat Sheet
| Area | Quick Tip |
|:---|:---|
| Prometheus | Pulls metrics from HTTP endpoints |
| Grafana | Visualizes time-series metrics interactively |
| Alertmanager | Central place for alert processing |

---

## ⚡ Common Mistakes
- Ignoring metric cardinality (too many unique labels → huge storage needs).
- Overloading Prometheus with high-frequency scrapes.
- Hardcoding dashboard queries instead of using variables.
- Neglecting alert suppression rules causing redundant alerts.

---

## 🧠 Quick Visual Mind Map
- **Monitoring**
  - Prometheus
    - Scraping
    - PromQL
    - Exporters
    - Alertmanager
  - Grafana
    - Dashboards
    - Alerts
    - Templating
    - Data Sources

---
