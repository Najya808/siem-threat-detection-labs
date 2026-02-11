# Lab 14: Setting Up Email Notifications

## Lab Objectives
- Understand how to configure email notifications using an SMTP server.
- Learn how to create and test alert rules.
- Verify proper configuration through test alerts and email notifications.

## Prerequisites
- Basic understanding of email systems.
- Access to a system where email notification setup is needed.
- Basic knowledge of command-line interfaces and configuration files.

## 1. Introduction
Email notifications are a crucial part of monitoring systems and applications. They alert users or administrators to events that require attention, such as errors or security breaches. In this lab, you will learn how to set up email notifications using an SMTP server.

## 2. Setting Up SMTP Server

### 2.1 Understanding SMTP
The Simple Mail Transfer Protocol (SMTP) is used for sending emails. You'll need the following settings:
- **Host:** SMTP server address.  
- **Port:** Usually 25, 465, or 587 for TLS/SSL.  
- **Credentials:** Username and password for authentication.

### 2.2 Configuring SMTP Server
1. Open your email client configuration file. Locations may differ, e.g.:  
   `/etc/email_client.conf` or `/etc/alert_system.conf`.
2. Add the SMTP server settings:
```text
smtp_host = smtp.example.com
smtp_port = 587
smtp_username = your_username
smtp_password = your_password
smtp_use_tls = true
Save the file and restart your application (if applicable) to apply the settings.

3. Creating an Alert Rule
3.1 Alert Rule Basics
An alert rule is a condition that triggers an alert notification. In this lab, you'll create a test alert for security purposes.

3.2 Setting Up the Alert Rule
Access your system’s alert configuration tool (web UI or configuration file).

Define a test alert rule to trigger after 5 failed login attempts within 1 minute.

Example configuration:

alert_name = "Failed Login Attempts"
condition = "5 failed logins in 1 minute"
trigger_action = "send_email"
email_recipient = "admin@example.com"
Save and activate the alert rule.

4. Testing and Verification
4.1 Generating a Test Alert
Simulate failed login attempts to trigger the alert.

Monitor logs to confirm if the alert condition is met.

4.2 Verify Email Notification
Check the recipient email account for the notification.

Example:

Subject: Alert: Failed Login Attempts
Message: There have been 5 failed login attempts in the last minute.
Ensure the email is received and the content is correct.

5. Conclusion
In this lab, you successfully configured email notifications by setting up an SMTP server and creating an alert rule to test your setup. You verified the effectiveness through a simulated test alert, confirming the importance of proactive notification systems in maintaining security and performance.

This process ensures timely responses to critical issues and enhances the operational awareness of system administrators.

What I Learned
How to configure an SMTP server for sending email notifications.

How to create alert rules that trigger based on specific conditions.

How to test and verify email notifications to ensure alerts are working correctly.

The importance of proactive notification systems in maintaining system security and performance.

Best practices for operational awareness through automated alerting.

