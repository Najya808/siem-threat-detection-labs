# siem-threat-detection-labs
SIEM &amp; Security Operations (HOA) labs from the Al-Razzaq cybersecurity program focused on threat detection, log analysis, and blue team fundamentals.

- [Lab 01 — Introduction to SIEM](lab-01-introduction-to-siem.md)
-  Learn the basics of Security Information and Event Management (SIEM) and its importance in monitoring and analyzing security events.

- [Lab 02: Understanding HOA Security Needs](lab-02-understanding-hoa-security-needs.md)
-   Learn how to assess security requirements for Homeowners Associations (HOA) and identify key areas for monitoring.
  
- [Lab 03: Preparing the Lab Environment](lab-03-preparing-lab-environment.md)
-   Learn how to set up a safe and functional lab environment for SIEM and log management experiments.

- [Lab 04: Selecting a SIEM Platform](lab-04-selecting-siem-platform.md)
-   Learn how to evaluate and choose the right SIEM platform based on features, compatibility, and use cases.

- [Lab 05: Installing Your Chosen SIEM](lab-05-installing-siem.md)
-   Learn the installation process for your selected SIEM platform, including configuration for initial use.

- [Lab 06: Navigating the SIEM Interface](lab-06-navigating-siem-interface.md)
-   Learn how to explore and navigate the SIEM interface to understand dashboards, alerts, and reporting tools.

- [Lab 07: Configuring Data Sources](lab-07-configuring-data-sources.md)
-   Learn how to connect and configure various data sources so your SIEM can ingest and process logs.

- [Lab 08: Gathering Windows Event Logs](lab-08-gathering-windows-event-logs.md)
-   Learn how to collect and analyze Windows Event Logs to feed into your SIEM for monitoring and alerting.

- [Lab 09: Gathering Linux Syslogs](lab-09-gathering-linux-syslogs.md)
-   Learn how to collect Linux system logs (syslogs) and forward them to your SIEM for analysis.

- [lab 10: Enabling Firewall or Router Logs](Enabling_Firewall_Router_Logs.md)
-   Learn how to enable logging on firewalls or routers, configure log levels and destinations, and verify log transmission to a SIEM system.

- [Lab 11: Parsing & Normalization Basics](Lab_11_Parsing_Normalization_Basics.md)
-   Learn how to review sample logs, check parser configurations, and verify the parsing process to ensure accurate and normalized data in SIEM or log processing tools.

- [Lab 12: Custom Field Extraction](Lab_12_Custom_Field_Extraction.md)
-   Learn how to perform custom field extraction using regex and Grok patterns, validate extracted fields, and handle unexpectedly formatted log data.

- [Lab 13: Basic SIEM Dashboards](Lab_13_Basic_SIEM_Dashboards.md)  
  Learn how to create and customize basic SIEM dashboards, visualize log data, and interpret security metrics using open-source tools.

- [Lab 14: Setting Up Email Notifications](Lab_14_Setting_Up_Email_Notifications.md)  
  Learn how to configure email notifications using an SMTP server, create alert rules, test alerts, and verify notifications for system monitoring.

- [Lab 15: Basic Correlation Rules](Lab_15_Basic_Correlation_Rules.md)  
   Learn how to create SIEM correlation rules, define thresholds and logic for detecting security threats, and test rule triggering using simulated login events.

- [Lab 16: Investigating Alerts in a SIEM System](Lab_16_Investigating_Alerts_in_a_SIEM_System.md)  
   Learn how to locate and analyze SIEM alerts, drill down into raw event logs, document findings, and propose incident response actions based on suspicious activities.

- [Lab 17: Host Monitoring Configuration](Lab_17_Host_Monitoring_Configuration.md)  
   Learn how to install a host intrusion detection agent, enable active monitoring for file changes and suspicious processes, and verify alerts within a SIEM system.

- [Lab 18: Network Traffic & IDS Integration (Optional)](Lab_18_Network_Traffic_IDS_Integration.md)  
   Learn how to install and configure an IDS, integrate IDS alerts with a SIEM system, and generate network traffic to monitor and analyze security events.

