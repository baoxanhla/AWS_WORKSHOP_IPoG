---
title: "Week 5 Worklog"
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Understand security services on AWS and AWS core security principles.
* Manage identities, access rights, and secure user authentication on AWS.
* Protect and operate data using encryption and data management mechanisms.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Learn about the Shared Responsibility Model <br>&emsp; + Responsibilities of "AWS" and the "Customer" <br>&emsp; + Security responsibilities for each type of service <br> - Learn the basics of Amazon Identity and Access Management (IAM): <br>&emsp; + Root Account <br>&emsp; + AWS IAM <br>&emsp; + IAM Principals <br>&emsp; + IAM User <br>&emsp; + IAM Policy <br>&emsp; + IAM Role <br>&emsp; + IAM Permission Boundary. | 10/06/2025 | 10/06/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - **Practice**: <br>&emsp; + Create IAM Group, IAM User, IAM Role, and Assume Role <br>&emsp; + Create EC2 Admin User, RDS Admin User, and Admin Group <br>&emsp; + Configure IAM Role Condition <br>&emsp;&nbsp;&nbsp; + Create IAM Role with Admin rights <br>&emsp;&nbsp;&nbsp; + Create IAM User <br>&emsp;&nbsp;&nbsp; + Configure Switch Role <br>&emsp;&nbsp;&nbsp; + Restrict by IP or Time <br>&emsp; + Limit User permissions <br>&emsp;&nbsp;&nbsp; + Create restrictive policy <br>&emsp;&nbsp;&nbsp; + Create restricted IAM <br>&emsp;&nbsp;&nbsp; + Test restricted User <br>&emsp; + Resource cleanup | 10/07/2025 | 10/07/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Learn how to use Tags and Resource Groups: <br>&emsp; + Tags <br>&emsp; + AWS Resource Groups <br> - **Practice**: <br>&emsp; + Use Tags via Console: create EC2 with Tags, add or remove Tags, and create resources by Tag <br>&emsp; + Use Tags via CLI <br> &emsp; + Create Resource Group <br>&emsp; + Manage access to EC2 Resource Tag services with AWS IAM <br>&emsp;&nbsp;&nbsp; + Create IAM User, IAM Policy, and IAM Role <br>&emsp;&nbsp;&nbsp; + Switch Role <br>&emsp;&nbsp;&nbsp; + Check IAM Policy: Access to AWS Region allowed/denied, use Resource Tag with values not meeting conditions, modify Resource Tag on EC2 and check policy <br>&emsp; + Create IAM Policy, IAM Role and check IAM Role <br>&emsp; + Resource cleanup. | 10/08/2025 | 10/08/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Learn the basics of Amazon Cognito: <br>&emsp; + User Pool <br>&emsp; + Identity Pool <br> - Learn about AWS Organizations <br> - Learn about AWS Identity Center (SSO) <br> - Learn about AWS Key Management Service (KMS) <br> - Learn about AWS Security Hub <br> - **Practice**: <br>&emsp; + Activate Security Hub <br>&emsp; + Review each standard set <br>&emsp; + Resource cleanup. | 14/09/2025 | 15/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - **Practice:** <br>&emsp; + Use AWS SSO <br>&emsp;&nbsp;&nbsp; + Create AWS Account in AWS Organizations, setup Organization Unit <br>&emsp;&nbsp;&nbsp; + Setup AWS SSO and test <br>&emsp; + Encryption with AWS KMS <br>&emsp;&nbsp;&nbsp; + Create Policy and Role <br>&emsp;&nbsp;&nbsp; + Create Group and User <br>&emsp;&nbsp;&nbsp; + Create Key Management Service <br>&emsp;&nbsp;&nbsp; + Create bucket and upload data to Amazon S3 <br>&emsp;&nbsp;&nbsp; + Create AWS CloudTrail for logging and Amazon Athena for data querying <br>&emsp;&nbsp;&nbsp; + Test and share encrypted data on S3 <br>&emsp; + Resource cleanup | 10/10/2025 | 10/10/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 5:

* Better understanding of the AWS security model:
    * Security responsibilities vary by service type, for example:
        * AWS is responsible for security *of* the cloud and is fully managed by AWS (infrastructure, hardware, etc.).
        * Customers are responsible for security configuration *in* the cloud for their data/applications (service configuration, access rights, data, encryption...).
    * Recognized that IAM and KMS play a critical role in AWS security.

* Understood and realized how to use AWS IAM:
    * Grasped concepts: Root Account, IAM User, IAM Group, IAM Role, IAM Policy, Permission Boundary.
    * Know how to create and manage basic IAM, assign permissions based on the least privilege principle, and use Roles to enhance security.

* Know how to use Tags to control and manage access:
    * Know how to use Tags for basic services via Console and CLI.
    * Created Resource Groups to group resources by tags.
    * Tested denial cases due to wrong Region, wrong Tag, or unsatisfied IAM Policy conditions.

* Understood the role of AWS Cognito:
    * User Pool: Manage user accounts and the login process.
    * Identity Pool: Grant temporary AWS credentials for applications to access AWS services.

* Know how to use AWS Organizations and Identity Center:
    * Know how to create OUs and grasp the principles of operating a multi-account environment such as: environment isolation, centralized management, and applying unified security policies.
    * Know how to setup AWS SSO, create Permission Sets, and log in to child accounts from a single identity.

* Know how to use AWS KMS to encrypt and protect data.
* Know how to activate and use AWS Security Hub to evaluate security standards, understand findings, and improve them.