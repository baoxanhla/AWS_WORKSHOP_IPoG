---
title: "Week 12 Worklog"
weight: 2
chapter: false
pre: " <b> 1.12 </b> "
---

### Week 12 Objectives:

* Review Serverless and AI knowledge systems.
* Detailed design of DynamoDB database tables for the project and API.
* Detailed check of connections between services in the project.

### Tasks to implement this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Review and design database (DynamoDB) <br>&emsp; + Review knowledge on Partition Key (PK) and Sort Key (SK) <br> - **Hands-on** <br>&emsp; + Design Schema for project tables <br>&emsp; + Determine Access Patterns (Data query methods) for the project.   | 11/24/2025   | 11/24/2025  | <https://cloudjourney.awsstudygroup.com/>    |
| Tue | - Review and design API (API Gateway + Lambda): <br> &emsp; + Review how to create REST API, Lambda Proxy Integration. <br> &emsp; + List necessary API endpoints: POST, GET | 11/25/2025   | 11/25/2025      | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Review AI integration flow with Bedrock  <br> &emsp; + Review Bedrock API call methods <br> &emsp; + Review basic Prompt Engineering| 11/26/2025   | 11/26/2025      | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Review security and authentication (Cognito + IAM ) <br> &emsp; + Review User Login flow -> Receive Token -> Send Token to API Gateway. <br> &emsp; + Review IAM Policy regarding least privilege  | 11/27/2025   | 11/27/2025      | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - Review system monitoring and operational methods <br> &emsp; + Review CloudWatch to plan monitoring when the project runs. <br> &emsp; + Review Boto3 <br> &emsp; + Plan project deployment steps | 11/28/2025 | 11/28/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 12:

* Completed Schema Design for DynamoDB:
  * Designed specific data tables, optimized for data retrieval.

* Clearly defined connection interfaces:
  * Defined clear input/output for Lambda functions.
  * Grasped how to use the `boto3` library to connect AWS "puzzle pieces" together.

* Prepared AI scenarios (Prompt Strategy) ready to test Bedrock as expected.

* Understood the Identity flow from Cognito through API Gateway down to Lambda.