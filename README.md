# AI WhatsApp CRM for Real Estate Agencies

A production-grade WhatsApp CRM built to automate lead qualification, customer conversations, campaign management, and sales workflows for real estate agencies.

The goal of this project is simple: when a lead sends a WhatsApp message, the system should be able to understand the customer's intent, search available properties, answer questions, qualify the lead, maintain conversation context, assist human agents when required, and provide the agency with complete visibility through a CRM.

This project was built as a full-stack system rather than a collection of independent features. Every module is designed to work together—from incoming WhatsApp messages to AI responses, campaign delivery, analytics, and operational dashboards.

---

## Features

### AI Sales Agent

- Understands customer intent
- Extracts property requirements
- Searches matching properties
- Maintains conversation memory
- Qualifies leads automatically
- Hands conversations over to human agents when needed
- Continues conversations within WhatsApp

---

### CRM

- Lead Management
- Opportunity Management
- Property Management
- Smart Lead Qualification
- Conversation History
- Customer Timeline
- AI Generated Lead Summaries

---

### Campaign Management

- Create WhatsApp marketing campaigns
- Import recipients from CRM
- Launch campaigns using Cloud Tasks
- Automatic retry handling
- Delivery tracking
- Read receipts
- Campaign analytics
- Campaign reuse with execution history

---

### WhatsApp Template Management

- Sync templates directly from Meta
- Create templates from the CRM
- Track approval status
- Support for multiple template categories
- Variable detection
- Template preview

---

### Dashboard

The dashboard provides a live overview of the business.

It includes:

- Lead metrics
- Campaign metrics
- Template metrics
- AI usage
- WhatsApp usage
- Delivery metrics
- Estimated AI cost
- Estimated WhatsApp cost
- Credit consumption
- Daily, weekly and monthly analytics

The metrics engine is incremental, meaning statistics are updated whenever an event happens instead of scanning the database repeatedly.

---

## Architecture

```
WhatsApp User
      │
      ▼
WhatsApp Cloud API
      │
      ▼
Webhook
      │
      ▼
Cloud Functions
      │
      ├──────── AI Agent
      │
      ├──────── CRM Updates
      │
      ├──────── Opportunity Engine
      │
      ├──────── Property Search
      │
      ├──────── Campaign Engine
      │
      └──────── Metrics Engine
                │
                ▼
Firestore
      │
      ▼
React CRM Dashboard
```

---

## Tech Stack

### Frontend

- React
- Vite
- Firebase SDK

### Backend

- Firebase Cloud Functions
- Firestore
- Cloud Tasks

### AI

- LangChain
- Groq
- Llama Models

### Messaging

- WhatsApp Cloud API
- Meta Graph API

---

## Campaign Engine

The campaign system is designed for reliability.

Features include:

- Queue-based processing
- Cloud Tasks dispatch
- Automatic retries
- Delivery webhooks
- Read receipts
- Failed message tracking
- Campaign lineage
- Campaign execution history
- Idempotent processing

---

## Metrics Engine

Instead of calculating analytics by scanning Firestore collections, the project maintains incremental metrics.

Whenever an important event happens (lead created, campaign launched, message delivered, template created, AI response generated, etc.), the corresponding counters are updated immediately.

This allows the dashboard to read a handful of documents regardless of database size.

---

## Cost Tracking

The project keeps track of:

- AI token usage
- Estimated AI cost
- WhatsApp messaging cost
- Credit consumption

The goal is to make it easy to build a usage-based billing model without performing expensive calculations later.

---

## Project Structure

```
frontend/
    pages/
    components/
    contexts/
    lib/

functions/
    agent/
    campaigns/
    templates/
    metrics/
    opportunities/
    webhooks/
    cloudTasks/
    whatsapp/
```

---

## Current Status

Implemented

- AI Agent
- CRM
- Opportunities
- Smart Leads
- Properties
- WhatsApp Integration
- Campaign Engine
- Template Management
- Delivery Tracking
- Dashboard
- Metrics Engine
- Credit Tracking
- Cost Tracking

Planned

- Multi-tenancy
- Authentication & Roles
- Subscription Billing
- Admin Portal
- Meta Lead Ads Integration

---

## Why I Built This

Most CRMs treat WhatsApp as just another messaging channel.

I wanted to build something that could actually act like a sales assistant—understanding customer conversations, qualifying leads, helping agents, managing campaigns, and giving agencies visibility into how the business is performing, all from a single system.

This project has also been an opportunity to explore production-oriented system design, including event-driven architecture, background workers, queue processing, incremental analytics, AI integration, and scalable Firebase applications.

---

## License

This repository is intended as a portfolio showcase.

The production version contains additional integrations and configurations that are not included here.
