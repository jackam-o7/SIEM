<h1>Building a home Security Information & Events Manager (SIEM) Lab</h1>


<h2>Description</h2>
In this project, I am setting up an Elastic Stack Security Information and Event Management (SIEM) system within a home lab environment. This project will involve deploying and configuring the Elastic Stack, a powerful suite of open-source tools for monitoring, logging, and data visualization. The primary objective is to gain hands-on experience with Elastic Stack’s capabilities, particularly in the context of cybersecurity operations, by setting up a functional SIEM system that can collect, analyze, and visualize log data from various sources.

<br />


<h2>Languages and Utilities Used</h2>

- <b>Elastic</b> 
- <b>VirtualBox</b>
- <b>Nmap</b>
- <b>Bash/Terminal</b>
- <b>KQL (Kusto Query Language) </b>

<h2>Environments Used </h2>

- <b>Kali Linux</b> 
  

<h2>Program walk-through:</h2>

<h3>Environment Setup</h3>

<b> 1) Creating an Elastic Account: </b>
- The first step involved creating an Elastic account. This account provides access to the Elastic Cloud, which allows for the deployment of Elastic Stack components like Elasticsearch, Kibana, and more. </br>

<b> 2) Downloading and setting up Kali Linux </b> </br>
- A Kali Linux virtual machine was chosen as the environment for conducting this project. Kali Linux is a popular Linux distribution tailored for cybersecurity tasks.
- The virtual machine was downloaded in a .rar format and was extracted to obtain the necessary files for use with VirtualBox.
- The extracted files were then used to create and launch the Kali Linux virtual machine in VirtualBox.

<b> 3) Starting the Elastic free trial </b> </br>
- After setting up the virtual environment, the next step was to start a free trial of Elastic Cloud. This trial provides full access to Elastic's offerings, including Elasticsearch, Kibana, and other components essential for building a SIEM system.

<h3>Elastic Stack Deployment</h3>

<b> 1) Deployment Type: Elasticsearch: </b>
- The Elastic deployment was initiated with Elasticsearch as the deployment type. Elasticsearch is the core component of the Elastic Stack, responsible for storing, searching, and analyzing large volumes of data in real-time.

<b> 2) Preparing to set up an Agent for Log Collection: </b>
- The next critical step is setting up an agent to collect logs. The agent will be responsible for gathering log data from various sources within the environment and sending it to Elasticsearch for storage and analysis.
- Options for agents include Elastic Agent and Filebeat, both of which are suitable for log collection, though they have different capabilities and use cases.

<b> 3) Setting up Elastic Agent for Log Collection: </b>
- To collect logs and other data, Elastic Agent was elected for use. Elastic Agent simplifies log and metric collection and integrates with Elasticsearch to enhance SIEM capabilities.
- The Elastic Agent was downloaded onto Kali Linux using the following commands: </br>

<img src="https://i.imgur.com/psD4uHC.png" height="60%" width="60%" alt="Elastic Agent downloading to Kali"/> <br/>

<b> 4) Verifying Elastic Agent Installation: </b>
- To confirm that the Elastic Agent was installed correctly, the following command was used to check the status of the Elastic Agent service:
   - ‘sudo systemctl status elastic-agent.service’ </br>
   
<img src="https://i.imgur.com/1TsSg1B.png" height="40%" width="40%" alt="Verifying Elastic Agent Installation"/> <br/>

<h3>Monitoring and Analysis</h3>

With the Elastic Stack SIEM successfully set up and operational, the next step is to focus on monitoring and analysis. My SIEM is now capable of collecting, indexing, and visualizing security events, allowing me to gain valuable insights into the security posture of my environment. I began this phase by simulating security events to ensure that the SIEM is capturing and processing data correctly. Following this, I will create and configure dashboards to help visualise the collected data, making it easier to monitor and analyse security events in real-time. The goal is to leverage these tools to detect patterns, identify anomalies, and continuously refine your security monitoring strategy.

<b> 1) Simulating Security Events: </b>
- To test the Elastic SIEM setup and ensure that it is capturing security events, Nmap was used to generate network activity on the Kali VM.
- The following Nmap scans were performed:
   - ‘sudo nmap -p- localhost’
   - ‘sudo nmap -sS localhost’

<b> 2) Checking Logs for Nmap Scans: </b>
- After simulating the security events, the logs were checked to verify that the Nmap scan data was being sent and indexed by the Elastic SIEM.
- Steps included:
  - Access the logs of my Elastic Deployment
  - Filter the logs for any related to Nmap scans
- I filtered the logs using the KQL query ‘process.args: nmap’

<img src="https://i.imgur.com/DxUMmAE.png" height="60%" width="60%" alt="Searching the logs"/> <br/>

By generating and analyzing different types of security events in Elastic SIEM like the one above, or generating authentication failures by typing in the wrong password for a user or attempting SSH logins an incorrect password, you can gain a better understanding of how security incidents are detected, investigated, and responded to in real-world environments.

<b> 3) Creating a dashboard to visualise events: </b>
- Dashboards and visualizers are crucial for maximizing the effectiveness of your SIEM setup. They transform complex security data into intuitive charts and graphs, making it easier to interpret, monitor, and analyze logs. By providing real-time insights and trend analysis, dashboards help in identifying patterns and anomalies quickly, enhancing your ability to detect and respond to security threats. This visual approach not only improves decision-making and reporting but also ensures that you can proactively manage and optimize your security posture

<b> Creating my dashboard </b>
- To set up my dashboard, I first accessed the Elastic Cloud portal and created a new dashboard by selecting "Dashboards" under the "Analytics" section. I then added a visualization, choosing either an "Area" or "Line" chart to display the count of events over time. In the visualization editor, I configured the metrics by setting "Count" for the vertical axis and "Timestamp" for the horizontal axis, and saved the visualization. Finally, I completed the dashboard setup with any additional settings as needed.

<img src="https://i.imgur.com/lzXdsfi.png" height="60%" width="60%" alt="Creating my dashboard"/> <br/>

<b> 4) Creating an alert: </b>
- In a SIEM, alerts are a crucial feature for detecting security incidents and responding to them in a timely manner. Alerts are created based on predefined rules or custom queries, and can be configured to trigger specific actions when certain conditions are met. In this task, we will walk through the steps of creating an alert in the Elastic SIEM instance to detect Nmap scans. By following these steps, you can create an alert that will monitor your logs for Nmap scan events and then notify you when they are detected.

<img src="https://i.imgur.com/Zbkpi5d.png" height="60%" width="60%" alt="Creating my alert"/> <br/>

- Now that I have created my alert, it will monitor my logs for Nmap scan events. If an Nmap scan event is detected, the alert will be triggered and I will receive an Email.

<img src="https://i.imgur.com/AvNrQgP.png" height="60%" width="60%" alt="Receiving my alert"/> <br/>
