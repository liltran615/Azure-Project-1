# Azure-Project-1
Vanderbilt
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram] (https://github.com/liltran615/Azure-Project-1/blob/main/Diagrams/Azure%20Lab%20Diagram.png]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

TODO: Enter the playbook file.
This document contains the following details:
Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Load balancing is the process of distributing incoming reequests/tasks over a set of resources in order to prevent disproportionate skew of requests load towards one specific server. For example, this can be particularly useful in maintaining availability of services to customers in the setting of a DoS attack on one of the server, rendering it unavailable. If the same services are available on an alternate server, the load balancer can distribute the web traffic to the alternate server when the primary server is 'overloaded' - this way the services (such as sales) continue to remain operational even in the mist of the attack. In addition it can also be configured to limit access to particular servers to prevent penetration by hackers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files, logs and system metrics.

Filebeat collects data about the file system. It is helpful in detecting changes to certain important files stampd by time like for example if a hacker attemps to change etc/passwd and this information is then sent to Elasticsearch on the ELK Server

Metricbeat Collects metrics to help with the assessment regarding the operational state of computer machines on the network (VMs in this case) and then sends it to Elasticsearch on ELK Server. For example it can be helpful in determining CPU usage, memory disk I/O, Network I/O and Uptime information.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux UBUNTU 18.4           |
| WEB1     | DVWA     | 10.0.0.5   | Linux UBUNTU 18.4|
| WEB2     | DVWA     | 10.0.0.7   | Linux UBUNTU 18.4|
| ELKVM    | ELK Stack| 10.2.0.4   | Linux UBUNTU 18.4|

### Access Policies

Only the Jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Workstation with personal ip through SSH P22

Machines within the network can only be accessed by Jump-box.

Which machine did you allow to access your ELK VM?
Jump-Box

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

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

It simplifies the process of configuring additional machines or updating changes to all existing ones to the network simultaneously. We will only have to make changes to the ansible playbook and it will automatically be implemented to all the machines linked with the playbook.

The playbook implements the following tasks:

Installs Docker, which intern facilitates instalation of containers
Installs Python-pip
Installs Docker python module
Increases virtual memory
Downloads and launches a docker ELK container with the ports 5601, 9200, 5044

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web-1: 10.0.0.5
Web-2: 10.0.0.7

We have installed the following Beats on these machines:

filebeat
metricbeat
These Beats allow us to collect the following information from each machine:

Filebeat will be used to collect log files from very specific files such as Apache, Microsft Azure tools and web servers, MySQL databases.
Metericbeat will be used to monitor VM stats, per CPU core stats, per filesystem stats, memory stats and network stats.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
Copy the configuration file to the ansible container.
Update the configuration file to include hosts: Ip address of the ELK server ["10.2.0.4"]
Run the playbook, and navigate to http://(vm ip):5601/app/kibana to check that the installation worked as expected.

