# Lab 18: Network Traffic & IDS Integration (Optional)

## Objectives
- Understand the role of Intrusion Detection Systems (IDS) in network security.
- Install and configure IDS to monitor network traffic.
- Integrate IDS alerts with a SIEM system.
- Generate and analyze network traffic to trigger IDS alerts.

## Prerequisites
- Basic understanding of networking and security concepts.
- Familiarity with Linux command line.
- Access to a Linux system (e.g., Ubuntu).
- Internet connection for downloading tools.
- Optional: Virtual machine software.

---

## Task 1: Install and Configure IDS Rules

### Install Snort IDS
```bash
sudo apt update
sudo apt install snort
Configure Snort
Edit configuration file:

sudo nano /etc/snort/snort.conf
Uncomment:

include $RULE_PATH/community.rules
Test Snort Installation
sudo snort -T -c /etc/snort/snort.conf
Key Concepts
IDS monitors network traffic for suspicious activity.

Community rules provide basic threat detection.

Task 2: Forward IDS Alerts to SIEM
Install ELK Stack
sudo apt install elasticsearch
sudo apt install logstash
sudo apt install kibana
Configure Logstash for Snort Logs
sudo nano /etc/logstash/conf.d/snort.conf
Example:

input {
  file {
    path => "/var/log/snort/alert"
    start_position => "beginning"
  }
}
Start Services
sudo service elasticsearch start
sudo service logstash start
sudo service kibana start
Technical Terms
SIEM centralizes and analyzes security alerts.

Logstash ingests and parses logs.

Task 3: Generate Test Traffic
Generate HTTP Traffic
curl http://example.com
Generate ICMP Traffic
ping -c 4 example.com
Verify Alerts in SIEM
Open Kibana:

http://<Kibana_IP>:5601
Check Snort alerts and logs.

Conclusion
In this lab, you installed and configured an IDS, integrated it with a SIEM system, and analyzed generated network traffic. These skills are essential for real-time threat detection and network monitoring.

