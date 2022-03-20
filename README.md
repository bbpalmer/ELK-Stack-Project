# ELK-Stack-Project - Columbia University Cybersecurity Boot camp
Bruce Palmer, MCSE  
**FineLine Security, LLC**  
March 5, 2022


## Objective
The goal of this project was to build an Azure-based cloud environment to maintain a secure, load-balanced and monitored intance of the Damn Vulnerable Web App (DVW). The web site, balanced across three virtual machines, each running Ubuntu 18.04, were provisioned identically with applications installed in Ansible containers within Docker.

Web site analytics were implemented using a dedicated ELK server (Elasticsearch, Logstash, Kibana) similarly provisioned within Ansible containers on top of Docker on a separate Ubuntu VM within a separate Azure Virtual network 

Security was established with network security groups (NSGs) associated with both virtual networks.  For administration purposes, SSH (port 22) connections were permitted from a remote administration computer, Mr. Palmer’s home computer, to each VM.  SSH connections to the VMs were restricted to being initiated from Mr. Palmers computer only.  Public connections to the web servers and ELK server were limited to HTTP (port 80) traffic only.  These rules ensured that DVWA was highly accessible from the public Internet but administraive access to the servers was restricted to connections from Mr. Palmer's computer only.

A "jump box" was utilized to facilitate access to the servers hosting Docker and the Ansible containers.  Access between the jump box and the servers was only permitted via ssh (port 22) using a dedicated SSH key pair.

It should be noted that the creation of separate virtual networks for the web servers and the ELK server was not a practical necessity.  Instead, the separate network was dictated by the vCPU limitation of the Azure test environment we employed.  To overcome this artificial limitation, the networks established mutual trust with an Azure peering relationship.  

## Azure Resources utilized:

### Virtual Networks
![image](https://user-images.githubusercontent.com/90714558/158080167-fbedd09b-7e5a-4e37-984a-b0a01729af03.png)


### Virtual Machines
  ![image](https://user-images.githubusercontent.com/90714558/158079764-faa4a7c4-b95c-4c1b-93f4-30f5a199a0e2.png)

### Network Security groups
![image](https://user-images.githubusercontent.com/90714558/158079992-762eaba5-4097-4c48-98d3-0ffa4c087a88.png)



### Load Balancers
![image](https://user-images.githubusercontent.com/90714558/158080105-493fce90-fa28-4aae-830d-340008539d67.png)

## Network Diagram  
![image](https://github.com/bbpalmer/ELK-Stack-Project/blob/main/Resources/ELK%20Stack%20project%20network.pdf)
