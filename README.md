## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - Ansible-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly protected, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?
  Load Balancers distribute network and or application traffic across several servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.
- What does Filebeat watch for?
  Filebeat watches and collects the data for audit logs, deprecation logs, gc logs and server logs.
- What does Metricbeat record?
  Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache.
  

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK VM   | Container| 10.2.0.4   | Linux            |
| Web-1    | Webserver| 10.0.0.7   | Linux            |
| Web-2    | Webserver| 10.0.0.9   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- ELK VM 10.2.0.4 
- Web-1 10.0.0.7 
- Web-2 10.0.0.9 

Machines within the network can only be accessed by Jump-box-Provisioner.
- Which machine did you allow to access your ELK VM? What was its IP address?_
- Jump-Box-Provisioner 10.0.0.1
- Web-1 10.0.0.7
- Web-2 10.0.0.9 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Workstaion IP        |
| Web-1    | No                  | 10.0.0.1             |
| Web-2    | No                  | 10.0.0.1             |
| ELK      | Yes                 | Workstaion IP        |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
- Ansible automation helps considerably with the representation of Infrastructure as Code. IAC involves provisioning and management of computing infrastructure and related configuration through machine-processable definition files.

The playbook implements the following tasks:
- Install docker.io
- Install Python3-pip3
- Install docker module
- Download and launch a docker web container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring
- Web-1 10.0.0.7
- Web-2 10.0.0.9
- ELK   10.2.0.4 

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed?
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the system file and Metricbeat collects machine metrics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible host file to the etc/ansible.
- Update the hosts file to include IP addresses of your webservers and ELK server.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- Which file is the playbook? Where do you copy it?
- The metricbeat and filebeat are the files that were copy to the ELK server.

- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- You would have to update the filebeat/metricbeat-config.yml file to run the playbooks on specific machines. To specify which machine to install the ELK server on, you would have to configure the filebeat/metricbeat-playbook.yml.

- Which URL do you navigate to in order to check that the ELK server is running?
- http://[ELK-VM-External-IP]:5601/app/kibana
