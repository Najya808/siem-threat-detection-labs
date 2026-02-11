# Lab 12: Custom Field Extraction

## Objectives
- Understand the concept of custom field extraction in log management.
- Learn how to utilize regex and Grok patterns for field extraction.
- Validate extracted fields within an SIEM (Security Information and Event Management) tool.

## Prerequisites
- Basic understanding of log formats and log management.
- Familiarity with regex syntax.
- Access to an open-source SIEM tool with appropriate permissions.
- Sample logs with missing fields or unrecognized formats.

## Lab Tasks

### Task 1: Identify Logs with Missing Fields
#### 1.1 Access the Log Interface
- Open the log management interface of your chosen SIEM tool (e.g., Elasticsearch, Logstash, Kibana (ELK) stack).

#### 1.2 Find Logs with Issues
- Navigate through your logs to locate entries with missing fields or entries that do not align with the default log format.  
- Example: Logs where the timestamp or IP address is not parsed correctly.

### Task 2: Extract Fields Using Regex
#### 2.1 Regex Basics
- A regular expression (regex) is a sequence of characters defining a search pattern.  
- Basic syntax example: `^[a-zA-Z0-9]+`

#### 2.2 Create a Regex Pattern
- Identify the pattern of the data you wish to extract.  
- Example: To extract an IP address: `(\d{1,3}\.){3}\d{1,3}`

#### 2.3 Apply Regex in SIEM
- Use a query console or interface within the SIEM tool to apply the regex pattern.  

**Example in Kibana:**
```json
{
  "query": {
    "regexp": {
      "message": {
        "value": ".*regex_pattern.*"
      }
    }
  }
}
Task 3: Use Grok for Field Extraction
3.1 Understanding Grok Patterns
Grok uses predefined patterns for log parsing.

It simplifies complex regex into readable patterns.

Example: %{IPORHOST:clientip} %{USER:ident} %{USER:auth} \[%{HTTPDATE:timestamp}\]

3.2 Define a Grok Pattern
Use online Grok debugger tools to build the necessary pattern.

Example for a typical syslog line:

%{SYSLOGTIMESTAMP:logdate} %{DATA:logsource} %{DATA:program}(?:\[%{POSINT:pid}\])?: %{GREEDYDATA:logmessage}
3.3 Implement Grok in SIEM
If using Logstash, implement via the Grok filter plugin:

filter {
  grok {
    match => { "message" => "%{SYSLOGTIMESTAMP:logdate} %{DATA:logsource} %{GREEDYDATA:logmessage}" }
  }
}
Task 4: Validate Extracted Fields
4.1 Review Extracted Data
Check the parsed data in the SIEM interface to ensure fields are extracted correctly.

Review field headers to see the new custom fields.

4.2 Data Quality Check
Validate that extracted fields correctly represent the log data.

Ensure no important information is lost or misinterpreted.

Conclusion
By completing this lab, you have learned how to perform custom field extraction using regex and Grok patterns in a log management system. These skills enable you to handle unexpectedly formatted log data and ensure accurate log analysis and security monitoring.

What I Learned
How to identify logs with missing or unrecognized fields.

The basics of regex syntax and its application for field extraction.

How to define and implement Grok patterns for easier and more readable parsing.

Methods to validate extracted fields and ensure data integrity.

Importance of custom field extraction for accurate log analysis and effective security monitoring
