# Lab 23: Threat Intelligence Feeds

## Objectives
- Understand the concept of threat intelligence feeds.
- Learn how to integrate threat intelligence feeds into a SIEM system.
- Identify and correlate threat data to detect potential threats.

## Prerequisites
- Basic understanding of cybersecurity concepts.
- Familiarity with SIEM tools (e.g., ELK Stack, Wazuh).
- Internet access for downloading open-source threat intelligence feeds.

---

## Lab Setup
1. Install and configure an open-source SIEM tool on your system.
2. Ensure the SIEM system is up and operational.

---

## Task 1: Understanding Threat Intelligence Feeds
### 1.1 What are Threat Intelligence Feeds?
- Streams of data providing information on current threats such as malicious IPs, domains, URLs, etc.
- Helps enhance security posture with up-to-date threat data.

### 1.2 Benefits
- **Early Detection:** Quickly identify and respond to threats.
- **Proactive Defense:** Improve decision-making and defensive measures.
- **Contextual Awareness:** Provides context for alarms triggered by the SIEM.

---

## Task 2: Selecting a Threat Intelligence Feed
1. Visit sites like **AlienVault Open Threat Exchange (OTX)** or **VirusTotal**.
2. Choose a feed containing malicious IPs.
   - Example: AlienVault OTX feed.

---

## Task 3: Configuring the SIEM System

### For ELK Stack
**Logstash Configuration** (`logstash.conf`):
```ruby
input {
    http_poller {
        urls => {
            malicious_ips => "http://example.com/malicious-ips-feed"
        }
        request_timeout => 60
        interval => 3600
        codec => "json"
    }
}

output {
    elasticsearch {
        hosts => ["localhost:9200"]
        index => "threat-feed"
    }
}
Start Logstash to fetch and store data:

bin/logstash -f logstash.conf
For Wazuh
Configure OSSEC rules or Syscheck to process the threat feeds.

Task 4: Correlating and Analyzing Data
Configure Alert Rules: Create SIEM alerts that match inbound logs with malicious IPs from the feed.

Visualization: Use Kibana (ELK Stack) or Wazuh Dashboard to visualize alerts and logs.

Task 5: Testing and Validation
Insert known malicious IPs into inbound logs.

Confirm the SIEM generates appropriate alerts.

Verify correct ingestion and alert correlation.

Conclusion
Integrated an open-source threat intelligence feed with a SIEM tool.

Validated data ingestion by simulating threats.

Learned the importance of timely threat intelligence for proactive cyber defense.

