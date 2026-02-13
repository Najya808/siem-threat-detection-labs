# Lab 36: Automating Simple Responses (SOAR Lite) (Optional)

## Objectives
- Understand the fundamentals of Security Orchestration, Automation, and Response (SOAR).
- Configure automated responses to security alerts using open-source tools.
- Illustrate how automation enhances response times and accuracy for simple security events.

## Prerequisites
- Basic understanding of network security concepts.
- Familiarity with command-line interfaces.
- Linux-based system with internet connectivity.
- Basic knowledge of endpoint monitoring tools such as OSQuery.

---

## Task 1: Configure an Automated Response to a Specific Alert

### Step 1: Identify the Alert Scenario
- Choose a simple security alert, e.g., detecting unauthorized port scanning.
- Simulate a scan using Nmap:
```bash
nmap -p 1-65535 <target-ip>
Step 2: Set Up the Monitoring Tool
Install OSQuery to monitor network activity:

sudo apt-get update
sudo apt-get install osquery
Configure the agent to log network events, including unusual connection attempts.

Step 3: Script the Automated Response
Create a script to block scanning IPs:

#!/bin/bash
IP_ADDRESS=$1
iptables -A INPUT -s $IP_ADDRESS -j DROP
echo "Blocked IP: $IP_ADDRESS"
Save as auto_block.sh.

Step 4: Integrate with SOAR Lite
Use a lightweight automation tool like StackStorm to trigger the script when an alert is detected:

st2 rule create auto-block-rule.yaml
Task 2: Test the Rule by Triggering the Condition
Step 1: Simulate an Attack
Execute a port scan against the monitored server:

nmap -p 1-65535 <target-ip>
Step 2: Monitor Alerts
Check OSQuery logs to verify that the alert was captured.

Task 3: Verify the Response Action Was Executed
Step 1: Check Firewall Rules
sudo iptables -L
Confirm that the scanning IP has been added to iptables.

Step 2: Confirm Automation Success
Ensure no further connections from the source IP are accepted.

Review logs to confirm consistent automated responses.

Key Concepts
SOAR (Security Orchestration, Automation, and Response): Automates and streamlines parts of the incident response process.

OSQuery: Queries system and network state like a database.

Iptables: Linux command-line firewall utility.

StackStorm: Open-source event-driven automation platform.

Conclusion
By completing this lab, you will:

Configure automated responses to security alerts using open-source tools.

Demonstrate the efficiency of SOAR solutions in reducing manual response efforts.

Improve response times and consistency for simple cybersecurity events.
