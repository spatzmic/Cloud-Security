## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](Diagrams/NetworkDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [filebeat.yml](https://github.com/spatzmic/Cloud-Security/blob/master/filebeat.yml) file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **redundant**, in addition to restricting **unauthorized access** to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **filelogs, event logs** and **system metrics**.

The configuration details of each machine may be found below.


| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | ubuntu severs    |
| DVWA1    | Webserver | 10.0.0.6   | ubuntu servers   |
| DVWA2    | Webserver | 10.0.0.7   | ubuntu servers   |
| DVWA3    | Webserver | 10.0.0.8   | ubuntu servers   |
| DVWA4    | Webserver | 10.0.0.9   | ubuntu serves    |
| ElkServer| Elkserver | 10.0.0.5   | ubuntu servers   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the **Jumpbox** machine can accept connections from the Internet.  Access to this machine is only allowed from the following IP addresses: **99.240.221.*** ** 

Machines within the network can only be accessed by the **Jumpbox 10.0.0.4**

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|---------------------|
| Jump Box  |    no               | 99.240.221.***      |
|  DVWA1    |    no               | 10.0.0.6            |
|  DVWA2    |    no               | 10.0.0.7            |
|  DVWA3    |    no               | 10.0.0.8            |
|  DVWA4    |    no               | 10.0.0.9            |
| Elkserver |    no               | 10.0.0.5            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is **less time consumin, less repetitive, and eliminates human error**

The playbook implements the following tasks:

-Install the docker
-Install Python 
-Increase virtual memory of VM server
-Download and install docker sepb/elk


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps](Ansible_Images/DockerPS.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines: **10.0.0.6, 10.0.0.7, 10.0.0.8, 10.0.0.9**

We have installed the following Beats on these machines: **Filebeat, Metricbeat**

These Beats allow us to collect the following information from each machine: **Filebeat collects log files, event logs.  Metricbeat collects system metrics such as uptime.**

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the [ansible.cfg](https://github.com/spatzmic/Cloud-Security/blob/master/ansible.cfg) file to **/etc/ansible**.
- Update the **ansible.cfg** file to include the remote user and update the host file to include the webserver and elkserver.
- Run the playbook, and navigate to **40.117.126.185:5601** to check that the installation worked as expected.

Download playbook: 
[elk1.yml](https://github.com/spatzmic/Cloud-Security/blob/master/elk1.yml)
