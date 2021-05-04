 ## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `diagram_filename.png` with the name of your diagram image file.  

![alt text] https://github.com/stellak28/Cloud-Network/blob/main/Diagrams/Network_Diagram.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and config file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/stellak28/Cloud-Network/blob/main/Ansible/Elk-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- _What aspect of security do load balancers protect? Web Traffic, Availability, Web security 
- What is the advantage of a jump box? An advantage of a jumpbox is that it is  gateway which has the control to access certain services 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- What does Filebeat watch for? Forwarding and centralizing logs 
- What does Metricbeat record? It takes the metric and statistics that it collects and ships them out to the output that you specify such as Elasticsearch

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |Webserver | 10.0.0.5   | Linux            |
| Web-2    |Webserver | 10.0.0.6   | Linux            |
| Web-3    |Webserver | 10.0.0.8   | Linux            |
|Elk-server|Webserver | 10.1.0.4   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Workstation public IP to TCP 5601

Machines within the network can only be accessed by Jumpbox Provisioner.
- Which machine did you allow to access your ELK VM? What was its IP address?
  Jumpbox Provisioner IP: 10.0.0.4 SSH port 22 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Public IP Port 22    |
| Web-1    | No                  | 10.0.0.4 on SSH 22   |
| Web-2    | No                  | 10.0.0.4 on SSH 22   |
| Web-3    | No                  | 10.0.0.4 on SSH 22   |
|Elk-server| No                  | Workstation Public IP| 
|          |                     |   using TCP 5601     |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
The main advantage of automating configuration with Ansible is that you can automate systems by listing the tasks in the playbook and it will run the applications in any state as you wanted it to be. 
The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

- Specify a different group of machines as well as a different remote user
  - name: Config elk VM with Docker
    hosts: elk
    remote_user: sysadmin
    become: true
    tasks:
Increase System Memory :
 - name: Use more memory
  sysctl:
    name: vm.max_map_count
    value: '262144'
    state: present
    reload: yes
Install the following services:
   `docker.io`
   `python3-pip`
   `docker`, which is the Docker Python pip module.
Launching and Exposing the container with these published ports:
 `5601:5601` 
 `9200:9200`
 `5044:5044`
- 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  




### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
