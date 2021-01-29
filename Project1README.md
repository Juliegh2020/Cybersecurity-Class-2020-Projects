# Cybersecurity-Class-2020-Projects## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

C:\Users\brook\Documents\Cybersecurity-Class-2020-Projects\Project 1\Network diagrams

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

C:\Users\brook\Documents\Cybersecurity-Class-2020-Projects\Project 1\Ansible YAML scripts

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting traffic to the network.
- _What aspect of security do load balancers protect? Load balancers protect the application by distributing network traffic over multiple servers to counteract a denial of service attack. A health probe monitors the health of each server, and if one of the machines becomes compromised, the load balancer can redirect traffic away from that machine. What is the advantage of a jump box? When a jump box is enabled, we have only one virtual machine with connectivity to the internet. We can connect all the other virtual machines to that single jump box. This prevents exposure of all virtual machines to the internet.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- _What does Filebeat watch for? Filebeat collects data about the file system
- _What does Metricbeat record? Metricbeat collects metrics about the machine (eg, uptime).

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
| Name                 | Function        | IP Address | Operating System |
|----------------------|-----------------|------------|------------------|
| Jump-Box-Provisioner | Gateway         | 10.0.0.9   | Linux            |
| Web-1                | Virtual machine | 10.0.0.10  | Linux            |
| Web-2                | Virtual Machine | 10.0.0.11  | Linux            |
| Web-3                | Virtual Machine | 10.0.0.13  | Linux            |
| Web-4E               | ELK server      | 10.1.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _75.132.35.236/32

Machines within the network can only be accessed by Jump Box.
- _Which machine did you allow to access your ELK VM? Jump Box 
What was its IP address? 52.255.133.243

A summary of the access policies in place can be found in the table below.
| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | 75.132.35.236/32     |
| Web-1                | No                  | Only from jump box   |
| Web-2                | No                  | Only from jump box   |
| Web-3                | No                  | Only from jump box   |
| Web-4E               | Yes                 | 75.132.35.236/32     |
                     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _What is the main advantage of automating configuration with Ansible? The main advantage of automating configuration with Ansible is consistency and re-use. Once the Ansible playbook is set up properly, the machine can be replicated over and over with the same configuration without human error.

The playbook implements the following tasks:
Installs the following apt packages: docker.io (Docker engine)and python3-pip (installs Python software)
Installs the pip package: docker (Python client)
Configures the Elk machine to use more memory.
Downloads and launches a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

C:\Users\brook\Documents\Cybersecurity-Class-2020-Projects\Project 1\Screenshots

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.10
- 10.0.0.11
- 10.0.0.13

We have installed the following Beats on these machines:
- _Filebeats

These Beats allow us to collect the following information from each machine:

Filebeat is used to collect log events. For example, Filebeats allows us to monitor SSH login attempts and successful and failed ssh logins. Metricbeat collects metrics from the operating system and any services running on the server (eg, Apache). 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat configuration file to the WebVMps where you just installed Filebeat.
- Update the filebeat-config.yml file to include the username/password, replace the IP address with the IP address of the ELK machine for booth output.elasticsearch and setup.kibana.
- Run the playbook, and navigate to the Filebeat Installation page to check that the installation worked as expected.

C:\Users\brook\Documents\Cybersecurity-Class-2020-Projects\Project 1\Screenshots

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Filebeat-playbook.yml. Where do you copy it? Onto the the Web VMs.
- _Which file do you update to make Ansible run the playbook on a specific machine? Filebeat-config.yml How do I specify which machine to install the ELK server on versus which to install Filebeat on? You use the /etc/ansible/hosts file to determine that.
- _Which URL do you navigate to in order to check that the ELK server is running? (http://<ELK.VM.External.IP>:5601/app/kibana. 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._



