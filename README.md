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
