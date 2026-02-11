# Lab 06 — Navigating the SIEM Interface

---

## Lab Overview
This lab focused on understanding the layout and navigation of a SIEM interface.  
The goal was to become familiar with dashboards, alerts, configuration panels, and user customization settings within a SIEM platform such as ELK Stack.

---

## Objectives
- Understand the layout of a SIEM interface
- Navigate dashboards and monitoring panels
- Explore alert management sections
- Learn configuration and user customization options

---

## Tools & Technologies
- ELK Stack (Elasticsearch, Logstash, Kibana)
- Web Browser
- Linux Environment
- Python (Selenium example)
- JSON Configuration

---

## Task 1 — Access SIEM GUI

### Login Process
- Opened SIEM login page in browser
- Entered username and password
- Accessed SIEM dashboard interface

### Automation Practice (Python Selenium Example)
```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get('http://siem.example.com/login')

username = driver.find_element_by_id('username')
password = driver.find_element_by_id('password')

username.send_keys('your_username')
password.send_keys('your_password')
driver.find_element_by_name('login').click()
Task 2 — Identify Key Sections
Dashboards
Observed security monitoring widgets

Viewed traffic summaries and threat activity

Examined visual data panels

Alerts Section
Navigated alert dashboard

Reviewed alert severity levels

Inspected detailed alert logs

Configuration Panel
Explored input sources

Reviewed parsing rules

Checked output destinations

Task 3 — User Settings & Customization
User Profile Settings
Accessed account settings

Reviewed notification preferences

Observed password and profile options

Theme & UI Customization
Example JSON configuration:

{
  "uiSettings": {
    "theme": "dark",
    "language": "en-US"
  }
}
Key Concepts Learned
SIEM Interface Navigation

Dashboard Monitoring

Alert Management

Security Event Visualization

UI Customization

What I Learned
How to navigate and explore a SIEM interface

How dashboards display real-time security data

How alerts are structured and analyzed

The role of configuration panels in SIEM management

Importance of user customization for better usability

Conclusion
This lab provided hands-on exposure to navigating a SIEM interface.
Understanding dashboards, alerts, and configuration areas improves the ability to monitor security events effectively.
Customization options enhance the user experience and make security monitoring more efficient.

