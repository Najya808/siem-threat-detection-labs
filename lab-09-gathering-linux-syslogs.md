# Lab 09 — Gathering Linux Syslogs

## Lab Overview
This lab focuses on understanding syslog in Linux and forwarding logs to a SIEM system.  
You will configure `rsyslog`, enable log forwarding, and verify logs in the SIEM dashboard.

---

## Objectives
- Understand the basics of syslog in Linux
- Enable and configure `rsyslog` for log collection
- Forward logs from a Linux server to a SIEM system
- Verify log reception and review in a SIEM

---

## Prerequisites
- Basic Linux command line knowledge
- Access to a Linux machine with administrative privileges
- Access to a SIEM system (or a simulated environment)
- SSH client installed for remote access (if needed)

---

## Task 1 — Introduction to Syslog
- **Key Concept:** Syslog is a standard for logging messages in Unix/Linux systems.
- **Rsyslog:** Common application to log program messages for monitoring and auditing.

---

## Task 2 — Enabling Rsyslog Service

### Check Rsyslog Status
```bash
systemctl status rsyslog
Start and Enable Rsyslog (if not active)
sudo systemctl start rsyslog
sudo systemctl enable rsyslog
Task 3 — Configuring Rsyslog for Log Forwarding
Edit Configuration
sudo nano /etc/rsyslog.conf
Enable UDP Listener
module(load="imudp")    # Start UDP listener module
input(type="imudp" port="514")  # Listen on UDP port 514
Forward Logs to SIEM
*.* @<SIEM_IP>:5544
Replace <SIEM_IP> with the IP address of your SIEM server.
Port 5544 is standard but may vary depending on your setup.

Save and Exit
In nano, press CTRL+O then CTRL+X

Restart Rsyslog Service
sudo systemctl restart rsyslog
Task 4 — Verifying Logs on the SIEM
Ensure SIEM is configured to receive logs.

Generate a test log entry:

logger "Test log message from $(hostname)"
Check SIEM dashboard for the new log entry.

Task 5 — Common Case Study
Syslogs are essential for intrusion detection.

Example: Detecting excessive login attempts or unauthorized access by monitoring system logs.

Conclusion
By completing this lab, you have learned to:

Configure rsyslog for syslog management

Forward logs from Linux to a SIEM

Verify log ingestion in the SIEM interface

This setup is crucial for monitoring, troubleshooting, and securing Linux environments.
