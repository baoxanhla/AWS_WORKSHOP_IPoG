---
title: "Event 2"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Report “Generative AI with Amazon Bedrock”

### Purpose of the Event

- Provide foundational knowledge about Generative AI and how it differs from traditional Machine Learning.
- Detailed description of Amazon Bedrock and Foundation Models.
- Technical guidance on RAG (Retrieval Augmented Generation) to build intelligent and accurate AI applications while reducing hallucinations.
- Introduction to the ecosystem of specialized AI services on AWS.

### Speakers

- **Lam Tuan Kiet** - Sr DevOps Engineer, FPT Software.
- **Danh Hoang Hieu Nghi** - AI Engineer, Renova Cloud.
- **Dinh Le Hoang Anh** - Cloud Engineer Trainee, First Cloud AI Journey.

### Key Highlights

#### The shift: Traditional ML vs Foundation Models

- **Traditional ML Models**: Specialized for specific tasks, require labeled data, and need separate training/deployment pipelines for each purpose.
- **Foundation Models (FM)**: Trained on massive amounts of unstructured data, capable of adapting to various tasks such as text generation, summarization, Q&A, and chatbot applications.

#### The AI Ecosystem on AWS

- **Amazon Bedrock**: A hub of leading foundation models from AWS partners (AI21 Labs, Anthropic, Cohere, Meta, Stability AI,...) and Amazon models.
- **AWS Specialized AI Services**: “Instant-use” AI services optimized for specific tasks without requiring model training:
    - Amazon Rekognition: Object detection, face recognition, emotion detection, celebrity recognition, video analysis – $0.001/image for the first 1M images.
    - Amazon Translate: Real-time multilingual text translation with high accuracy and natural tone.
    - Amazon Textract: Extracts structured information (tables, forms) from scanned documents or PDFs.
    - Amazon Transcribe: Converts speech to text.
    - Amazon Polly: Converts text to speech.
    - Amazon Comprehend: Sentiment analysis, keyword extraction, and topic classification.
    - Amazon Kendra: Natural-language search across internal enterprise documents.
    - Amazon Lookout: Detect anomalies in production lines or industrial machinery for predictive maintenance.
    - Amazon Personalize: Real-time recommendation system powered by machine learning.

#### Prompting Technique: Chain of Thought (CoT)

- Comparison between **Standard Prompting** and **Chain-of-Thought Prompting**.
- CoT guides the model to reason step-by-step for complex logic problems, significantly improving accuracy compared to simply requesting the final result.

#### RAG (Retrieval Augmented Generation) – Technical Core

- **Problem**: Addressing hallucinations and lack of updated knowledge in LLMs.
- **Solution**: Combine Retrieval from an external Knowledge Base with the Generation capability of LLMs.
- **Data Ingestion Process**:
    1. Raw Data (New data) → Chunking.
    2. Processed through an Embeddings model (e.g., Amazon Titan Text Embeddings V2.0).
    3. Stored as vectors in a Vector Store (OpenSearch Serverless, Pinecone, Redis...).
- **RetrieveAndGenerate API**: Manages the entire pipeline from user input → embedding query → retrieving relevant data → augmenting the prompt → generating the final response.

### What I Learned

#### AI and Cloud Mindset

- Understand when to use **Specialized AI Services** for fast, specific tasks and when to use **Bedrock/GenAI** for creative and complex workloads.
- Master the design mindset of RAG systems: not just calling LLM APIs, but managing data and vectorization to provide accurate context for AI outputs.

#### Technical Architecture

- The **Chain of Thought** technique is key to optimizing model output without fine-tuning.
- Deep understanding of Amazon Titan Embeddings V2.0 and its role in converting multilingual text into vectors (supports 100+ languages, flexible vector sizes 256/512/1024).

### Application to Work

- Applying Amazon Bedrock to the current project:  
  - Amazon Rekognition: Identify food items from images to auto-fill calorie information.  
  - Amazon Comprehend: Analyze text to standardize food names and store calorie data.
- Experiment with RAG in the ongoing project.
- Use Bedrock Agents to orchestrate tasks such as querying food items from a vector store, calculating calorie goals, and generating daily meal plans.

### Experience at the Event

Joining the workshop “Generative AI with Amazon Bedrock” provided a very practical perspective on building modern AI applications, from foundational theory to real-world implementation.

#### Hands-on Knowledge from Experts

- Speakers clearly explained the data flow in a **RAG** system, helping me visualize the “black box” behind modern chatbot applications.
- The distinction between **Traditional ML** and **Generative AI** helped reshape my strategy for choosing technologies in future projects.

#### Technology Experience

- Impressed by **RetrieveAndGenerate API** in Bedrock as it eliminates much manual work in linking Vector Stores with LLMs.
- Saw the power of **Amazon Titan Embedding** in supporting multilingual applications, making it very suitable for the Vietnamese market.

#### Key Takeaways

- RAG is the new standard: For AI to work in enterprises, RAG is essential for accuracy and data security.
- Full ecosystem: AWS provides everything from infrastructure (Vector Store) to models (Bedrock) and application-level orchestration (Agents), significantly accelerating implementation.

### Some Photos from the Event

![Anh](/images/2-Proposal/genaigenai.png)
![Anh](/images/2-Proposal/genai1.png)
![Anh](/images/2-Proposal/genai2.png)
![Anh](/images/2-Proposal/genai3.png)

> Overall, the event not only delivered technical knowledge but also helped reshape my mindset about application design, system modernization, and effective collaboration among teams.
