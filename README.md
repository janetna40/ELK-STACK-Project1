# ELK-STACK-Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project1_Diagram_1 drawio](https://user-images.githubusercontent.com/85567847/133757383-390f1a84-1f1b-4671-a770-6ddf4c65e2d2.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible files to follow; may be used to install only certain pieces of it, such as Filebeat.

https://github.com/janetna40/ELK-STACK-Project1/blob/7b8c4dc0a3105edbf6f7d7d56e9b8f7a93d378fe/Ansible/filebeat-playbook.yml (Installs and configures Filebeat on the target machines)

https://github.com/janetna40/ELK-STACK-Project1/blob/7b8c4dc0a3105edbf6f7d7d56e9b8f7a93d378fe/Ansible/metricbeat-playbook.yml (Installs and configures Metricbeat on the target machines)

https://github.com/janetna40/ELK-STACK-Project1/blob/7b8c4dc0a3105edbf6f7d7d56e9b8f7a93d378fe/Ansible/install-elk-playbook.yml (Installs and configures the ELK Server)


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
 - One of the main advatages is that it helps prevent human error with no manual configuratiobn done and allowing automation configuration of the machine.  

