# Lab 27: Simple Log Forensics

## Objectives
- Understand the basics of log forensics to identify suspicious activities.
- Learn to use open-source tools for log analysis.
- Identify key log elements such as timestamps, usernames, and IPs for forensic analysis.

## Prerequisites
- Basic knowledge of network protocols.
- Familiarity with command-line interface (CLI).
- Access to a Unix-based system with tools like `grep`, `awk`, and `sed`.
- Sample log files for analysis.

---

## Key Concepts
- **Log Forensics:** Analyzing log files to track system activities and uncover security breaches.
- **Timestamps:** Essential for establishing when events occurred.
- **IP Addresses:** Useful for tracing the origin of suspicious activity.

---

## Lab Tasks

### Task 1: Select a Date/Time Range
1. **Define Time Period**  
   Example: Investigate logs from **July 15, 2023, 10:00 AM to 12:00 PM**.

2. **Filter Logs**  
   Extract logs within the specified time frame:
   ```bash
   grep 'Jul 15 10:' /var/log/auth.log > filtered_logs.txt
   grep 'Jul 15 11:' /var/log/auth.log >> filtered_logs.txt
   grep 'Jul 15 12:' /var/log/auth.log | head -n 30 >> filtered_logs.txt
Task 2: Use Advanced Filters to Isolate Suspicious Activity
Identify Suspicious Patterns
Look for keywords like "failed", "error", "unauthorized":

grep -E 'failed|error|unauthorized' filtered_logs.txt > suspicious_activity.txt
Analyze Login Attempts
Count multiple failed login attempts from the same IP:

awk '/Failed password/ {print $(NF-3)}' filtered_logs.txt | sort | uniq -c | sort -nr
Task 3: Document Evidence
Extract Key Elements
Extract usernames, IPs, and timestamps:

awk '{print $1, $2, $3, $11, $13}' suspicious_activity.txt > evidence.txt
Document Findings
Clearly record the findings, e.g.:

Username: suspicious_user
IP: 192.168.1.10
Timestamp: Jul 15 10:35:19
Conclusion
You have filtered and analyzed log files effectively using CLI tools.

You can identify suspicious activities based on logs and extract key forensic information.

Continued practice enhances proficiency in log forensics and aids in security investigations.
