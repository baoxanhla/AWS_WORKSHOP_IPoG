---
title: "Week 10 Worklog"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

* Know how to deploy Amazon CloudWatch to monitor the system.
* Understand the AWS CloudTrail process for recording detailed API activity tracking.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Learn about Amazon CloudWatch <br>&emsp; + Metrics <br>&emsp; + Logs <br>&emsp; + Alarms <br>&emsp; + Events <br>&emsp; + Dashboards <br>&emsp; + AWS X-Ray | 11/10/2025 | 11/10/2025 | <https://cloudjourney.awsstudygroup.com/>|
| Tue | - **Practice**: <br>&emsp; + Create IAM Role, IAM policy, and configure EC2 Instance <br>&emsp; + Configure CloudWatch metrics, logs <br>&emsp; + Activate CloudWatch Alarms <br>&emsp; + Configure Dashboards <br>&emsp; + Resource cleanup | 11/11/2025 | 11/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Learn AWS CloudTrail <br>&emsp; + Trails <br>&emsp; + Events: Read/Write/All <br>&emsp; + CloudTrail Insights | 11/12/2025 | 11/12/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Learn AWS Amplify <br>&emsp; + Frontend <br>&emsp; + Backend <br>&emsp; + Storage <br>&emsp; + Authentication | 11/13/2025 | 11/13/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - **Practice:**: Monitor Lambda with CloudWatch and X-Ray <br>&emsp; + Host source code on Amplify <br>&emsp; + Monitor with CloudWatch: Debug with logs, create customer metrics, and create alerts with Alarms <br>&emsp; + Monitor with X-Ray <br>&emsp; + Resource cleanup. | 11/14/2025 | 11/14/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 10:

* Basic deployment of comprehensive monitoring system with Amazon CloudWatch:

  * **Metrics**: Distinguished between Default Metrics (like CPU, Network) and Custom Metrics (like Memory usage, Disk space - metrics AWS cannot automatically collect from outside the hypervisor). Knew how to install CloudWatch Agent to push these custom metrics from EC2 to CloudWatch.
  * **Centralized Log Management**: Knew how to aggregate logs from multiple sources (EC2 app logs, Lambda execution logs) into CloudWatch Logs Groups for lookup.
  * **Alarms**: Established an alert system (via email/SMS with SNS) when the system encounters issues (CPU overload, full disk, or application returning many errors).
  * **Management Dashboard**: Built a visual dashboard displaying the health of the entire system on a single screen.
  

* Security control with AWS CloudTrail:

  * Clearly distinguished the core difference: CloudWatch answers "How is the system performing?", while CloudTrail answers "Who did what to the system?".
  * Knew how to track API call history for security and incident investigation purposes. Example: Finding out who accidentally deleted a Security Group or who stopped an EC2 instance.
  * Understood **CloudTrail Insights** to automatically detect anomalous behaviors in the account (e.g., a spike in API calls to create resources).
  

* Rapid application deployment with AWS Amplify:

  * Understood Amplify is a toolkit to accelerate the web/mobile app development process, automating the connection of Frontend to Backend services (Auth, Storage, API).
  
  * Successfully practiced a simplified CI/CD process: Push code to Git -> Amplify automatically builds and deploys to the Hosting environment.
  * Knew how to integrate monitoring (CloudWatch/X-Ray) directly into the application deployed by Amplify to track end-user experience.