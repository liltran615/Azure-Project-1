# Azure-Project-1
Vanderbilt
:technologist:
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/Azure%20Lab%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

[ansible.yml](ansible.yml.TXT)
:orange_book:

[ansibleinstall-elk.yml.TXT](ansibleinstall-elk.yml.TXT)
:blue_book:

[metricbeat-playbook.TXT](metricbeat-playbook.TXT)
:closed_book:

[filebeat-playbook.yml.TXT](filebeat-playbook.yml.TXT)
:green_book:

This document contains the following details:
Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures the application will be highly available, in addition to restricting access to the network.

Load balancer performs the following functions:

1) Distributes client requests or network load across multiple servers.
2) Sends requests to online servers.
3) Provides flexibility to add or delete servers.

Integrating an ELK server allows users to monitor the Virtual Machines for changes to the files, logs and system metrics.

Filebeat collects data about the file system, and this is sent to Elasticsearch on ELK Server.

Metricbeat Collects metrics to help with the assessment regarding the operational state of computer machines on the network, and then sends it to Elasticsearch on ELK Server. 

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux UBUNTU 18.4           |
| WEB1     | DVWA     | 10.0.0.5   | Linux UBUNTU 18.4|
| WEB2     | DVWA     | 10.0.0.7   | Linux UBUNTU 18.4|
| ELKVM    | ELK Stack| 10.2.0.4   | Linux UBUNTU 18.4|

### Access Policies

Only the JUMP-BOX-PROVISOR machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Workstation with PERSONAL IP Address through SSH Port 22.

Machines within the network can only be accessed by JUMP-BOX.

Which machine did you allow to access your ELK VM?

JUMP-BOX-PROVISOR :desktop_computer: :earth_americas:

What was its IP address?

IP : 10.0.0.1

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | SSH via Admin's IP   |
| WEB1     | No                  | 10.0.0.5             |
| WEB2     | No                  | 10.0.0.7             |
| ELK      | No                  | 10.2.0.4             |

### Elk Configuration

Ansible was used to make configuration on the ELK machine. No configuration was performed manually which will decrease the chances of mistakes.

[ansible.yml](ansible.yml.TXT)

[ansibleinstall-elk.yml.TXT](ansibleinstall-elk.yml.TXT)

It makes the process of configuring and updating machines to the network easier. We will only have to make changes to the ansible playbook, and it will automatically be changed to all the machines linked with the playbook.

The playbook implements the following tasks: :books:

Install Docker, which intern facilitates instalation of containers
Install Python-pip
Install Docker Python Module
Increases Virtual Memory
Downloads and launches a docker ELK container with the ports 5601, 9200, 5044


![Docker PS](Pictures/sudo%20docker%20ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web-1: 10.0.0.5 :computer: :globe_with_meridians:

Web-2: 10.0.0.7 :computer: :globe_with_meridians:

We have installed the following Beats on these machines:

Filebeat [filebeat-playbook.yml.TXT](filebeat-playbook.yml.TXT)

![](Pictures/file%20beat%20status.png)

Metricbeat [metricbeat-playbook.TXT](metricbeat-playbook.TXT)

![](Pictures/metric%20beat%20status.png)


This allows us to collect the following information:

Filebeat to be used to collect log files from applications like Microsft Azure Tools, Apache,  and MySQL databases.

Metericbeat to be used to monitor CPU core statistics, VM statistics file system statistics,network statistics, memory statistics, etc

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node configured. 

SSH into the control node, and follow the steps:

STEP 1) Copy the configuration file to the ansible container.

STEP 2) Update the configuration file to include hosts: Ip address of the ELK server ["10.2.0.4"]

STEP 3) Run the playbook, and navigate to http://(vm ip):5601/app/kibana to check that the installation worked as expected.

