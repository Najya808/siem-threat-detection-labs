# Lab: Enabling Firewall or Router Logs

## Objectives
- Understand the process of enabling logs on firewalls or routers.
- Configure the log level and destination for efficient monitoring.
- Verify that logging is correctly configured and logs are being captured by a Security Information and Event Management (SIEM) system.

## Prerequisites
- Basic understanding of firewalls and routers.
- Access to a compatible router or firewall device (preferably open-source).
- A basic setup of a SIEM solution (e.g., OSSIM or Wazuh).
- Administrative access to the network device.
- Terminal or command-line tools installed on the local machine.

## Lab Tasks

### Task 1: Identify Router/Firewall Log Support
1. **Access your Router:**  
   Log into your network device via web interface or SSH terminal.

2. **Check for Syslog Support:**  
   - **Web Interface:** Navigate to logging or advanced settings section to check if syslog is supported.  
   - **Command Line:** Use commands like `show logging` or `syslog status` to verify support.

   **Example:**
   ```bash
   show logging
Note: Open-source software like pfSense or OpenWrt typically supports syslog.

Task 2: Configure Log Level and Destination
Setup Syslog Destination:

Web Interface: Enter the IP address of your SIEM server as the syslog server destination.

Command Line:

set system syslog host <SIEM_SERVER_IP> facility local0
Configure Log Level:

Web Interface: Choose the desired verbosity level (Debug, Info, Error) based on monitoring needs.

Command Line:

set system syslog facility local0 level debug
Task 3: Verify Logs are Reaching the SIEM
Check SIEM System:
Query your SIEM for logs indexed from the firewall/router.

Troubleshoot if Necessary:

Ensure network connectivity between device and SIEM server.

Validate syslog server IP and port settings.

Use tools like tcpdump or Wireshark to monitor traffic.

Example:

tcpdump -i eth0 'udp port 514 and host <ROUTER_IP>'
Conclusion
In this lab, we explored the process of enabling and configuring router or firewall logs using syslog. Proper configuration ensures logs are transmitted to a SIEM system for effective network event monitoring. This lab highlights the importance of logging in security, anomaly detection, and incident response, using open-source tools for a cost-effective approach.

What I Learned
How to access and configure logging on a firewall or router via both web interface and CLI.

How to set up a syslog destination and define log levels for monitoring.

The importance of verifying that logs reach a SIEM system for security and operational awareness.

Troubleshooting techniques for log transmission issues using tools like tcpdump or Wireshark.

Understanding the role of firewall/router logs in detecting security incidents and ensuring network integrity.
