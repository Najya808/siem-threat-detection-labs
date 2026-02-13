# Lab 25: Basic Incident Response Workflow

## Objectives
- Understand the basic concepts of incident response.
- Simulate a security incident using open-source tools.
- Document steps taken to respond to the incident in a SIEM system.
- Analyze and close out the incident with a comprehensive summary.

## Prerequisites
- Basic understanding of network security principles.
- Familiarity with Linux command-line interface.
- Installed and configured SIEM solution (e.g., ELK Stack).

## Tools and Environment
- OS: Ubuntu 20.04 LTS or similar.
- SIEM Tool: ELK Stack (Elasticsearch, Logstash, Kibana).
- Simulation Tool: Fail2Ban.

---

## Section 1: Introduction to Incident Response
Incident response involves identifying, managing, and mitigating security threats to ensure minimal operational impact.

**Key Concepts:**
- **Incident:** An event affecting the integrity, availability, or confidentiality of information.
- **Response Workflow:** Systematic steps to manage and mitigate threats.

---

## Section 2: Simulate a Security Incident

### Task 1: Configure Fail2Ban for Repeated Failed Login Attempts

1. **Install Fail2Ban:**
```bash
sudo apt update
sudo apt install fail2ban
Configure Fail2Ban:

sudo nano /etc/fail2ban/jail.local
Add:

[sshd]
enabled = true
port = ssh
logpath = /var/log/auth.log
bantime = 3600
findtime = 600
maxretry = 3
Restart Fail2Ban:

sudo systemctl restart fail2ban
Test Fail2Ban:
Attempt multiple SSH logins with wrong credentials to trigger a ban.

Section 3: Record Steps in SIEM
Task 2: Integrate Fail2Ban with ELK Stack
Ensure Elasticsearch, Logstash, and Kibana are installed and running.

Configure Logstash to Process Fail2Ban Logs:

sudo nano /etc/logstash/conf.d/fail2ban.conf
Add:

input {
  file {
    path => "/var/log/fail2ban.log"
    start_position => "beginning"
  }
}

filter {
  grok {
    match => { "message" => "%{TIMESTAMP_ISO8601:timestamp} %{WORD:level} \[%{WORD:program}\] %{GREEDYDATA:details}" }
  }
}

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "fail2ban-%{+YYYY.MM.dd}"
  }
}
Restart Logstash:

sudo systemctl restart logstash
Verify in Kibana:
Check that Fail2Ban logs are visible. Create visualizations and dashboards for incident analysis.

Assign Incident & Add Comments:
Tag actions taken and assign incidents to analysts in Kibana.

Section 4: Close out the Incident with a Summary
Task 3: Document Incident Closure
Analyze Events: Review captured events and mitigation effectiveness.

Prepare a Summary: Document incident overview, affected systems, actions, resolution, and preventive measures.

Example Summary:

Incident Description: Detection of repeated SSH login failures on October 5, 2023.

Response Actions: Implemented Fail2Ban rules to ban offending IPs, logged events in ELK Stack.

Resolution Time: ~2 hours from detection to resolution.

Preventive Measures: Stricter password policies and more frequent log monitoring.

Conclusion
Successfully simulated a security incident and followed a basic incident response workflow.

Gained hands-on experience with monitoring, analyzing, and documenting intrusion attempts using open-source tools.
