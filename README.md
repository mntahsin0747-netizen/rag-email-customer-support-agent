# RAG Email Customer Support Agent

An AI-powered email customer support automation built with **n8n, RAG, Supabase Vector Store, Hugging Face Embeddings, Groq, and Gmail**.

## 📌 Overview

This project automates repetitive customer support email handling using a **Retrieval-Augmented Generation (RAG)** architecture.

When a customer sends an email, the workflow:

1. Detects the incoming email through Gmail
2. Extracts and cleans the customer message
3. Retrieves relevant information from the company knowledge base
4. Generates a grounded AI response
5. Sends the draft for human approval
6. Sends the approved response back to the customer
7. Routes rejected responses for manual review

The system is designed to reduce repetitive support work while maintaining **human oversight before sending AI-generated responses**.

## 🎯 Business Problem

Customer support teams often spend significant time answering repetitive questions about:

* Shipping
* Returns & refunds
* Payment methods
* Order tracking
* Order cancellation
* Warranty
* Account issues

This automation handles these repetitive queries using a company knowledge base while keeping a **human-in-the-loop approval step** for reliability.

## 🏗️ Workflow Architecture

```text
Customer Email
      ↓
Gmail Trigger
      ↓
Extract & Clean Email
      ↓
RAG Knowledge Retrieval
      ↓
AI Customer Support Agent
      ↓
Human Approval
      ↓
   ┌───────────────┐
   │               │
Approved        Rejected
   │               │
   ↓               ↓
Send Gmail      Manual Review
   │
   ↓
Customer
```

## ⚙️ Key Features

* Automatic Gmail email detection
* Email content extraction and cleaning
* RAG-based knowledge retrieval
* Supabase Vector Store integration
* Hugging Face embeddings
* AI-generated customer support responses
* Human-in-the-loop approval
* Automatic Gmail response after approval
* Manual review routing for rejected drafts
* Grounded responses to reduce hallucination

## 🧠 RAG Pipeline

The system uses a company knowledge base containing support policies and procedures.

The knowledge pipeline:

1. Loads company knowledge
2. Splits the content into smaller chunks
3. Generates embeddings
4. Stores the embeddings in Supabase Vector Store
5. Retrieves relevant knowledge when a customer email arrives
6. Provides the retrieved context to the AI agent

The workflow uses a **400-character chunk size with 40-character overlap** for document splitting.

## 🤖 AI Customer Support Agent

The AI agent generates customer responses using the retrieved knowledge-base context.

The agent is instructed to:

* Use only information available in the retrieved context
* Avoid inventing policies, prices, timelines, or other facts
* Escalate when sufficient information is unavailable
* Keep responses warm, professional, and concise
* Address the customer appropriately

## 👤 Human-in-the-Loop

Before an AI-generated response is sent to the customer, the draft is submitted for human approval.

```text
AI Draft
   ↓
Human Review
   ↓
Approved?
   ├── Yes → Send Gmail Reply
   │
   └── No → Manual Review
```

This provides an additional reliability layer and prevents an AI-generated response from being automatically sent without human verification.

## 🛠️ Tech Stack

* **n8n** — Workflow automation
* **RAG** — Knowledge-grounded generation
* **Supabase Vector Store** — Vector storage and retrieval
* **Hugging Face** — Text embeddings
* **Groq** — LLM inference
* **Gmail** — Email trigger, approval, and response

## 🔑 Key Concepts Demonstrated

* AI Agents
* Retrieval-Augmented Generation (RAG)
* Vector Databases
* Semantic Knowledge Retrieval
* LLM-powered Email Automation
* Human-in-the-Loop AI
* Workflow Automation
* Prompt Engineering
* API & Tool Integration

## 📌 Project Outcome

The workflow demonstrates how a business can combine **RAG + AI Agents + workflow automation + human approval** to automate repetitive customer support communication while keeping responses grounded in company-provided information.

