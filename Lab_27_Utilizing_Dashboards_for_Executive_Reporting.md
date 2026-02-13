# Lab 27: Utilizing Dashboards for Executive Reporting

## Objectives
- Understand the basics of creating dashboards for executive reporting.
- Generate easy-to-read charts displaying daily incidents and top event types.
- Learn to use descriptive labels and minimize technical jargon.
- Gain experience in exporting or sharing dashboard links.

## Prerequisites
- Basic understanding of data visualization concepts.
- Familiarity with open-source dashboarding tools (Grafana or Kibana).
- Access to a dataset containing daily incidents and event types.
- Installed and configured Grafana or Kibana.

---

## Key Concepts
- **Dashboards:** Graphical representation tools used in executive reporting.
- **Charts:** Visual elements (bar charts, line graphs, pie charts) representing data.
- **Labels:** Textual identifiers describing the data.
- **Exporting:** Saving or sharing a dashboard with other users.

---

## Lab Tasks

### Task 1: Setting Up the Dashboard Environment
1. **Install Grafana or Kibana**  
   - Follow the official installation guides:  
     - [Grafana Installation Guide](https://grafana.com/docs/grafana/latest/installation/)  
     - [Kibana Installation Guide](https://www.elastic.co/guide/en/kibana/current/install.html)

2. **Access the Dashboard Tool**  
   - Launch Grafana/Kibana.  
   - Navigate in a web browser:  
     - Grafana: `http://localhost:3000`  
     - Kibana: `http://localhost:5601`

---

### Task 2: Creating Charts for Daily Incidents
1. **Import Your Data Source**  
   - Go to Data Sources → Add Data Source → Connect to your dataset.  
   - Example: MySQL database in Grafana with connection details.

2. **Design Daily Incidents Chart**  
   - Create a new dashboard → Add Panel → Choose chart type (Time Series or Bar Chart).  
   - Add query for daily incidents:  
     ```sql
     SELECT date, COUNT(incident_id) AS incident_count
     FROM incidents
     GROUP BY date;
     ```

3. **Apply Formatting and Labels**  
   - Label x-axis as "Date" and y-axis as "Number of Incidents".  
   - Configure thresholds or color coding.  
   - Keep language non-technical for executives.

---

### Task 3: Visualizing Top Event Types
1. **Create Pie Chart for Event Types**  
   - Add a new panel in the same dashboard → Select Pie Chart visualization.  
   - Query top event types:  
     ```sql
     SELECT event_type, COUNT(*) AS event_count
     FROM events
     GROUP BY event_type;
     ```

2. **Customize Pie Chart**  
   - Label each segment clearly with event type names.  
   - Avoid technical jargon.  
   - Adjust chart size and positioning for clarity.

---

### Task 4: Exporting or Sharing the Dashboard
1. **Export Dashboard**  
   - Select Export → Choose format (PDF, PNG, etc.) or generate a shareable link.

2. **Share Dashboard**  
   - Use Grafana's share link functionality for secure access.  
   - Configure permissions so only authorized users can view the report.  
   - Example: Grafana → Click "Share" → "Link" or "Snapshot" for temporary public access.

---

## Conclusion
- Learned to create effective executive dashboards using open-source tools.  
- Gained hands-on skills in importing data, designing charts, applying clear labeling, and exporting dashboards.  
- Can now present complex security data clearly and efficiently to executive stakeholders.
