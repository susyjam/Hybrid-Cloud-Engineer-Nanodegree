# Private Cloud Web Application infrastructure
## Project Overview

Our fictitious company is called The E-Commerce Company.

After a failure in our datacenter, the CEO has demanded our team come up with a better solution to prepare and handle such failure events moving forward and mitigate the downtime it caused our customers. You are given the job to design a private cloud solution for your company’s key revenue generator, an e-commerce web application.

According to your CEO, all of the VMs must be protected against failure.

## Tasks

Deploy and protect the three Virtual Machines composing the infrastructure for a web application: a web server VM, application VM and database server VM on the private cloud:
  1. Study the provided e-mails with yor E-Commerce Company IT Leaders to determine whether your organization is Cloud Ready.
  2. Determine the High level requirements from the e-mails.
  3. Configure an on-prem HCI environment to support VMs and implement a data protection/disaster recovery strategy to protect them
  4. Your solution must also show that you are able to recover if one of your protected VMs is deleted.

### First E-mail: CTO E-mail

```
Hello,

It has come to our attention that our main revenue producing application stack is no longer able to 
meet the company's needs for performance and availability. We have been considering a Hyperconverged 
solution with continuing plans to expand into the cloud in the future. We have acquired an HCI cluster 
to do a proof of concept.

We have interviewed all the business stakeholders and determined their processing needs; the next step 
is for you to build out a test solution for evaluation.

We would like to see a 3-tier application stack with a database server VM, application server VM 
and web server VM. Identified requirements are to have separate production and development environments. 
The production environment requires built-in data protection using backup/restore with snapshots and no more
than 1 hour of data loss after a failure. Additional tests for VM workload expansion (cloning), 
the ability to dynamically add CPU/Memory resources to online virtual machines (add 1 vCPU and 2GB memory
to the database server) is required. Final verification is the removal of a key VM and performing a full 
restoration.

The systems administration group has provisioned the test environment HCI cluster. You will be responsible 
for the basic infrastructure configurations and virtual machine buildout and testing. The applications
team will perform the database and application installations. Our CEO would like to see a demo tomorrow - 
you have 8 hours to prepare the environment. I'm sure you're up to the task!

Respectfully,

CTO
```
### Requeriments
  1. Database server VM
  2. Application server VM
  3. Web server VM

### Second E-mail: Network Operations E-mail

```
Hi!

The network infrastructure will consist of separate production and development networks. The production
network will be managed using IPAM/DHCP from an IP Pool provided by the Network Operations group. 
The production network will be on vlan 0, using the 172.31.0.0/24 network. The IP Pool will use a Start 
address of 172.31.0.210 and an End address of 172.31.0.230. The development network will be unmanaged 
on VLAN 101 using the 172.31.101.0/24 network.

Respectfully,

Network Operations
```

### Third E-mail: Network Operations E-mail

```
Hey there!

The basic testing resource requirements for each virtual machine in the 3-tier application stack will be
the same. Microsoft SQL on Windows, has been chosen for the database tier and the application server 
and web server tiers will both be Linux based. Each virtual machine will be configured with 1 vCPU 
and 4 GB of RAM. For testing purposes you will need to configure the Network Time Protocol (NTP) using 
the public service, pool.ntp.org, and 8.8.8.8 for the Domain Naming Service (DNS). You will also need 
to create a new storage container called Images to hold the Windows and CentOS virtual disk images 
(C:\Images) to be uploaded to the Image Service. The virtual machine naming convention will be based 
on a 2-3 letter representation, followed by the environment. Example: Database server for Production, 
use db-prod. Application for development, use app-dev, etc…

The production virtual machines, when created based on the previous criteria, should be duplicated 
to create an identical development environment.

Respectfully,

Systems Administration
```
