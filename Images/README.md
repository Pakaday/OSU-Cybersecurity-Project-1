A series of screenshots with descriptions on installing and verifying that installs are successful and what to look for.

- Curl command to download the [filebeat-config](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Linux/filebeat-config.yml.txt)
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/FileBeat_Download.png)

- Use mkdir files and mkdir roles inside of /etc/ansible/, then ls to verify folders are created.
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Ansible_Folders.png)

- After creating the previous two folders, move [filebeat-config](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Linux/filebeat-config.yml.txt) and [metricbeat-config](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Linux/metricbeat-config.txt) into the files folder. Then, move [filebeat-playbook](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/filebeat-playbook.yml) and [metricbeat-playbook](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/metricbeat-playbook.yml) into the roles folder.
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Ansible_Folders_Confirm.png)

- Modify the IP addresses in the [filebeat-config](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Linux/filebeat-config.yml.txt) to the IP of Elk server virtual machine for the Elasticsearch output and Kibana setup.
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Filebeat_IP_Config.png) ![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Filebeat_IP_Config_2.png)

- Modify the [filebeat-playbook](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/filebeat-playbook.yml)
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Filebeat_Playbook.png)

- Use ansible-playbook filebeat-playbook.yml to run the configured playbook.
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Filebeat_Run.png)

- Verify Kibana has received the system data and the system log dashboard is showing captured data.
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Kibanasys.png) ![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Kibanasys1.png)

- Modify the [metricbeat-playbook](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Ansible/metricbeat-playbook.yml)
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Metricbeat_Playbook.png)

-Use ansible-playbook metricbeat-playbook.yml to run the configured playbook.
![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Metricbeat_Run.png)

- Verify Kibana has received the metric data and the metric data dashboard is showing captured metrics.
- ![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Kibanametric.png) ![image](https://github.com/Pakaday/OSU-Cybersecurity-Project-1/blob/main/Images/Kibanametric1.png)
