---
title: "Week 2 Worklog"
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Goals:

* Design and deploy a VPC following the AWS Well-Architected Framework.
* Configure key network security components.
* Establish secure connectivity between on-premises environments and AWS.

### Tasks to be performed this week:
| Day | Task | Start Date | Completion Date | Reference |
| --- | ----- | ----------- | ---------------- | --------- |
| 2   | - Learn about Amazon Virtual Private Cloud (Amazon VPC), Architecture and Scope <br>&emsp; + AWS Region <br>&emsp; + Availability Zones (AZ) <br>&emsp; + Classless Inter-Domain Routing (CIDR) <br> - Learn about core Amazon VPC components <br>&emsp; + Subnet <br>&emsp; + Route Table <br>&emsp; + Internet Gateway <br>&emsp; + NAT Gateway <br> - Learn about VPC firewall components <br>&emsp; + Security Group <br>&emsp; + Network ACLs <br>&emsp; + How to use the Resource Map <br> - **Practice:** <br>&emsp; + Create VPC <br>&emsp; + Create Subnets <br>&emsp; + Create Internet Gateway <br>&emsp; + Create Route Table <br>&emsp; + Create Security Group <br>&emsp; + Enable VPC Flow Logs | 09/15/2025 | 09/15/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn EC2 basics <br>&emsp; + Instance types <br>&emsp; + AMI <br>&emsp; + Key Pair <br>&emsp; + Network Setup <br> - Learn SSH remote methods into EC2 <br> - Learn Elastic IP <br> - Learn VPC Reachability Analyzer <br> - Learn AWS Systems Manager Session Manager and Amazon CloudWatch | 09/16/2025 | 09/16/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Practice:** Deploy Amazon EC2 with multi-AZ, create NAT Gateways and Amazon CloudWatch for VPC <br>&emsp; + Launch EC2 instances in Public and Private Subnets <br>&emsp; + SSH connection <br>&emsp; + Create and configure NAT Gateway <br>&emsp; + Use Reachability Analyzer <br>&emsp; + Create EC2 Instance Connect Endpoint <br>&emsp; + Use Session Manager <br>&emsp; + Deploy CloudWatch monitoring for VPC resources <br>&emsp; + Resource cleanup: Terminate EC2 instances, delete NAT Gateway and Elastic IP Address, remove VPC Endpoints | 09/17/2025 | 09/17/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn AWS Site-to-Site VPN <br>&emsp; + AWS Site-to-Site VPN <br>&emsp; + Virtual Private Gateway <br>&emsp; + Customer Gateway <br>&emsp; + AWS VPN Tunnel <br> - Learn Transit Gateway <br> - Learn VPC Peering | 09/18/2025 | 09/18/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice:** <br>&emsp; + Configure Site-to-Site VPN: Create VPN environment and configure VPN connectivity <br>&emsp; + Configure VPC Peering <br>&emsp; + Configure Transit Gateway | 09/19/2025 | 09/19/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Week 2 Achievements:

* Successfully created and configured a VPC following the AWS Well-Architected Framework:
  * Main VPC with CIDR block (10.0.0.0/16)
  * Two subnets: Public and Private across separate Availability Zones (multi-AZ)
  * Fully configured Route Tables, Internet Gateway, and NAT Gateway ensuring Private Subnet instances access the internet securely
  * Enabled VPC Flow Logs and monitored network traffic in CloudWatch Logs

* Able to deploy and manage EC2:
  * Launched EC2 instances in Public and Private Subnets, assigned Elastic IP to the public instance
  * Accessed EC2 using SSH, Instance Connect, and Session Manager (no Public IP required)
  * Monitored EC2 operations via CloudWatch (CPU, Network, Status Checks)

* Configured Security Group and Network ACLs for enhanced security:
  * Security Group – instance-level protection
  * Network ACL – subnet-level protection  
* Understood CloudWatch Alarms to warn about abnormal CPU or network activity.

* Learned and practiced AWS Site-to-Site VPN to securely connect AWS with on-premises:
  * Created Virtual Private Gateway (VGW) and attached it to VPC  
  * Created Customer Gateway (CGW) simulating on-premises environment  
  * Established a stable IPSec VPN tunnel between AWS and CGW  

* Practiced VPC Peering to connect two isolated VPCs within the same Region
* Learned and tested AWS Transit Gateway
* Understood and applied AWS Systems Manager for managing infrastructure without direct SSH access
