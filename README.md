# RAG Email Customer Support Agent

An AI-powered email customer support automation built with n8n, RAG, Supabase Vector Store, Groq, Hugging Face Embeddings, and Gmail.

## 📌 Overview

This project automates repetitive customer support email handling using a Retrieval-Augmented Generation (RAG) architecture.

Incoming customer emails are analyzed, relevant information is retrieved from a company knowledge base, and an AI agent generates a grounded response.

A human approval step is included before the response is sent to the customer.

## 🎯 Business Problem

Customer support teams often spend significant time answering repetitive questions related to:

- Shipping
- Returns & refunds
- Payment methods
- Order tracking
- Order cancellation
- Warranty
- Account issues

This workflow automates these repetitive interactions while keeping human oversight for reliability.

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
 Approved       Rejected
   │               │
   ↓               ↓
Send Reply     Manual Review
   │
   ↓
Customer
      ↓
Customer

## ⚙️ Key Features

- Automatic Gmail email detection
- Email content extraction and cleaning
- RAG-based knowledge retrieval
- Supabase Vector Store integration
- AI-generated customer responses
- Human-in-the-loop approval
- Automatic Gmail response after approval
- Manual review logging
- Grounded AI responses to reduce hallucination

## 🧠 RAG Pipeline

The knowledge base contains company policies and procedures.

The workflow:

1. Loads company knowledge
2. Splits the text into smaller chunks
3. Generates embeddings
4. Stores embeddings in Supabase Vector Store
5. Retrieves relevant information when a customer email arrives
6. Provides retrieved context to the AI agent

## 🤖 AI Agent

The AI agent generates customer responses using the retrieved knowledge-base context.

The agent is instructed to:

- Use only information available in the retrieved context
- Avoid inventing policies, prices, or timelines
- Escalate when sufficient information is unavailable
- Keep responses professional and concise

## 👤 Human-in-the-Loop

Before a response is sent automatically, the generated draft is sent for human approval.

```text
AI Draft
   ↓
Human Review
   ↓
Approved?
   ├── Yes → Send Gmail Reply
   │
   └── No → Manual Review Log
