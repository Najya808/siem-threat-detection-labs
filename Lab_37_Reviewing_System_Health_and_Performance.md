#  Lab 38: Reviewing System Health & Performance

##  Objectives
- Examine CPU and memory usage of the SIEM host.
- Review log ingestion rates and indexing performance.
- Identify system bottlenecks and errors through log analysis.
- Propose basic remediation steps to improve system stability.

---

##  Prerequisites
- Basic understanding of CPU, memory, and performance metrics.
- Familiarity with Linux system logs.
- Access to a Linux system acting as a SIEM host.
- Installed open-source monitoring tool (Prometheus used in this lab).

---

##  Tools Used
- **Prometheus** – system monitoring
- **Linux CLI utilities** – `top`, `htop`, `grep`
- **System logs** – `/var/log/syslog`

---

##  Task 1: Monitor CPU and Memory Usage

### 1.1 Install Prometheus
```bash
sudo apt update
sudo apt install prometheus -y
1.2 Verify Prometheus Status
sudo systemctl status prometheus
1.3 Access Prometheus Dashboard
Open browser and navigate to:

http://localhost:9090
1.4 Monitor CPU Usage
Run the following query:

100 - (avg by(instance)(irate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)
1.5 Monitor Memory Usage
node_memory_Active_bytes / node_memory_MemTotal_bytes * 100
 Task 2: Review Ingestion & Indexing Performance:
2.1 Analyze Log Ingestion Rate
rate(log_entries_total[1m])
2.2 Observe Indexing Performance
Monitor delays in log appearance

Compare ingestion time vs indexed time

Identify spikes during high load

 Task 3: Identify Bottlenecks and Errors:
3.1 Review System Logs
grep -i "error" /var/log/syslog
3.2 Identify Bottlenecks
Repeated warning/error messages

High CPU or memory usage during indexing

Log processing delays

3.3 Suggested Mitigations
Increase system RAM or CPU allocation

Optimize log retention policies

Reduce unnecessary log verbosity

Scale ingestion pipelines if required

 Verification:
CPU and memory metrics visible in Prometheus

Ingestion metrics updating in real time

Errors successfully identified in system logs

 What I Learned:
How to monitor SIEM host performance using Prometheus.

How CPU and memory constraints affect log ingestion.

How to identify system bottlenecks through logs.

Importance of proactive performance monitoring in SIEM environments.

 Conclusion:
This lab demonstrated how to review and analyze system health and performance of a SIEM host. By monitoring CPU, memory usage, ingestion rates, and system logs, potential issues can be detected early and resolved before impacting security operations.
