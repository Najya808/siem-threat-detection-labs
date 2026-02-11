 Lab 07 — Configuring Data Sources
 Lab Overview:

This lab focused on configuring data sources for SIEM log collection.
The main goal was to collect logs from network devices and endpoints using open-source tools and verify successful data ingestion.

 Objectives:

Identify important data sources for log collection

Configure log ingestion pipelines

Validate real-time log monitoring

Understand log formatting and classification

 Tools & Technologies:

Syslog-ng

NXLog (Windows Log Agent)

Linux CLI

Router Syslog Configuration

Log Monitoring

 Task 1 — Identify Data Sources:
Selected Sources

Router (network logs)

Windows PC (system & application logs)

Local Linux system logs

Log Types

Network traffic events

User activity logs

System events

Application logs

⚙️ Task 2 — Configure Log Collection
Install Syslog-ng
sudo apt-get update
sudo apt-get install syslog-ng

Basic Syslog-ng Configuration
@version: 3.5
source s_local { system(); internal(); };
destination d_local { file("/var/log/messages"); };
log { source(s_local); destination(d_local); };

Router Configuration

Access router admin panel

Enable remote syslog

Set SIEM/Linux server IP as log destination

Windows Agent (NXLog)
<Input in>
  Module im_msvistalog
</Input>

<Output out>
  Module om_uds
  UnixSocket /dev/log
</Output>

<Route 1>
  Path in => out
</Route>

 Task 3 — Verify Data Ingestion:
Monitor Logs
tail -f /var/log/messages

Validation Checks

Logs appear in real time

Device names present

Timestamps correct

Event codes visible

 Key Concepts Learned:

Data source integration

Centralized logging

Syslog protocol basics

Endpoint log forwarding

Real-time log monitoring

 What I Learned:

How to configure log ingestion from multiple devices

How routers and Windows systems send logs to SIEM

How to verify log flow using Linux commands

Importance of structured logging for security analysis
