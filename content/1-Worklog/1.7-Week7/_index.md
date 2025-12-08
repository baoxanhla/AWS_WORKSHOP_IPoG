---
title: "Week 7 Worklog"
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Grasp the architecture and operation of the Serverless model with Lambda and API Gateway.
* Understand the operational mechanism of AWS Lambda and the basics of Event-Driven architecture.
* Know how to use SQS and SNS with a logical architecture.
* Configure API Gateway as a Lambda trigger.
* Save data from Lambda to DynamoDB.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resources |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| Mon | - Learn about AWS Lambda <br>&emsp; + IAM Role for Lambda <br>&emsp; + Lambda function <br> - Learn about Amazon API Gateway <br>&emsp; + Methods <br>&emsp; + CORS <br> - **Practice**: <br>&emsp; + Create IAM role with least privilege for Lambda to access S3 and DynamoDB <br>&emsp; + Create Lambda function to handle file uploads <br>&emsp; + Configure API Gateway to trigger Lambda <br>&emsp; + Save data from Lambda to DynamoDB | 10/20/2025 | 10/20/2025 |  <https://cloudjourney.awsstudygroup.com/>|
| Tue | - **Practice**: Interaction between Lambda, S3, and DynamoDB <br>&emsp; + Create image processing Lambda function <br>&emsp; + Create S3 Bucket <br>&emsp; + Create IAM Policy for Lambda function and test activity <br>&emsp; + Create and manage table in AWS DynamoDB + Create Lambda function to write data <br>&emsp; + Resource cleanup | 10/21/2025 | 10/21/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - **Practice**: Host static website on S3 <br>&emsp; + Create Bucket, enable hosting, assign policy, and upload frontend folder to S3 <br>&emsp; + Create DynamoDB table, deploy Lambda function to read, write, and delete data <br>&emsp; + Setup API Gateway <br>&emsp; + Test API with Postman <br>&emsp; + Test API with front-end <br>&emsp; + Resource cleanup | 10/22/2025 | 10/22/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Learn Event-driven architecture with Amazon SQS and SNS <br>&emsp; + SQS: queue<br>&emsp; + SNS: Pub and Sub <br> - **Practice**: <br>&emsp; + Create Queue and SNS Topic <br>&emsp; + Create API and Lambda function to interact with Queue and SNS Topic <br>&emsp; + Test activity with APIs <br>&emsp; + Resource cleanup | 10/23/2025 | 10/23/2025 | <https://cloudjourney.awsstudygroup.com/> |
| Fri | - Learn AWS Step Functions <br>&emsp; + Orchestrate microservices | 10/24/2025 | 10/24/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Results achieved in Week 7:

* Understanding of Serverless Architecture on AWS
  * Grasped the architecture and operating model of AWS Lambda, execution lifecycle, and duration-based pricing.
  * Clearly understood API Gateway acting as a HTTP front-door for Lambda, including:
    * **REST API vs HTTP API**: Types of APIs in API Gateway used to expose backends; REST API is feature-rich, HTTP API is lightweight and cost-optimized.
    * **Methods**: Defining HTTP actions (GET/POST/PUT/DELETE) and linking to Lambda or other backends.
    * **CORS**: Allowing front-ends from different domains to call the API, configured via CORS headers.
    * **Integration request/response**: The data transformation layer between API Gateway and backend, including input and output mapping.
    

[Image of AWS API Gateway triggering Lambda function architecture]

  * Understood how to design event-driven architectures, data flows, and advantages over traditional models.

* Deployed Lambda – API Gateway – DynamoDB – S3
  * Created IAM Role with **Least Privilege** for Lambda to access S3 and DynamoDB.
  * Created Lambda Functions to:
    * Handle file uploads from S3.
    * Read, write, and update DynamoDB data.
  * Created API Gateway to trigger Lambda and handle requests/responses.
  * Configured static website hosting on S3 and connected the front-end with API Gateway.

* Interactions between Lambda – S3 – DynamoDB
  * Created S3 bucket and enabled event notifications for Lambda.
  * Wrote Lambda for processing images or data uploaded to S3.
  * Performed CRUD operations with DynamoDB from Lambda.
  * Created DynamoDB tables, indexes (if needed), and handled various data formats.

* Understood and deployed Event-driven systems with SNS & SQS
  * Grasped the models:
    * **SNS** (Publisher → Topic → Subscriber)
    * **SQS** (Producer → Queue → Consumer)
  * Created SNS topics and SQS queues, connected SNS → SQS (fan-out pattern).
  
  * Wrote Lambda functions to publish and consume messages.
  * Tested communication flow via API Gateway and Lambda.

* Learned AWS Step Functions
  * Understood the concept of **orchestration** versus **choreography**.
  * Learned how Step Functions coordinates multiple Lambdas/microservices via a State Machine.