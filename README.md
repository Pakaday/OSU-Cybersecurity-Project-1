## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Diagrams/FPN_Proj1.drawio.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

[filebeat-playbook.yml](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/filebeat-playbook.yml)

[install-elk.yml](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/install-elk.yml)

[metricbeat-playbook.yml](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
- What aspect of security do load balancers protect?
  - Load balancers increase availability by distributing traffic across multiple servers, thus helping to prevent DDoS (Distributed Denial of Service) attacks.
- What is the advantage of a jump box?
  - An advantage of a jump box is that it is a secure computer that admins must connect to first before running administrative tasks or before connecting to other servers or unsecured environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system applications.
- What does Filebeat watch for?
  - Filebeat is used to monitor log files/locations you specify, collects log events and forwards them to Elasticsearch or Logstash for indexing.
- What does Metricbeat record?
  - Metricbeat is used to record metrics and statistics and forward what it collects to the output you specify.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

|         Name        | Function   |                IP Address               | Operating System |
|---------------------|------------|-----------------------------------------|------------------|
| Jumpbox-Provisioner | Gateway    | Private: 10.0.0.4 Public: 40.117.63.114 | Linux            |
| Web-1               | Webserver  | Private: 10.0.0.5                       | Linux            |
| Web-2               | Webserver  | Private: 10.0.0.6                       | Linux            |
| Elk-VM              | Monitoring | Private: 10.1.0.4                       | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox-Provisioner can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 74.140.4.189

Machines within the network can only be accessed by Jumpbox-Provisioner.

-Which machine did you allow to access your ELK VM? 

-The Jumpbox-Provisioner with an IP of 10.0.0.4.

A summary of the access policies in place can be found in the table below.

|        Name         | Publicly Accessible | Allowed IP Addresses |
|---------------------|---------------------|----------------------|
| Jumpbox-Provisioner | Yes                 | 74.140.4.189         |
| Web-1               | No                  | 10.0.0.5             |
| Web-2               | No                  | 10.0.0.6             |
| Elk-VM              | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
- The main advantage would be to automate and streamline multiple processes into one Ansible playbook rather than inputting the configurations manually into each configuration file.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
- Install docker.io
- Install pip3
- Install Docker python module
- Increased the available virtual memory
- Download and launch a docker container running an Elk instance

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/2ef7ea779dd5b4fc6fab245f4d8555ac9eb18aa9/Images/Elk761%20(2).png)



### Target Machines & Beats
This ELK server is configured to monitor the following machines:

|  Name  | IP Addresses |
|--------|--------------|
| Web-1  | 10.0.0.5     |
| Web-2  | 10.0.0.6     |
| Elk-VM | 10.1.0.4     |

We have installed the following Beats on these machines:
- We have installed Filebeats and Metricbeats on these machines.

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
  - Filebeat is used to collect log files from specific locations on remote machines.
   - These can be logs from Apache webserver and show SSH login attempts and sudo use in the system.
  - Metricbeat is used to collect metrics and system usage data on remote machines.
   - These can be CPU and memory usage.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- In the Ansible container, use the following command: cd /etc/ansible/
- In the /etc/ansible/ directory, use the following command: mkdir files roles
  - This command will create the files and the roles directory.
- Copy the [filebeat-playbook.yml](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/filebeat-playbook.yml) file to /etc/ansible/roles/roles. Using a text editor, paste the copied playbook into a new file named filebeat-playbook.yml. (nano filebeat-playbook.yml)
- Copy the [metricbeat-playbook.yml](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/metricbeat-playbook.yml) file to /etc/ansible/roles/roles. Using a text editor, paste the copied playbook into a new file named metricplaybook-yml. (nano metricbeat-playbook.yml)
- Update the [hosts](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Linux/hosts.txt) file to include elk and webservers.
  - Use your virtual machine private IP addresses and add the python interpreter.
- Edit and update [hosts](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Linux/hosts.txt) file with IP addresses of your specified virtual machines, with webservers as one group and the elk server as its' own group.
  - This is an example of what we are looking for:

<p>[webservers]<br>
10.0.0.5 ansible_python_interpreter=/usr/bin/python3<br>
10.0.0.6 ansible_python_interpreter=/usr/bin/python3<p>


<p>[elk]<br>
10.1.0.4 ansible_python_interpreter=/usr/bin/python3<p>

- Run the playbook, and navigate to the public IP address of your Elk server virtual machine "YOUR_IP:5601/app/kibana" to check that the installation worked as expected, which is 20.110.189.53:5601/app/kibana for my Elk server.
  - To run the playbook, use the following command:
  - ansible-playbook filebeat-playbook.yml (This will run and install the filebeat-playbook we created)
  - ansible-playbook metricbeat-playbook.yml (This will run and install the metricbeat-playbook we created)
