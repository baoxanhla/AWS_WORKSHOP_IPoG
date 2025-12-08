---
title: "Week 3 Worklog"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Goals:

* Understand the core virtual server service (Amazon EC2) and key compute-related components in AWS.
* Gain a clear understanding of the architecture, operating mechanisms, and management of virtual server services in AWS.

### Tasks to be performed this week:
| Day | Task                                                                                                                                                                                   | Start Date | Completion Date | Reference |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | ---------- |
| 2   | - Learn about Amazon Elastic Compute Cloud (EC2): <br>&emsp; + Instance type <br>&emsp; + AMI, Backup, Key Pair <br>&emsp; + Elastic Block Store <br>&emsp; + Instance Store <br>&emsp; + User Data <br>&emsp; + Meta Data <br>&emsp; + EC2 Auto Scaling <br>&emsp; + EFS/FSx – Lightsail – MGN | 09/22/2025 | 09/22/2025| <https://cloudjourney.awsstudygroup.com/> |
| 3   | - **Hands-on:** <br>&emsp; + Create and connect to EC2 Instances on Windows and Linux <br>&emsp; + Create EC2 Snapshot (Backup) <br>&emsp; + Install applications on EC2 <br>&emsp; + Use Tags and Resource Groups for resource management <br>&emsp; + Limit resource usage with IAM <br>&emsp; + Clean up resources | 09/23/2025 | 09/23/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about Amazon CloudWatch <br>&emsp; + Metrics <br>&emsp; + Logs <br>&emsp; + Alarms <br>&emsp; + Dashboard <br> - **Hands-on:** <br>&emsp; + Configure CloudWatch Metrics for EC2 <br>&emsp; + Analyze CloudWatch Logs from EC2 applications and create Metrics Filters <br>&emsp; + Configure CloudWatch Alarms for alerts <br>&emsp; + Build CloudWatch Dashboard for EC2 monitoring <br>&emsp; + Clean up resources | 09/24/2025 | 09/24/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about EC2 Auto Scaling <br>&emsp; + Auto Scaling Group <br>&emsp; + Scaling types: manual, scheduled, dynamic <br>&emsp; + Launch Template <br>&emsp; + Elastic Load Balancer <br> - **Hands-on:** <br>&emsp; + Create a Launch Template <br>&emsp; + Create a Target Group <br>&emsp; + Create a Load Balancer <br>&emsp; + Create an Auto Scaling Group for flexible scaling <br>&emsp; + Verify behaviors of different scaling mechanisms <br>&emsp; + Clean up resources | 09/25/2025 | 09/25/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Learn about Amazon Lightsail <br>&emsp; + Lightsail Database <br>&emsp; + WordPress Instance <br>&emsp; + PrestaShop E-Commerce Instance <br>&emsp; + Akaunting Instance <br>&emsp; + Akaunting Instance <br> - **Hands-on:** <br>&emsp; + Deploy different instances and databases: WordPress, PrestaShop E-Commerce, and Akaunting <br>&emsp; + Use Lightsail Load Balancer <br>&emsp; + Create Snapshot for backup and restore <br>&emsp; + Scale up to a larger instance <br>&emsp; + Clean up resources | 09/26/2025 | 09/26/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Week 3 Achievements:

* Gained understanding of the architecture and operation of Amazon EC2 and differentiated between Instance Types (General Purpose, Compute Optimized, Memory Optimized, Storage Optimized).
* Understood how to use Amazon Machine Image (AMI), Key Pair, Elastic Block Store (EBS), and Instance Store for server configuration and management.
* Learned how to use User Data and Meta Data to automate configuration during EC2 Instance launch.
* Understood and practiced working with EFS/FSx for shared storage across instances.

* Successfully created and connected to EC2 Instances using both Windows and Linux.
* Created and restored EC2 Snapshots (Backups).
* Installed basic web applications on EC2 Instances.
* Used Tags and Resource Groups to classify and manage resources effectively.
* Configured IAM to restrict access and control resource usage.

* Fully understood the components of Amazon CloudWatch: Metrics, Logs, Alarms, and Dashboard.
* Configured CloudWatch Metrics for EC2 and created Metrics Filters from application logs.
* Set up CloudWatch Alarms to receive alerts when CPU or network traffic exceeds thresholds.
* Built CloudWatch Dashboards to summarize and monitor EC2 system status.

* Gained full understanding of EC2 Auto Scaling mechanisms and scaling types:  
  * **Manual**: manually adjust the number of EC2 instances when resource demand changes.  
  * **Scheduled**: automatically scale based on defined schedules, suitable for predictable traffic patterns to reduce cost.  
  * **Dynamic**: automatically scale out/in based on CloudWatch metrics such as CPU usage or network traffic.  
* Learned how to configure and test Auto Scaling Group behavior under varying load.

* Studied and deployed different Lightsail Instances:  
  * WordPress Instance: basic CMS website.  
  * PrestaShop Instance: e-commerce platform.  
  * Akaunting Instance: financial and accounting management system.  
* Used Lightsail Database for application data storage and Lightsail Load Balancer for higher availability and load distribution.
* Learned how to create Snapshots for backups and upgrade to larger instance sizes.

