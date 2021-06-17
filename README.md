# ELK-stack-Project-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](/Diagrams/Project1.jpg)

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

Load balancing ensures that the application will be highly Reliable and available, in addition to restricting Traffics to the network.
- the aspect of security do load balancers protect? What is the advantage of a jump box?_
Load Blancers protecs the system from DDoS Atacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the operating system and system Services.
- Filebeat monitors the log files or locations that you specify.
- Metricbeat records the metrics and statistics from the operation system and from services running on the server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.5.0.4   | Linux            |
| WEB 1    |Webserver1| 10.5.0.5   | Ubuntu           |
| WEB-2    |Webserver2| 10.6.0.4   | Ubuntu           |
| WEB-3    |webserver3| 10.5.0.6   | Ubuntu

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-   40.122.123.56

Machines within the network can only be accessed by the Jump Box virtual machine.
- The Jumpbox to access your ELK VM. The IP adress fo the jumpbox is 10.0.0.1

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.1             |
| WEB-1    | No                  | 10.5.0.5             |
| WEB-2    | NO                  | 10.6.0.4             |
| WEB-3    | No                  | 10.5.0.6
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible allows IT administrators to automate their daily tasks and save a lot of time. That frees them to focus on efforts that help deliver more value to the business by spending time on more important tasks.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Install python3-pip
- Install Docker python module
- Set the vm_max_count to 262144
- Download and launch a docker elk container
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats ###
This ELK server is configured to monitor the following machines:
- WEB-1 10.5.0.5
- WEB-2 10.6.0.4
- WEB-3 10.5.0.6

We have installed the following Beats on these machines:
- FILEBEAT
- METRICBEAT

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the lof ilde oe location that specify, which we use to see what changes or messages the lot file have recived such as kill command. MetricBeat recoords the metrics and statistics form the operation and statstics from the operating system and from the services running on.

### Using the Playbook ###
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to /etc/ansible
- Update the ansible file to include...
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? ansible.cfg
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your.VM.IP]:5601/app/kibana 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- Commands to Use the Playbook

    nano ansible.cfg
    add the machine, its IP, and ansible_python_interpreter=/usr/bin/python3 to the hosts
    Ctrl + x to exit file
    in the folder that install-elk.yml is in, run: cp install-elk.yml /etc/ansible
    nano install-elk.yml /etc/ansible

    name: installing elk hosts: [your_machine]
    Ctrl + x to exit file
    ansible-playbook install-elk.yml

    name: installing elk hosts: [your_machine]
    Ctrl + x to exit file
    ansible-playbook install-elk.yml