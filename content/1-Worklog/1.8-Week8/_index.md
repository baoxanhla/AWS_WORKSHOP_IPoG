---
title: "Week 8 Worklog"
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Automate resource creation using CloudFormation.
* System configuration management.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Learn AWS CloudFormation, Cloud9 <br>&emsp; + Template: Json, Yaml <br>&emsp; + Stack <br>&emsp; + Drift Detection<br> -**Practice** <br>&emsp; + Use Cloud9 to create a basic CloudFormation template | 10/27/2025 | 10/27/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - **Practice:** Advanced CloudFormation: <br>&emsp; + Create Lambda Function <br>&emsp; + Create Stack <br>&emsp; + Connect EC2 instance <br>&emsp; + Mappings and StackSets <br>&emsp; + Drift Detection <br>&emsp; + Resource cleanup | 10/28/2025 | 10/28/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Learn AWS Systems Manager (SSM) <br>&emsp; + Patch Manager <br>&emsp; + Run Command <br>&emsp; + Session manager <br> - **Practice** <br> &emsp; + Create EC2 instance, IAM Role and assign IAM Role <br> &emsp; + Configure Patch Manager + Run Command <br> &emsp; + Resource cleanup | 10/29/2025 | 10/29/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Learn AWS CDK <br> **Practice**: AWS CDK with VS Code <br>&emsp; + Create public EC2 instance <br>&emsp; + Configure VS Code environment to use AWS CDK <br>&emsp; + Create ECS cluster, Application, and Combine API Gateway with Application Load Balancer <br>&emsp; + Create Lambda function, API Gateway, S3 <br>&emsp; + Deploy Stack and upload files to S3 <br>&emsp; + Create Nested Stacks with CDK and deploy <br>&emsp; + Resource cleanup. | 10/30/2025 | 10/30/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - **Practice**: Session Manager: <br> &emsp; + Create private & public EC2 instances and IAM Role <br> &emsp; + Connect to Public server <br> &emsp; + Create connection to Private EC2 server <br> &emsp; + Update IAM Role to access S3 + Create S3 Buckets and S3 Gateway VPC Endpoint <br> &emsp; + Monitor session logs with SSM Session Manager <br> &emsp; + Configure Port Forwarding <br> &emsp; + Resource cleanup. | 10/31/2025 | 10/31/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 8:

* Understood and practiced CloudFormation basics
  * Understood CloudFormation architecture, how templates work, and the Stack lifecycle.
  
  * Distinguished main components:
    * **Template**: Defines resources (YAML/JSON).
    * **Parameters, Mappings, Resources, Outputs**.
    * **Stack**: A group of resources deployed from a template.
    * **StackSets**: Deploy stacks across multiple accounts/regions.
    * **Drift Detection**: Checks for differences between actual resources and the template configuration.
    
  * Created basic CloudFormation templates to deploy resources (EC2, Lambda, Security Group…).

* Deployed Advanced CloudFormation
  * Created a stack to deploy Lambda functions and EC2.
  * Learned how to use **Mappings, Parameters, and Outputs** in templates.
  * Used **StackSets** to deploy to multiple Regions/AWS Accounts.
  * Practiced **Drift Detection** to detect changes compared to the template.
  * Practiced the basic **deploy – update – delete** stack workflow.

* Know how to use AWS Systems Manager (SSM)
  * Created EC2 and configured IAM Role to connect with SSM.
  * Used **Session Manager** to connect to EC2 without needing SSH/Keypairs.
  
  * Practice:
    * Run remote commands with **SSM Run Command**.
    * Configure and run **Patch Manager** to update the OS.
    * Record EC2 access logs to S3.
    * Practice **Port Forwarding** via SSM.
  * Understood security benefits when not opening port 22.

* Learned AWS CDK (Cloud Development Kit)
  * Understood how CDK allows defining cloud infrastructure using familiar programming languages.
  
  * Practiced creating and deploying Nested Stacks.

* Know how to use Session Manager
  * Connected Public EC2 → Private EC2 via Session Manager.
  * Created and used **S3 Gateway VPC Endpoint** so Private EC2 can access S3 without Internet.
  * Monitored activities in Session Manager Logs.
  * Cleaned up resources.