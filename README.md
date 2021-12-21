# super-umbrella
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![diagram](https://user-images.githubusercontent.com/90219947/146972980-3e571009-211b-47ae-979f-b6164f60d0e2.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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
- Load Balancers protect the Availability of network security. They do this by ensuring that network traffic will continue to flow even if one of the servers goes down. The advantage of a jumpbox is that it has only one path in which is through SSH.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Filebeat monitors log files or specified locations, makes a collection of log events and send the data to the specified output.
- Metricbeats records statistics and preformance on your server. This information is also sent to a specified output.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1     |   VM       |     10.0.0.5       |          Linux        |
| Web-2    |     VM     |   10.0.0.6         |           Linux       |
|  Web-3    |    VM      |       10.0.0.7     |          Linux        |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My public IP address.

Machines within the network can only be accessed by The Jump-Box VM.
- The machine that I allowed access to the ELK VM was the Jump-Box 20.118.202.229.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |        No              |20.118.202.236  |
|   Web-1        |       No              | 20.118.202.229                     |
|      Web-2                 | No|20.118.202.229
Web-3|            No         |     20.118.202.229                 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage of automating configuration with Ansible is that it makes tasks that have to be repeated less vulnurable to any errors. The main advantage of automating the ELK machine with Ansible is also the fact that it minimizes the chance of human error.

The playbook implements the following tasks:
- Install Docker
- Install Python
- Install Docker Module
- Increase virtual memory
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- Filebeat
MetricBeat

These Beats allow us to collect the following information from each machine:
- Filebeats collects and monitors the log files on the Virtual Machines. Metricbeats collects metrics and statistics from the Virtual Machines. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to http://20.127.143.116:5601/app/kibana#/home to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
