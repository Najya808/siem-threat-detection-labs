# Lab 15: Basic Correlation Rules

## Objectives
- Understand the concept of correlation rules within a Security Information and Event Management (SIEM) system.
- Learn to identify scenarios of interest such as security threats.
- Develop skills to use open-source tools to define logic and thresholds for correlation rules.
- Generate and test events to ensure rules are correctly triggered.

## Prerequisites
- Basic knowledge of cybersecurity concepts.
- Familiarity with event logging and monitoring systems.
- Access to a computer with an open-source SIEM tool such as ELK Stack or Wazuh.
- Basic understanding of scripting or command-line usage.

## Lab Tasks

### Task 1: Identify a Scenario for Correlation
#### 1.1 Define a Potential Security Threat
- Example scenario: Multiple failed login attempts followed by a successful login (could indicate a brute-force attack).

#### 1.2 Document the Scenario Details
- Specify parameters, including thresholds (e.g., 5 failed logins within 10 minutes).

### Task 2: Use SIEM Rule Editor
#### 2.1 Access SIEM Tool
- Open your SIEM tool (e.g., Wazuh, ELK Stack).  
- For ELK, open Kibana.

#### 2.2 Navigate to the Rule Editor
- In Kibana, access the **Rules** section under the **SIEM** app.

#### 2.3 Define Logic for the Rule
- Set conditions for triggering the alert.

**Example for Elasticsearch (ELK Stack):**
```json
{
  "trigger": {
    "schedule": {
      "interval": "10m"
    }
  },
  "input": {
    "search": {
      "request": {
        "indices": [
          "logs-*"
        ],
        "body": {
          "query": {
            "bool": {
              "must": [
                { "match": { "event.action": "login_failed" } },
                { "range": { "@timestamp": { "gte": "now-10m/m" } } }
              ]
            }
          }
        }
      }
    }
  }
}
2.4 Set Thresholds and Conditions
Establish the number of failed attempts that will trigger the rule.

Task 3: Generate and Test Events
3.1 Write a Script for Generating Log Events
Python Example:

import logging
import time

logging.basicConfig(filename='failed_login_logs.log', level=logging.INFO)

# Simulate failed logins
for i in range(6):
    logging.info(f"Failed login attempt {i+1}")
    time.sleep(2)

# Simulate a successful login
logging.info("Successful login attempt")
3.2 Monitor SIEM for Rule Trigger
Check the alert dashboard in your SIEM to verify if the rule has been triggered by your test script.

Conclusion
Correlation rules are critical for detecting potential security threats. This lab helped you learn to define specific thresholds and conditions for tailored security monitoring. Practicing with different scenarios strengthens your ability to create effective correlation rules using open-source tools like ELK Stack or Wazuh.

What I Learned
The concept and importance of correlation rules in a SIEM.

How to identify and document scenarios of interest, including thresholds for alerts.

How to use a rule editor in ELK Stack or Wazuh to define logic and conditions.

How to generate test events to ensure rules are correctly triggered.

Best practices for monitoring and refining correlation rules to improve security visibility.
