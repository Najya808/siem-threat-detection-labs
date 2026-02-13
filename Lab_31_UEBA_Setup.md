# Lab 31 Setting Up User and Entity Behavior Analytics (UEBA) (Optional)

## Lab Objectives
- Understand and configure User and Entity Behavior Analytics (UEBA) to detect anomalies.
- Learn to identify unusual user account activities using open-source tools.
- Interpret UEBA outputs to enhance security measures.

## Prerequisites
- Familiarity with basic network security principles.
- Understanding of user account management and security configurations.
- Access to a Linux server with internet connectivity.
- Basic knowledge of Git and command-line operations.

## Tools Required
- Elastic Stack (ELK Stack) – Open-source log management tool.
- Filebeat and Auditbeat – For log forwarding.
- Kibana – For data visualization.

---

## Lab Tasks

### Task 1: Set Up Elastic Stack for UEBA

#### 1.1 Install Elasticsearch
Ensure Java is installed (Elasticsearch requires it).

```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.15.2-amd64.deb
sudo dpkg -i elasticsearch-7.15.2-amd64.deb
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
1.2 Install Kibana
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.15.2-amd64.deb
sudo dpkg -i kibana-7.15.2-amd64.deb
sudo systemctl start kibana
sudo systemctl enable kibana
Task 2: Enable UEBA Features
2.1 Install Filebeat and Auditbeat
Filebeat

wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.15.2-amd64.deb
sudo dpkg -i filebeat-7.15.2-amd64.deb
Auditbeat

wget https://artifacts.elastic.co/downloads/beats/auditbeat/auditbeat-7.15.2-amd64.deb
sudo dpkg -i auditbeat-7.15.2-amd64.deb
2.2 Configure Filebeat for Data Ingestion
Edit configuration file:

sudo nano /etc/filebeat/filebeat.yml
Modify Elasticsearch output:

output.elasticsearch:
  hosts: ["localhost:9200"]
Start and enable Filebeat:

sudo systemctl start filebeat
sudo systemctl enable filebeat
Task 3: Review a Sample User Behavior Timeline
3.1 Set Up Visualizations in Kibana
Open Kibana: http://localhost:5601

Navigate to Discover to access ingested logs.

Create visualizations to analyze user actions over time.

3.2 Identify Unusual Activity
Use Kibana's Machine Learning features to automatically detect anomalies.

Evaluate alerts for false positives.

Fine-tune anomaly detection settings for better accuracy.

Key Concepts
UEBA: Detects hacker activities or insider threats by identifying deviations from normal user behavior.

Anomaly Detection: Utilize machine learning to identify outliers indicating potential security risks.
