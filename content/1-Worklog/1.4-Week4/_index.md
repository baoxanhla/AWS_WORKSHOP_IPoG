---
title: "Week 4 Worklog"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Goals:

* Understand and apply AWS storage services such as S3, Storage Gateway, and the Snow Family.
* Master backup and data recovery mechanisms using AWS Backup and Disaster Recovery on AWS.
* Learn how to implement secure, scalable, and highly available storage solutions for application systems.

### Tasks to be performed this week:
| Day | Task | Start Date | Completion Date | Reference |
| --- | ----- | ----------- | ---------------- | ---------- |
| 2   | - Learn about Amazon Simple Storage Service (Amazon S3) <br>&emsp; + S3 Bucket <br>&emsp; + S3 Object <br>&emsp; + Access Point <br>&emsp; + Storage Classes: Standard, Standard-IA, Intelligent-Tiering, Glacier <br>&emsp; + S3 Static Website & CORS <br>&emsp; + Access Control <br>&emsp; + Endpoint & Versioning <br>&emsp; + Object Key & Performance <br>&emsp; + Glacier Tiers: Expedited, Standard, Bulk <br> - **Hands-on:** <br>&emsp; + Create an S3 Bucket <br>&emsp; + Upload data to S3 <br>&emsp; + Host a static website on S3: enable static website feature, configure Block Public Access, and make objects public <br>&emsp; + Test the website <br>&emsp; + Accelerate the website with CloudFront <br>&emsp; + Move and copy S3 objects to another region <br>&emsp; + Clean up resources | 09/29/2025 | 09/29/2025 | <https://cloudjourney.awsstudygroup.com/>  |
| 3   | - Learn how to use AWS Backup to create a backup plan for active AWS resources <br>&emsp; + AWS Backup architecture <br>&emsp; + Backup Plan <br>&emsp; + AWS SNS (Simple Notification Service) <br> - **Hands-on:** <br>&emsp; + Create an S3 Bucket and deploy AWS Backup infrastructure <br>&emsp; + Create a Backup Plan <br>&emsp; + Configure Notifications <br>&emsp; + Verify backup operations <br>&emsp; + Clean up resources | 09/30/2025 | 09/30/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about Snow Family: Snowball, Snowball Edge, Snowmobile <br> - Learn about Storage Gateway <br>&emsp; + File Gateway <br>&emsp; + Volume Gateway <br>&emsp; + Tape Gateway <br> - Learn about Disaster Recovery: Recovery Time Objective (RTO) and Recovery Point Objective (RPO) <br>&emsp; + Backup and restore <br>&emsp; + Pilot Light (Active-Standby) <br>&emsp; + Warm Standby (Low Capacity Active-Active) <br>&emsp; + Full Capacity (Active-Active) <br> - **Hands-on:** <br>&emsp; + Create a Storage Gateway <br>&emsp; + Create File Shares <br>&emsp; + Connect File Shares from on-premises environment <br>&emsp; + Clean up resources | 10/01/2025 | 10/01/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about AWS Import/Export <br> - **Hands-on:** <br>&emsp; + Prepare a virtual machine on VMware Workstation <br>&emsp; + Import a VM into AWS: export VM from on-premises, upload to AWS, import as AMI, launch EC2 Instance from imported AMI <br>&emsp; + Export EC2 Instance to VM: configure ACL for S3 Bucket, export from EC2 instance, export from AMI <br>&emsp; + Clean up resources | 10/02/2025 | 10/02/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Learn about Amazon FSx <br> - **Hands-on:** <br>&emsp; + Prepare practice environment <br>&emsp; + Create an SSD Multi-AZ file system <br>&emsp; + Create an HDD Multi-AZ file system <br>&emsp; + Create new file shares <br>&emsp; + Test performance <br>&emsp; + Monitor performance <br>&emsp; + Enable data deduplication <br>&emsp; + Enable shadow copies <br>&emsp; + Manage user sessions and file opens <br>&emsp; + Enable user storage quotas <br>&emsp; + Enable continuous share <br>&emsp; + Scale throughput capacity <br>&emsp; + Scale storage capacity <br>&emsp; + Clean up resources | 10/03/2025 | 10/03/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Week 4 Achievements:

* Understood the structure and operation of S3 Bucket, Objects, Access Points, ACL/Policy, CORS, Versioning, Object Keys, and storage classes (Standard, IA, Intelligent-Tiering, Glacier).
* Successfully implemented:
  * Created buckets and uploaded objects  
  * Hosted a static website and accelerated it with CloudFront  
  * Configured public access and access control  
  * Performed cross-region object replication  

* Understood and practiced hybrid storage integration from on-premises to AWS using Storage Gateway.
* Gained detailed understanding of the Snow Family and its use cases for large-scale data migration.
* Learned and applied Amazon FSx: created Multi-AZ SSD/HDD file systems, managed shares, shadow copies, deduplication, monitoring, and scaled performance/storage.

* Mastered AWS Backup & Disaster Recovery mechanisms:
  * Understood AWS Backup architecture, Backup Vault, Backup Plan, and lifecycle behavior.
  * Successfully configured Backup Plan, SNS, Notifications, automated backups, and tested restores.
  * Learned Disaster Recovery details:
    * **RTO**: Maximum acceptable downtime for recovery.  
    * **RPO**: Maximum acceptable data loss from the time an incident occurs.  
    * **Pilot Light**  
    * **Warm Standby**  
    * **Multi-Site Active-Active**  

* Gained ability to deploy secure, scalable, and highly available storage solutions:
  * Applied Versioning and Replication (S3) for high availability.
  * Used Multi-AZ FSx for fault-tolerant storage architecture.
  * Used CloudFront for global optimization of static content delivery.
  * Understood DR models for fast system recovery.
  * Learned how to scale FSx throughput and storage capacity.

* Improved hybrid storage deployment skills between on-premises and AWS:
  * Learned VM Import/Export workflows: export VM from VMware, upload to S3, import as AMI, launch EC2, export EC2 back to VM format.
  * Connected Storage Gateway File Shares to the on-premises environment.
