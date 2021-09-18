# ELK-STACK-Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project1_Diagram_1 drawio](https://user-images.githubusercontent.com/85567847/133757383-390f1a84-1f1b-4671-a770-6ddf4c65e2d2.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible files to follow; may be used to install only certain pieces of it, such as Filebeat.

[Filebeat Playbook](https://github.com/janetna40/ELK-STACK-Project1/blob/0899bacb55d415564623d63b5ea4448d1daa149a/Ansible/filebeat-playbook.yml) 
	-Installs and configures Filebeat on the target machines

[Metricbeat Playbook](https://github.com/janetna40/ELK-STACK-Project1/blob/dc5c52593a5e4e115d204123d2a820f989fbcc7f/Ansible/metricbeat-playbook.yml) 
	-Installs and configures Metricbeat on the target machines

[Installing ELK Playbook](https://github.com/janetna40/ELK-STACK-Project1/blob/dc5c52593a5e4e115d204123d2a820f989fbcc7f/Ansible/install-elk-playbook.yml-elk-playbook.yml) 
	-Installs and configures the ELK Server


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly effective and efficient, in addition to restricting traffic to the network.
What aspect of security do load balancers protect? 
		- Load balancers help distribute traffic evenly across the servers and help mitigate DoS attacks.

What is the advantage of a jump box?
		- One advatage of a Jumpbox is that a user can focus on a few connections between a few machines, rather than connections between all machines. By having a single node gateway router, this forces all network traffic through a router that is secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logs and system metrics/data.

What does Filebeat watch for?
		-Filebeat forwards and centralizes log data. It also monitors log files, collects log events and forwards the information/data for indexing.
	
What does Metricbeat record?
		-Metricbeat collects metric data from the target servers such as CPU/memory data, 
	Inbound traffic data, and disk usage.

The configuration details of each machine may be found below.

| Name                 | Function         | IP Address | Operating system |
|----------------------|------------------|------------|------------------|
| Jump-Box-Provisioner | Gateway          | 10.0.0.4   | Linux (Ubuntu)   |
| Web-1                | Server           | 10.0.0.5   | Linux (Ubuntu)   |
| Web-2                | Server           | 10.0.0.6   | Linux (Ubuntu)   |
| VM-ELK               | ELK Stack Server | 10.1.0.4   | Linux (Ubuntu)   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Add whitelisted IP addresses: Public IP address: 40.76.94.121

Machines within the network can only be accessed by an SSH connection.

Which machine did you allow to access your ELK VM? What was its IP address?
The Jump-Box-Provisioner was allowed access to the ELK VM.
Public IP: 40.76.94.121
Private IP: 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessed | Allowed IP Addresses |
|----------------------|-------------------|----------------------|
| Jump-Box-Provisioner | Yes               | 10.0.0.4             |
| Web-1                | No                | 10.0.0.5             |
| Web-2                | No                | 10.0.0.6             |
| VM-ELK               | No                | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
 - One of the main advatages is that it helps prevent human error with no manual configuration done and allowing automation configuration of the machine.  

The playbook implements the following tasks:

Installing Filebeat
-Downloaded and installed Filebeat
-Edited and copied the filebeat configuration
-Setup file beat
-Started and enabled the Filebeat service 

Installing ELK
-Downloaded and launched the docker container for the ELK stack 
-Installed docker.io package using apt command 
-Installed the docker module using pip command 
-Installed python3-pip package manager using apt
-Configured the Virtual Machines to use more using the sysctl module

Installing Metricbeat 
-Setup Metricbeat
-Downloaded and installed Metricbear
-Edited and copied the Metricbeat configuration
-Emabled the Metricbeat docker module 
-Started and enabled the Metricbeat service


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<img width="1625" alt="Docker_ps_screenshot" src="https://user-images.githubusercontent.com/85567847/133864145-cb1bd722-8759-48a1-ac11-699beeb95198.png">


   
### Target Machines & Beats
This ELK server is configured to monitor the following machines:

| Web-1                 | 10.0.0.5             |
| Web-2                 | 10.0.0.6             |


We have installed the following Beats on these machines:
 Specify which Beats you successfully installed:
 -Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
--Filebeat forwards and centralizes log data. It also monitors log files, collects log events and forwards the information/data for indexing. -Metricbeat collects metric data from the target servers such as CPU/memory data, Inbound traffic data, and disk usage.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook files to the specific directory needed to run the playbooks. the directory is     /etc/ansible/roles.

- I update the host file to include the elkservers group along with the correspinding IP adresses. I also had to create a webservers group with the corresponding IP adresses of the target machines.

Example provided below below:

<img width="561" alt="Screen Shot 2021-09-17 at 6 36 33 PM" src="https://user-images.githubusercontent.com/85567847/133863952-ff2a1bbe-a55d-4f7a-aa5e-ba79805a1a8b.png">


- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
I used the IP address for the ELK-VM with port 5601/app/kibana in the web browser/ if its successful it should run and open up kibana as shown below

<img width="1552" alt="Screen Shot 2021-09-16 at 9 02 38 PM" src="https://user-images.githubusercontent.com/85567847/133864923-70da69e1-8506-4a0b-ac17-6064dddb78ea.png">


Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it?

Filebeat-playbook and copy I copied it to /etc/ansible/roles

Which file do you update to make Ansible run the playbook on a specific machine? 

Filebeat-config.yml

How do I specify which machine to install the ELK server on versus which to install Filebeat on?
To specify, the config files can manipulated to specify which machines (IP ADDRESSES) we want them to run

Which URL do you navigate to in order to check that the ELK server is running? 

IP address for the ELK-VM with port 5601/app/kibana Ex. IP ADDRESS FOR ELK SERVER:5601/app/kibana



Commands needed to run the Ansible Configuration for the ELK Server are:

| Commands              Explanation        

|----------------------|-------------------|

| SSH azjanetna@Jumpbox (Public IP) | connection from local machine to Jumpbox              
| sudo apt-get update               | updates all packages                         
| sudo apt install docker.io        | installs docker application                   
| sudo docker start (name)          | starts the docker application               
| sudo docker pull cyberxsecurity/ansible  |   downloads the docker

| ssh-keygen                   | creates a ssh key                               




