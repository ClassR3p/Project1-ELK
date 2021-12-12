## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Elk Project drawio](https://user-images.githubusercontent.com/24533867/145702943-d7ca77e4-8675-49e8-b57e-7dffcd92b8c6.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- /etc/ansible/install-elk-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- Load Balancers protect your server from DDoS attacks and diverts traffic away.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat watches for any new changes in the file system and when it was changed.It also logs events and watches if anything changes among the logs over a period of time
- Metricbeat looks at the metrics and statistics to collect and ship the output to a specific spot.It then records the metrics and statistics from your operating system and sericves on your server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |10.0.0.4    |Linux(ubtntu 18.04)|
|ELK-Machine1|Server  |10.0.0.5    |Linux(ubtntu 1804) |
|ELK-Machine2|Server  |10.2.0.4    |Linux(ubtntu 18.04)|
|ELK-Machine3|Server  | 10.2.0.5   |Linux(ubtntu 18.04)|
|ELK-Server |Elk Server|10.1.0.4|Linux(ubtntu 18.04)|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-  172.24.32.1 is the only IP adress I whitelisted 

Machines within the network can only be accessed by _____.
- Jump-Box-Provisioner can be accessed through the private IP:10.0.0.4  

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
|Jump Box    | no                    |10.0.0.4     |
|ELK-Machine1|no                     |10.0.0.5     |
|ELK-Machine2|no                     |10.2.0.4     |
|ELK-Machine3|no                     |10.2.0.4     |
|ELK-Server  |no                     |10.1.0.4     |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible tattoos allows the user to deploy to multiple servers using playbook

The playbook implements the following tasks:
- Install docker.io
- Install Python-pip
- Install docker container
- Launch docker container: elk
- Command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![Docker_ps](https://user-images.githubusercontent.com/24533867/145702955-c7a7b1f6-f088-414a-a4ac-50566656da43.JPG)


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- |ELK-Machine1|10.0.0.5     |
- |ELK-Machine2|10.2.0.4     |
- |ELK-Machine3|10.2.0.4     |

We have installed the following Beats on these machines:
- Filebeat 
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors your the placement and changes log files.It then collects these log events and forwards them to Elasticsearch or Logstash
- Metricbeat collects metrics from your computer specifically your OS and services that you ran within the server
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
- 

SSH into the control node and follow the steps below:
- Copy the Playbook file to /etc/ansible.
- Check and update configuration file to include the VMs
- Run the playbook, and navigate to ELK server to check that the installation was sucessful

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
/etc/ansible/host
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
-Servers > [10.0.0.5] ansible_python_interpreter=/usr/bin/python3 [10.2.0.4] ansible_python_interpreter=/usr/bin/python3 [10.2.0.5] ansible_python_interpreter=/usr/bin/python3
-Elk > 10.1.0.4 ansible_python_interpreter=/usr/bin/python3
-run playbook
-ssh in ELK server
-sudo docker ps
-installing_elk.yml Location: /etc/ansible/installing_elk.yml
-Go to http://[52.225.74.201]:5601/app/kibana to confirm 

![elkproject_kibana_screenshot](https://user-images.githubusercontent.com/24533867/145702967-17a4d11f-dabe-4ab5-8718-cf496371dc9b.png)

- _Which URL do you navigate to in order to check that the ELK server is running?
put:
- ssh catman@20.120.0.25
- sudo docker container list -a 
check and locate contianer 
- sudo docker start container 
- sudo docker attach container 
