## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/UcheOny/Unit12-Homework/blob/main/Network%20Diagram%20HW.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and config file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Dmn Vulnerable Web Application.

Load balancing ensures that the application will be highly versatile, in addition to restricting high traffic to the network.

Load balancers are advantageous when a D-DoS attack occurs, or when there is a high volume of traffic that another server can compensate or alleviate. By integrating an ELK server, users may simply monitor vulnerable virtual machines (VMs) for changes to their data system logs.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.

Filebeat monitors and observes the log files or locations specified by the user, gathers log events, and indexes them to Elasticsearch or Logstash. 
Metricbeat Retrieve metrics from your systems and services. It is a lightweight approach to provide system and service information. From CPU to RAM, Redis to NGINX, and so forth.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | DVWA     | 10.0.0.5   | Linux            |
| Web-2    | DVWA     | 10.0.0.6   | Linux            |
| El-VM    | Server   | 10.1.0.4   | Linux (Kibana)   |           


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK Server machine, (ELK -vm) can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
:{20.213.160.17} Machines within the network can only be accessed by Jump-Box-Provisioner.
My local host machine is allowed to acess Jump-Box-Provisioner -Jump-Box-Provisioner has access to my Elk-VM.
{20.213.160.17} is my jumpbox ip, {70.215.73.19} is my localhost ip, {13.75.228.14} is my Elk-VM ip. [ALL OF THESE IPS ARE THE PUBLIC IP'S] A summary of the access policies in place can be found in the table below.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |  20.213.160.17       |
|Elk Server| Yes                 |  13.75.228.14        |
| Web-1    | No                  |  20.211.16.37        |            
| Web-2	   | No				           |  20.211.16.37        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The benefit of using Ansible to automate configuration is that it boosts efficiency while configuring several computers.

The playbook implements the following tasks:
⦁	Install Docker.io -Install Docker module
⦁	Increase Virtual Memory
⦁	Download and launch elk container
⦁	Enable elk ports
⦁	Download and launches the sebp/elk container over ports 5601, 9200, and 5044.
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:
Metricbeat and Filebeat

These Beats allow us to collect the following information from each machine:
- _Filebeat gathers log events and indexes them using Elasticsearch or Logstash. 
Metricbeat monitors the operating system and system services for system metrics. Using the Playbook.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
⦁	Copy the my-playbook.yml file to playbook.
⦁	Update the _my-playbook.yml file to include host: webservers.
⦁	the playbook and navigate to curl localhost/setup.php to check that the installation worked as expected.

Which file is the playbook? Where do you copy it? /etc/ansible folder Which file do you update to make Ansible run the playbook on a specific machine? Update the [ansible-config]. How do I specify which machine to install the ELK server on versus which to install Filebeat on? update the hostname in the hosts file and then update the [ansible-config] file and then save. _Which URL do you navigate to check that the ELK server is running? http://[13.75.228.14]:5601

