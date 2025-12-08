---
title: "Blog 2"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Automating vector embedding generation in  Aurora PostgreSQL with  Bedrock
by **Domenico di Salvia** and **Andrea Filippo La Scola** | on **September 05, 2025** | in Advanced (300), Amazon Aurora, Amazon Bedrock, Technical How-to | Permalink

Vector embeddings have significantly transformed the way we interact with unstructured data in generative AI applications. Embeddings are mathematical representations that enable semantic search, recommendation systems, and several natural language processing tasks by capturing the essence of text, images, and other content in a machine-processable form. In applications using **Retrieval-Augmented Generation (RAG)** or similar AI solutions, keeping embeddings up to date as data changes is crucial to ensure search and recommendation results remain relevant.

Although **Bedrock** provides **fully managed RAG solutions**, many organizations have specific requirements that lead them to build custom vector database solutions using **PostgreSQL** along with the **pgvector extension**. In this article, the authors present multiple approaches for automatically generating embeddings in **Aurora PostgreSQL** when data is inserted or updated. Each approach makes trade-offs in complexity, latency, reliability, and scalability so you can choose the strategy that best fits your application.

---

## Solution Overview
When using Aurora PostgreSQL with the pgvector extension to build a vector database, you need a reliable mechanism to generate or update embeddings whenever the underlying data changes. The general workflow is:

1. Detect when new or modified data requires an embedding.
2. Send that content to a Bedrock embedding model (e.g., Titan).
3. Receive the vector embedding.
4. Store it alongside the source data.

In the article, the authors use **Titan** as the underlying embedding model via Bedrock because it provides production-grade embeddings without managing additional infrastructure. You may also choose other supported models (e.g., Cohere Embed, Anthropic Claude) or even custom models via **SageMaker** or open-source libraries.

### Prerequisites
Before implementing any approach, ensure you have:
- An **Aurora PostgreSQL cluster** with **pgvector** enabled.
- **IAM roles & policies** configured to allow **Bedrock access**.
- For approaches using **AWS Lambda**, VPC configuration allowing Lambda to access both the database and Bedrock.
- For the **aws_ml extension**, a compatible database version.
- For **pg_cron**, ensure the extension is enabled and configured.
- The authors provide a GitHub repository with an AWS CDK stack and source code to deploy the demo environment.

---

## Implementation Approaches

The article describes five automation strategies, each with pros and cons.

### 1. **Database triggers + aws_ml extension (synchronous)**
- Trigger inside the database calls aws_ml synchronously within the same transaction to generate embeddings.
- Includes sample PL/pgSQL code for generating and storing embeddings.
- **Pros:** immediate consistency, few external components.
- **Cons:** slows down transactions, limited scalability, complex error handling, risk of timeouts.

### 2. **Database triggers + aws_lambda extension (synchronous)**
- Trigger synchronously invokes a Lambda function, which generates and returns the embedding.
- Logic is separated from the database but still synchronous.
- **Pros:** more flexibility in Lambda (pre/post-processing), better error observability.
- **Cons:** still blocks the transaction, Lambda latency (cold starts), more configuration overhead.

### 3. **Database triggers + aws_lambda extension (asynchronous)**
- Trigger invokes Lambda asynchronously, returning immediately without waiting for the embedding.
- Lambda later writes the embedding into a document_embeddings table (e.g., via RDS Data API).
- **Pros:** transactions are not blocked; improved write throughput.
- **Cons:** eventual consistency; more complex error handling; slower embedding generation.

### 4. **SQS queue + Lambda batch processing (asynchronous)**
- Trigger sends data changes into an SQS queue; a Lambda consumer processes items in batches.
- Batching reduces API calls, increases retries, and improves fault tolerance.
- **Pros:** highly scalable, robust error handling, efficient API usage.
- **Cons:** longer delay between data changes and embedding availability; more operational complexity.

### 5. **Scheduled updates using pg_cron extension (asynchronous)**
- pg_cron schedules periodic jobs to fetch records requiring embeddings, process them in batches, and update results.
- No triggers, so initial data writes are unaffected.
- **Pros:** simple architecture, fewer external dependencies.
- **Cons:** delayed embedding generation, batch overhead, potential database load during cron runs.

---

## Design Factors to Consider
When selecting a production strategy, consider:

- **Bedrock API rate limits** – heavy usage may require batching or throttling.
- **Token limits** – long text may need chunking.
- **Costs** – dependent on Lambda invocations, API usage, and other AWS services.
- **Latency requirements** – each method has different delays.
- **Database write performance** – synchronous methods slow down transactions.
- **Error handling** – asynchronous architectures handle retries more robustly.
- **Index maintenance** – vector indexes degrade over time and require periodic optimization.

---

## Decision Tree
The authors provide a decision diagram to help choose an embedding strategy based on application needs (latency, consistency, complexity). Start with simpler approaches (e.g., option 1 or 5) and evolve as requirements grow.

They also note the need for vector index maintenance — depending on the index type, periodic maintenance is required to preserve search quality and performance.

A complete solution, deployment scripts, and sample code are available in the GitHub repository linked in the article.

---

## Cleanup
To avoid unnecessary costs, the authors recommend:
1. Deleting all CloudFormation stacks used for the demo.
2. Removing any additional AWS resources created during testing.

---

## Conclusion
Automating embedding generation in Aurora PostgreSQL ensures that AI capabilities such as semantic search, recommendations, and data retrieval stay up to date as your data evolves. Keeping embeddings synchronized with data changes maintains relevance and accuracy for AI applications.

The article outlines a wide range of methods—from triggers, cron jobs, and queues to batch solutions—each with trade-offs around latency, scalability, consistency, and operational complexity. The best choice depends on your application’s tolerance for delay, write volume, and operational overhead.

The authors encourage reviewing the accompanying GitHub repository for full implementation details and example code. Feedback and contributions via issues or pull requests are welcome.

---

## Authors

| |
| --- | ----------------------------------------------------------------------------- |
| Andrea Filippo La Scola ![Image](/images/2-Proposal/andrea.png) | **Andrea** is a Partner Solutions Architect at AWS specializing in **data analytics** and **serverless architectures**. He supports AWS partners and customers in **Italy** in designing innovative solutions based on AWS services. |
| Domenico di Salvia ![Image](/images/2-Proposal/domenico.png) | **Domenico** is a **Senior Database Specialist Solutions Architect** at AWS. He works with customers across the **EMEA** region, providing technical guidance for database projects. He helps them maximize value when using or migrating to AWS by designing cloud database architectures that are **scalable, secure, high-performance, sustainable, cost-efficient, and reliable**. |
