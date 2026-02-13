# Lab 19: Creating a Real-Time Dashboard

## Objectives
- Understand the principles of real-time data monitoring.
- Set up a basic real-time dashboard using open-source tools.
- Explore real-time log and alert visualization.
- Configure dashboards to update at specific intervals.

## Prerequisites
- Basic understanding of web technologies and data visualization.
- Familiarity with Linux command-line operations.
- Access to a virtual machine or server with an internet connection.

## Tools Required
- Ubuntu or any Linux-based system
- Docker
- Grafana
- Prometheus

---

## Task 1: Set Up Prometheus

### Install Docker
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
Run Prometheus
docker pull prom/prometheus
docker run -d --name=prometheus -p 9090:9090 prom/prometheus
Open browser:

http://localhost:9090
Task 2: Set Up Grafana
Run Grafana
docker pull grafana/grafana
docker run -d --name=grafana -p 3000:3000 grafana/grafana
Open:

http://localhost:3000
Login:

username: admin
password: admin
Add Prometheus Data Source
Go to Configuration → Data Sources

Add Prometheus

URL:

http://prometheus:9090
Click Save & Test

Task 3: Create Real-Time Dashboard
Create Dashboard
Click Create → Dashboard

Add New Panel

Add Query:

rate(http_requests_total[1m])
Configure Refresh Interval
Set refresh to:

5s
Observe real-time updates in dashboard panels.

Conclusion
In this lab, you created a real-time monitoring dashboard using open-source tools. You configured Prometheus as a data source and visualized data through Grafana dashboards with real-time refresh intervals. These skills are essential for monitoring infrastructure, detecting anomalies, and improving system observability.