- [Lab 19: Creating a Real-Time Dashboard](Lab_19_Real_Time_Dashboard.md)  
   Learn how to build a real-time monitoring dashboard using Prometheus and Grafana, configure live data visualization, and monitor system activity with automated refresh intervals.

- [Lab 20: Role-Based Access Control](Lab_20_Role_Based_Access_Control.md)  
   Learn how to implement RBAC using Linux groups, create analyst and admin roles, enforce read-only permissions, and validate role-based access through practical testing.

- [Lab 21: Searching & Filtering Data](Lab_21_Searching_Filtering_Data.md)  
   Learn how to perform field-based log searches, apply time and severity filters, and save frequently used queries to streamline SIEM data analysis workflows.

- [Lab 22: Index Maintenance & Data Retention](Lab_22_Index_Maintenance_Data_Retention.md)  
   Learn how to maintain database indexes, configure data retention policies, and verify automated handling of outdated logs using open-source systems like PostgreSQL or ElasticSearch.

- [Lab 23: Threat Intelligence Feeds](Lab_23_Threat_Intelligence_Feeds.md)  
   Learn how to integrate threat intelligence feeds into a SIEM system, correlate threat data with inbound logs, and visualize potential threats using open-source tools like ELK Stack or Wazuh.

- [Lab 24: Alarm Tuning](Lab_24_Alarm_Tuning.md)  
   Learn how to identify frequently triggered false positives, apply exception conditions, and test alarm configurations to improve alert accuracy using open-source monitoring tools like Suricata, Snort, or ElastAlert.

- [Lab 25: Basic Incident Response Workflow](Lab_25_Basic_Incident_Response_Workflow.md)  
   Learn how to simulate a security incident using Fail2Ban, document and analyze it in an ELK Stack SIEM, and follow a basic incident response workflow to improve organizational security practices.

- [Lab 26: Utilizing Dashboards for Executive Reporting](Lab_27_Utilizing_Dashboards_for_Executive_Reporting.md)  
   Learn how to create executive-friendly dashboards using Grafana or Kibana. Import datasets, visualize daily incidents and top event types, apply clear labels, and export or share dashboards for management reporting.

- [Lab 27: Simple Log Forensics](Lab_28_Simple_Log_Forensics.md)  
   Learn to perform basic log forensics using CLI tools. Filter logs by date/time, isolate suspicious activity, analyze login attempts, and document evidence including timestamps, usernames, and IPs.

- [Lab 28: Regular Expressions in Log Searches](Lab_28_Regex_in_Log_Searches.md)  
   Learn to use Regular Expressions (Regex) to efficiently search and extract data from log files. Construct patterns for IPs, user IDs, and error codes. Apply these skills in Python scripts or text editors for log parsing and forensic analysis.

- [Lab 29: Analyzing Trends Over Time](Lab_29_Analyzing_Trends_Over_Time.md)  
   Learn to process and visualize time-series data using Python. Build line charts, compute weekly averages, detect anomalies, and export results as PDF snapshots. Mastery of these techniques aids in identifying patterns, monitoring trends, and supporting data-driven decisions.

- [Lab 30: File Integrity Monitoring (Optional)](Lab_31_File_Integrity_Monitoring.md)  
   Learn to monitor file and directory changes using `auditd` on Linux. Configure watches, simulate changes, and verify alerts. FIM helps detect unauthorized modifications, protecting system integrity and supporting proactive security practices.

- [Lab 31: Setting Up User and Entity Behavior Analytics (UEBA) (Optional)](Lab_32_UEBA_Setup.md)  
   Learn to configure UEBA using the Elastic Stack (ELK), Filebeat, and Auditbeat. Set up anomaly detection, visualize user behavior, and detect unusual account activities to enhance cybersecurity monitoring.

- [Lab 32: Backup & Restore of SIEM Data](Lab_32_SIEM_Backup_Restore.md)  
   Learn to perform manual backup and restore of SIEM data (indices and rules) in open-source tools like ELK Stack. Simulate restores in test environments to ensure data integrity and maintain system reliability.
