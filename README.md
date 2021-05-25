## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Homework_13\Diagrams\Azure Diagram.JPG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Filebeat_yaml.jpg file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies	
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Redundant, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system servers.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Container| 10.0.0.5   | Linux            |
| Web-2    | Container| 10.0.0.8   | Linux            |
| ELK      | Logging  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 98.40.225.115


Machines within the network can only be accessed by 98.40.225.115.
 
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 98.40.225.115        |
| Web-1/2  | No                  | 10.0.0.4             |
| ELK      | Yes                 | 98.40.225.115        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because changes are easy to track and deploy to multiple devices.

The playbook implements the following tasks:
- Install Docker and Docker components
- Install Python
- Increase virtual memory
- Increase memory usage
- Download and launch ELK container

The following screenshot displays the result of running `sudo docker ps` after successfully configuring the ELK instance.

Homework_13\Ansible\Docker_ps

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.8

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat and metricbeat work in tandem to collect the metrics, statistics, and logs from our machines. They also take that information and send it to our ELK server.

 ### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ELK.yml file to roles.
- Update the hosts file to include the Elk server host and corresponding ip
- Run the playbook and navigate to /etc/ansible/roles to check that the installation worked as expected.

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- The hosts file. Changing the host in the playbook

Which URL do you navigate to in order to check that the ELK server is running?
- http://52.167.134.196:5601/

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
- ansible-playbook ELK.yml
