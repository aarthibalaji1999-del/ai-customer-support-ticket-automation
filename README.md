# AI Customer Support Ticket Automation

## Project Overview

This project automates the customer support ticket management process using AI and workflow automation.

When a customer sends an email, the automation captures the incoming message, uses Groq AI to categorize the support issue, creates a structured support ticket in Airtable, notifies the support team through Slack, and sends an acknowledgement email to the customer.

A second automation monitors ticket status changes in Airtable. When a support ticket is marked as **Resolved**, the system automatically sends a resolution email to the customer.

### Workflow

**Scenario 1: Ticket Creation & Acknowledgement**

```text
Customer sends an email
        ↓
Gmail - Watch Emails
        ↓
Groq AI - Create Chat Completion
        ↓
Airtable - Create Record
        ↓
Slack - Create Message
        ↓
Gmail - Send Acknowledgement Email
```

**Scenario 2: Resolution Notification**

```text
Manager updates Status = Resolved
        ↓
Airtable - Watch Records
        ↓
Filter - Status = Resolved
        ↓
Gmail - Send Resolution Email
```

### Node Structure

#### Scenario 1

1. Gmail - Watch Emails
2. Groq AI - Create Chat Completion
3. Airtable - Create Record
4. Slack - Create Message
5. Gmail - Send Acknowledgement Email

#### Scenario 2

1. Airtable - Watch Records
2. Filter - Status = Resolved
3. Gmail - Send Resolution Email

### Tech Stack

* **Make** - Workflow automation platform
* **Gmail** - Customer email processing and notifications
* **Groq AI** - AI-powered support issue categorization
* **Airtable** - Support ticket database and status tracking
* **Slack** - Support team notifications

