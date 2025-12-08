---
title: "Week 9 Worklog"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Goals:

* Get familiar with the AWS data and Machine Learning ecosystem.
* Understand the key features supported in AWS's AI ecosystem.

### Tasks to complete this week:
| Day | Tasks                                                                                                                                                                                   | Start Date | End Date | Reference |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | -------- | --------- |
| 2   | - Learn about AWS Glue <br>&emsp; + Crawler <br> - Learn about Amazon Athena <br> - Learn about Amazon QuickSight <br> - Learn about Amazon SageMaker | 11/03/2025   | 11/03/2025   | <https://cloudjourney.awsstudygroup.com/>   |
| 3   | - **Hands-on**: Data Analysis <br>&emsp; + Create IAM Role and IAM Policy + Create S3 Bucket <br>&emsp; + Create Glue Crawler and validate data <br>&emsp; + Create notebook with AWS Glue Studio <br>&emsp; + Analyze using Athena and visualize with QuickSight <br>&emsp; + Clean up resources | 11/04/2025   | 11/04/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - **Hands-on**: Data analysis with Amazon SageMaker <br>&emsp; + Create SageMaker Studio <br>&emsp; + Prepare dataset, analyze data, and export to S3 <br>&emsp; + Train and fine-tune Machine Learning models <br>&emsp; + Deploy and evaluate model performance <br>&emsp; + Automatic model tuning <br>&emsp; + Clean up resources | 11/05/2025   | 11/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about Amazon Bedrock <br>&emsp; + Foundation Models <br>&emsp; + Bedrock Agents <br>&emsp; + Knowledge Bases <br>&emsp; + Bedrock Inference Features | 11/06/2025   | 11/06/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Learn about Pre-trained AI Services <br>&emsp; + Amazon Rekognition <br>&emsp; + Amazon Translate <br>&emsp; + Amazon Textract <br>&emsp; + Amazon Transcribe <br>&emsp; + Amazon Polly <br>&emsp; + Amazon Comprehend <br>&emsp; + Amazon Kendra <br>&emsp; + Amazon Lookout <br>&emsp; + Amazon Personalize | 11/07/2025   | 11/07/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Week 9 Achievements:

* Understand and build a serverless data processing pipeline:

  * Understand the modern Data Lake model on AWS, with S3 as the central storage.
  * AWS Glue: Glue Crawler automatically detects schema from raw data (CSV/JSON in S3) and generates metadata.
  * Convert unstructured data into structured tables in Glue Data Catalog for querying.
  * Amazon Athena: Query data stored in S3 using SQL without provisioning servers or loading data into a traditional database.
  * Amazon QuickSight: Connect to Athena for data visualization, create BI dashboards to enable data-driven decisions.

* Understand the Machine Learning development workflow on Amazon SageMaker:

  * Environment: SageMaker Studio.
  * Training: Understand the decoupled resource model—Notebook for coding, but when calling fit(), SageMaker provisions a separate training cluster, which shuts down automatically after completion to optimize cost.
  * Optimization: Use Automatic Model Tuning to find the best hyperparameters instead of manual experimentation.
  * Deployment: Deploy the trained model to a real-time inference Endpoint (REST API).

* Grasp the Generative AI trend with Amazon Bedrock:

  * Understand the shift from "training your own model" to "using Foundation Models (FMs)" via API.
  * Understand core components for building modern LLM applications:
    * Knowledge Bases: RAG (Retrieval-Augmented Generation) mechanism to provide enterprise-specific data to AI.
    * Agents: Allow AI not only to "chat" but also to perform actions (call APIs, retrieve data).

* Understand the ecosystem of Pre-trained AI Services (no ML model building required):

  * Classify service groups to apply to the right business problem without building models from scratch:

    * Vision: Rekognition (image/video analysis).
    * Speech/Audio: Transcribe (STT), Polly (TTS).
    * NLP/Text: Translate, Comprehend (sentiment/entity analysis), Textract (document OCR).
    * Specialized: Personalize (recommendations), Lookout (predictive maintenance).
