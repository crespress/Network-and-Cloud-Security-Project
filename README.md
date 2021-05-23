## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!https://github.com/crespress/Network-and-Cloud-Security-Project/blob/main/ELKSTACK%20Project%20Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible-playbook file may be used to install only certain pieces of it, such as Filebeat.

  - sudo docker run -ti cyberxsecurity/ansible: latest bash

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.
- What aspect of security do load balancers protect? Load balancers protect the system from DDoS attacks by distributing traffic across multiple servers or applications. What is the advantage of a jump box? The advantage of the jump box is to give access to the user from a single point of access that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- What does Filebeat watch for? Filebeat monitors log files and log events. 
- What does Metricbeat record? Metricbeat record the specified metrics and statics from various OS from various locations.

The configuration details of each machine may be found below.

| Name          | Function | IP Address  |
|---------------|----------|-------------|
| JumpBoxOffsec | Gateway  | 10.0.0.4    |
| Web1-OffSec   | Webset   | 10.0.0.5    |
| Web2-OffSec   | Webset   | 10.0.0.6    |
| Web3-Offsec   | Webset   | 10.0.0.7    |
| OffSecNetElk  | Gateway  | 10.2.0.4    |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxOffsec machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 20.96.32.52

Machines within the network can only be accessed by the network group.
- Which machine did you allow to access your ELK VM? JumpBoxOffSec What was its IP address?10.2.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | IP Address  |
|---------------|---------------------|-------------|
| JumpBoxOffsec | Yes  -  20.96.32.52 | No 10.0.0.4 |
| Web1-OffSec   | No                  | 10.0.0.5    |
| Web2-OffSec   | No                  | 10.0.0.6    |
| Web3-Offsec   | No                  | 10.0.0.7    |
| OffSecNetElk  | No                  | 10.2.0.4    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? Ansible is lightweigh, intelligently shares resources, easily duplicated, prevalent, and redundant.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download images
- unistall apache 2
- install docker.io
- install pip3
- download and launch a docker web container
- enable docker services

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

! file:///Users/candacerespress/OneDrive/ELK%20Stack%20Project/Images/Ansible%20Config%20Files/Docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring - 10.0.0.5, 10.0.0.6, 10.0.0.7

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed - Filebeats and Metricbeats

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. Filebeats stores logs of the data. I expect to see logs of web activity that has taken place in the machines monitored. Metricbeats collects statics and metrics. I expect to information such as bytes used, the location of Web traffic, and number of unique visitors. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? install-elk.yml Where do you copy it? /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? Ansible.cfg How do I specify which machine to install the ELK server on versus which to install Filebeat on? Change the IP addresses of the hosts to match the private IP of the Elk servers. 
- _Which URL do you navigate to in order to check that the ELK server is running? 23.100.65.192 (Static IP of Web VM)

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ 
- sudo apt update
- sudo apt install docker.io
- sudo systemctl status docker
- sudo docker pull cyberxsecurity/ansible
- sudo docker run -ti cyberxsecurity/ansible: latest bash