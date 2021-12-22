# super-umbrella
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram2](https://user-images.githubusercontent.com/90219947/147009106-6aec4e22-bd78-4c2c-83f6-b24c0179f049.PNG)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

Ansible/install-elk.yml.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load Balancers protect the Availability of network security. They do this by ensuring that network traffic will continue to flow even if one of the servers goes down. The advantage of a jumpbox is that it has only one path in which is through SSH.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logs and system metrics.
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

![DockerPS](https://user-images.githubusercontent.com/90219947/147019978-4501e9af-07e6-43a9-932b-c13756f62f5b.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeats collects and monitors the log files on the Virtual Machines. Metricbeats collects metrics and statistics from the Virtual Machines. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible file to /etc/ansible.
- Update the hosts file to include the IP of the webservers.
- Run the playbook, and navigate to http://20.127.143.116:5601/app/kibana#/home to check that the installation worked as expected.




To make the playbook, we used the command nano filebeat-playbook.yml and edited it to do the follwing:
- Download filebeat .deb file
- Install filebeat .deb
- Drop in /etc/filebeat/filebeat.yml
- Enable and Configure System Module
- Setup filebeat
- Start filebeat service
- Enable service filebeat on boot

We then ran the playbook using the command: ansible-playbook filebeat.yml

To make the metricbeat playbook, we used the command nano metricbeat-playbook.yml and edited it to do the following:
- Install metricbeat
- Dropped in /etc/metricbeat/metricbeat.yml
- Enable and configure docker module for metric beat
- Setup metric beat
- Start metric beat
- Enable service metricbeat on boot

We then ran the playbook using the command: ansible-playbook metricbeat.yml

We then navigated to http://[your.VM.IP]:5601/app/kibana and this was the result:

![kibana1](https://user-images.githubusercontent.com/90219947/147156212-a217867e-7372-40f9-944d-e6a099c915bf.PNG)

