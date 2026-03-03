# Publishing Application Logs Directly to ELK Stack (Elasticsearch, Logstash, and Kibana) & Filebeat

**Objective:** To automate the application log monitoring across environments using the ELK stack and a NodeJS application. This streamlines log collection, processing, and visualization with Elasticsearch, Logstash, and Kibana. The goal is to create dashboards and alerts for faster, high-quality software delivery.

**Real-time scenario:** General Insurance, a leading global insurance provider based in the US, offers various products such as home, health, car, and life insurance. The company is transitioning to a DevOps architecture and aims to automate continuous monitoring across its environments.
To achieve this, they have adopted the ELK stack as their application monitoring tool. ELK stack will collect and process application logs using Logstash. However, to support the microservices architecture running on Docker containers, logs will be sent directly to the ELK stack.
By using ELK Stack and Docker, the company aims to provide continuous feedback to developers, speeding up software delivery, improving quality, and reducing the feedback loop between developers and testers.

**Major Tools, Environment Used in This Project:**

- Node-JS App
- Elasticsearch
- Kibana
- Logstash
- Filebeat
- Docker
- Docker Compose
- AWS EC2 Instance: Ubuntu-22.04, 8GB RAM, 2 vCPU (as Host Machine)
- Java: Version: open-jdk 11
- GitHub Repo for App Source Code

**High Level Project Diagram:**
------------------------------------
ELK Architecture with Node-js App

<img width="942" height="446" alt="image" src="https://github.com/user-attachments/assets/c0ca270c-46c5-41fa-9d1c-34e39ae5d07f" />
--------------------------------------------------------------------------------------------------------------------------------

**High Level Tasks/Steps:**

- Install Pre-requisites: Java (JDK), Docker, Docker-compose
- Install and Configure Elasticsearch
- Install and Configure Logstash
- Install and Configure Kibana
- Install and Configure Filebeat
- Clone the Github repo of Node-js App source code
- Prepare Dockerfile for Node-js App
- Prepare docker-compose.yaml file to configure & run the App
- Verify Node-js App logs at 
  •	Container local logs path
  •	Host/Server > volume logs path
  •	Kibana GUI
-Create Kibana Dashboard for logs Data Visualization & Analysis

