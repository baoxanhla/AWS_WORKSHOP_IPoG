---
title: "Week 11 Worklog"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Understand the CI/CD process and the AWS Code Series toolset.
* Experience Amazon AI services.

### Tasks to implement this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Explore CI/CD orchestrator services on AWS <br>&emsp; + AWS CodeCommit <br>&emsp; + AWS CodeBuild <br>&emsp; + AWS CodeDeploy <br>&emsp; + AWS CodePipeline | 11/17/2025   | 11/17/2025      | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Explore AWS Elastic Beanstalk <br>&emsp; + Application <br>&emsp; + Environment <br> - **Hands-on:** Deploy a web application on AWS with Elastic Beanstalk  <br>&emsp; + Create CloudFormation stack <br>&emsp; + Connect Linux EC2 instance and install database <br>&emsp; + Check local server to download project <br>&emsp; + Deploy on Elastic Beanstalk <br>&emsp; + Update application <br>&emsp; + Check environment and query EC2 instance info <br>&emsp; + Clean up resources.| 11/18/2025   | 11/18/2025      | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Update knowledge on Amazon Bedrock <br>&emsp; + Better understand pre-trained AI services like cost and hơw to call API| 11/19/2025   | 11/19/2025    | <https://cloudjourney.awsstudygroup.com/>   |
| Thu | - **Hands-on**: Use Amazon Polly <br>&emsp; + Setup DynamoDB  <br>&emsp; + Explore Amazon Polly <br>&emsp; + Create Speech and speech marks using AWS CLI <br>&emsp; + Create speech marks using AWS Polly SDK for Java  | 11/20/2025   | 11/20/2025      | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - **Hands-on:** Use Amazon Rekognition <br>&emsp; + Create Cognito Identity Pool <br> - Object detection with Amazon Rekognition <br>&emsp; + Facial recognition <br>&emsp; + Test person finding application <br>&emsp; + Attach EBS volume                                                                                         | 11/21/2025   | 11/21/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 11:

* Understand the "Software Supply Chain" process on AWS (CI/CD):

* Understood the shift from manual deployment (copying files, SSH into server) to a fully automated process with the AWS Code Series.
* Grasped the role of each service:

    * AWS CodeCommit: Source code version control (Git-based), the origin of all changes.
    * AWS CodeBuild: Automated compilation and testing environment (Unit Test), ensuring "clean" code before proceeding.
    * AWS CodeDeploy: Automates code deployment to server fleets, minimizing downtime and human error.
    * AWS CodePipeline: The "Conductor" coordinating the entire process above into a continuous flow.

* Grasped Platform as a Service with Elastic Beanstalk:

  * Understood the value of using Elastic Beanstalk to handle the entire configuration process instead of manually configuring VPC, EC2, Load Balancer, and Auto Scaling Groups.


* Updated strategic vision on Generative AI via the event: Generative AI with Amazon Bedrock

  * Understood the model shift from "Self-training models" to "Using Foundation Models (FMs) via API".
  * Grasped core Amazon Bedrock concepts: Serverless AI, ability to integrate Knowledge Bases (RAG) and Agents to build secure and private enterprise AI applications.

* In-depth hands-on integration of AI Services:
  * With Amazon Polly: Converting text to audio
    * Know how to convert simple text to speech.
    * Know how to handle Speech Marks (Metadata about the real-time timing of words), a technique for lip-syncing virtual characters.
    * Know how to use the SDK (Java) to integrate Polly into the backend.
  * With Amazon Rekognition:
    * Know how to use Cognito Identity Pool to grant temporary permissions for applications to access Rekognition directly without hard-coding Access Keys.
    * Understood how to use the API to solve complex computer vision problems: Facial recognition, object detection, and person identification.