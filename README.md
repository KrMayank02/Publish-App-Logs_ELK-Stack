# Publishing Application Logs Directly to ELK Stack (Elasticsearch, Logstash, and Kibana) & Filebeat

**Objective:** To automate the application log monitoring across environments using the ELK stack and a NodeJS application. This streamlines log collection, processing, and visualization with Elasticsearch, Logstash, and Kibana. The goal is to create dashboards and alerts for faster, high-quality software delivery.

**Real-time scenario:** General Insurance, a leading global insurance provider based in the US, offers various products such as home, health, car, and life insurance. The company is transitioning to a DevOps architecture and aims to automate continuous monitoring across its environments.
To achieve this, they have adopted the ELK stack as their application monitoring tool. ELK stack will collect and process application logs using Logstash. However, to support the microservices architecture running on Docker containers, logs will be sent directly to the ELK stack.
By using ELK Stack and Docker, the company aims to provide continuous feedback to developers, speeding up software delivery, improving quality, and reducing the feedback loop between developers and testers.


**Major Tools, Environment Used in This Project:**
------------------------------------------------
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
-------------------------

- Install Pre-requisites: Java (JDK), Docker, Docker-compose
- Install and Configure Elasticsearch
- Install and Configure Logstash
- Install and Configure Kibana
- Install and Configure Filebeat
- Clone the Github repo of Node-js App source code
- Prepare Dockerfile for Node-js App
- Prepare docker-compose.yaml file to configure & run the App
- Verify Node-js App logs at 
    -	Container local logs path
    - Host/Server > volume logs path
    -	Kibana GUI
- Create Kibana Dashboard for logs Data Visualization & Analysis


**Output Result Screenshots:**
-------------------------------

Verify whether the Elasticsearch service is running by sending an HTTP request:

<img width="777" height="493" alt="image" src="https://github.com/user-attachments/assets/e7d309c4-dacb-4785-b806-dddfdaf1e803" />
-------------------------------------------------------------------------------

Logstash:

<img width="905" height="143" alt="image" src="https://github.com/user-attachments/assets/3113c986-ff1a-4604-aeb7-0d17c4c8cc3c" />
------------------------------------

Access Kibana GUI on Browser, with URL: http://100.24.35.222:5601/

<img width="867" height="728" alt="image" src="https://github.com/user-attachments/assets/8700063d-8d33-4626-82c1-bf6eba10228a" />
----------------------------------

Filebeat inputs:

<img width="935" height="615" alt="image" src="https://github.com/user-attachments/assets/924dc643-0078-4685-b49c-c75e174182f9" />
---------------------------------

<img width="883" height="273" alt="image" src="https://github.com/user-attachments/assets/422403e8-0e58-4c50-b7b7-3359e520fc7e" />
------------------------------------------------------------------------------------------------------------------------------

<img width="844" height="257" alt="image" src="https://github.com/user-attachments/assets/c7ec2d7c-f6a8-4d92-b9d8-c9e212e7f08b" />
------------------------------------------------------------------------------------------------------------------------------

The below command displays that Elasticsearch is loading multiple logs under the index searched for pattern “filebeat-*“

<img width="966" height="681" alt="image" src="https://github.com/user-attachments/assets/1808ea7e-9dd7-46ad-ba29-d71e568643e1" />
------------------------------------------------------------------------------------------------------------------------------

Check the instruction in Dockerfile:

vi Dockerfile

<img width="425" height="421" alt="image" src="https://github.com/user-attachments/assets/a6d59b36-bdad-466e-aa19-4cf8cc82d827" />
-------------------------------------------------------------------------------------------------------------------------

Check the instructions in docker-compose.yml:

vi docker-compose.yml

<img width="491" height="473" alt="image" src="https://github.com/user-attachments/assets/cd436fb0-ce14-4864-b6bf-188b84fec1fb" />
-----------------------------------------------------------------------------------------------------------------------

Let’s hit the App URL on browser to generate app specific logs:

http://100.24.35.222:8080

http://100.24.35.222:8080/post

<img width="650" height="303" alt="image" src="https://github.com/user-attachments/assets/a625de8e-845f-4906-8beb-247585910fff" />


<img width="677" height="296" alt="image" src="https://github.com/user-attachments/assets/684b83e9-166c-4ed4-8fc0-21879ddae51c" />

Both these URLs have been hit 9 times. So, the logs will be generated for 9 hits.
--------------------------------------------------------------------------------------------------------------------

Let’s verify Node-js App logs inside the docker container:

<img width="947" height="418" alt="image" src="https://github.com/user-attachments/assets/b7734f11-a71f-42a6-9205-57214fcc3416" />

Hence, for 9 Hits on Browser – App URL, 9 times logs have been generated with correct message. This is generated inside container.
---------------------------------------------------------------------------------------------------------------------

Let’s check the App logs on Volume at Host path mapped with container path.

cd /home/ubuntu/elk-project/nodejs-logs/

ls

cat app.log

<img width="939" height="343" alt="image" src="https://github.com/user-attachments/assets/d3f6594c-057f-490c-9142-ae9881ac5cb4" />
-------------------------------------------------------------------------------------------------------------------------

A long list of System logs and Application Logs are being displayed on Kibana GUI with index pattern “filebeat-*”

<img width="865" height="467" alt="image" src="https://github.com/user-attachments/assets/bcb9cdc8-fd93-4971-aaf6-fd6c49d9d069" />
------------------------------------------------------------------------------------------------

<img width="958" height="492" alt="image" src="https://github.com/user-attachments/assets/640c3d02-f1cb-4133-8a08-99018ca15fcb" />
--------------------------------------------------------------------------------------------------

<img width="963" height="494" alt="image" src="https://github.com/user-attachments/assets/b7314982-9c07-4588-a3bf-463a72b60328" />
--------------------------------------------------------------------------------------------------------------------

Create Dashboard, modify the Visualization Type as required: here we have chosen three dashboard type respectively: Pie, Bar Horizontal and Metric.

<img width="961" height="497" alt="image" src="https://github.com/user-attachments/assets/efc60884-bd9f-4b69-8c4f-fc9ba76d673b" />
-----------------------------------------------------------------------------------------------------

<img width="927" height="468" alt="image" src="https://github.com/user-attachments/assets/fc000161-9687-4767-9c0a-cfd7cd7b1eda" />
---------------------------------------------------------------------------------------------------------

<img width="935" height="358" alt="image" src="https://github.com/user-attachments/assets/d46d8c95-0f80-4c79-8ace-ec1e9682426e" />
---------------------------------------------------------------------------------------------------------

**Now, the Objective of the Project has been met: This streamlines log collection, processing and visualization with Elasticsearch, Logstash, Kibana and Filebeat with Nodejs-Application.**
**Hence, the Project is finally completed!**

