# Lab 31: File Integrity Monitoring (Optional)

## Objectives
- Understand the fundamentals of File Integrity Monitoring (FIM).
- Learn how to configure FIM using open-source tools.
- Monitor files or directories for changes.
- Trigger and observe alerts for file changes.

## Prerequisites
- Basic knowledge of Linux command-line operations.
- Access to a Linux-based system (Ubuntu, CentOS, etc.).
- Installed packages: `auditd` and `auditctl`.

---

## Introduction
File Integrity Monitoring (FIM) is a crucial cybersecurity process that examines files and directories to detect unauthorized changes. It ensures the integrity and security of system files and configurations. In this lab, we will use `auditd`, an open-source monitoring tool, to implement FIM.

---

## Lab Tasks

### Task 1: Install and Configure auditd

**On Ubuntu**
```bash
sudo apt-get update
sudo apt-get install auditd audispd-plugins
On CentOS

sudo yum install audit audit-libs
Start auditd Service

sudo systemctl start auditd
sudo systemctl enable auditd
Verify Installation

auditctl -v
Task 2: Identify Files/Directories to Monitor
Determine target files for monitoring.

Example: Frequently modified configuration files.

For demonstration, we will monitor /etc/passwd.

Task 3: Configure auditd to Monitor Changes
Create Audit Rule for a File

sudo auditctl -w /etc/passwd -p wa -k passwd_changes
Explanation

-w: Add a watch to the file.

-p: Define permissions to monitor (w=write, a=attribute changes).

-k: Assign a key for easier identification in logs.

List Current Rules

sudo auditctl -l
Task 4: Generate a Change Event
Simulate File Modification

sudo nano /etc/passwd
Add an insignificant change (like a comment), then save and exit.

Task 5: Verify Alert Generation
Check audit Logs

sudo ausearch -f /etc/passwd
Display Specific Change Record

sudo aureport -f --summary | grep passwd_changes
Example Case Study

A company monitored its /etc directory using FIM.

Unauthorized changes were captured, preventing potential breaches.

Conclusion
Successfully set up and tested a basic File Integrity Monitoring system using auditd.

Monitoring system files helps detect unauthorized changes quickly.

Regular log review enhances system security and prevents data breaches.

