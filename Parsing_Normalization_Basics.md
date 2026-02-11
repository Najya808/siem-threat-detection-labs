# Lab: Parsing & Normalization Basics

## Objectives
- Understand the fundamentals of parsing and normalization in data processing workflows.
- Gain hands-on experience in reviewing and identifying key fields in log data.
- Learn to verify and configure parsers or pipelines to ensure data accuracy and integrity.

## Prerequisites
- Basic knowledge of data formats such as JSON, CSV, or XML.
- Familiarity with command line operations.
- Access to a SIEM tool or log parsing system that supports open-source configurations.

## Lab Tasks

### Task 1: Reviewing Sample Logs
#### 1.1 Access Sample Log Data
- Open your SIEM tool.  
- Navigate to the section containing log data.

#### 1.2 Identify Key Fields
- **Timestamp:** Locate the field that denotes when the log event occurred.  
- **Source IP:** Identify the field that shows the source of the log event.  
- **Event ID:** Find the field that uniquely identifies events.  

**Example Log Line:**
```json
{
    "timestamp": "2023-10-15T13:45:30Z",
    "source_ip": "192.168.1.1",
    "event_id": "abc123",
    "event_type": "UserLogin"
}
Task 2: Checking Parser Configuration
2.1 Understanding Parser Functionality
Understand how parsers map data formats into structured fields.

Recognize the difference between structured and unstructured data.

2.2 Accessing the Parser Configuration
Locate the configuration files for your parsing tool (e.g., JSON pipeline files in Elasticsearch).

Check for mappings related to key fields like timestamp, source IP, and event ID.

Sample Parser Configuration:

{
    "description" : "Field Extraction for Log Data",
    "processors" : [
        {
            "date" : {
                "field" : "timestamp",
                "formats" : ["ISO8601"]
            }
        },
        {
            "rename": {
                "field": "ip_addr",
                "target_field": "source_ip"
            }
        }
    ]
}
Task 3: Verifying the Parsing Process
3.1 Testing the Parser
Introduce a sample log into the system.

Use built-in tools to verify that fields are correctly parsed.

3.2 Debugging and Corrections
Ensure the timestamp field uses a correct time format.

Validate source IP against standard IP formats.

Check event IDs for consistency and uniqueness.

Conclusion
Through this lab, you should have developed a foundational understanding of parsing and normalization. Practicing these tasks ensures that log data is accurately represented and easily queryable within analytical tools. These skills are critical for maintaining the integrity and usability of data processing workflows, especially when using open-source technologies.

What I Learned
How to identify key fields in log data such as timestamp, source IP, and event ID.

The role of parsers in converting unstructured logs into structured, queryable data.

How to access and understand parser configuration files for different log processing tools.

Methods to test, debug, and validate parsing accuracy to ensure data integrity.

Importance of parsing and normalization in maintaining reliable and actionable data workflows.
