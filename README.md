# AI Customer Support Ticket Automation

## Project Overview

This project automates the customer support ticket management process using AI and workflow automation.

When a customer sends an email, the automation captures the incoming message, uses Groq AI to categorize the support issue, creates a structured support ticket in Airtable, notifies the support team through Slack, and sends an acknowledgement email to the customer.

A second automation monitors ticket status changes in Airtable. When a support ticket is marked as **Resolved**, the system automatically sends a resolution email to the customer.
## Problem Statement

Traditional customer support processes often require support teams to manually review incoming emails, identify the type of issue, create support tickets, notify the appropriate team members, and send acknowledgement messages to customers.

This manual process can lead to:

* Delayed ticket creation
* Inconsistent issue categorization
* Missed or delayed team notifications
* Repetitive manual email responses
* Lack of a structured ticket tracking process
* Additional effort when notifying customers after resolution

## Solution

This project uses **Make** and **Groq AI** to automate the customer support workflow from email intake to ticket resolution.

When a customer sends an email, the system automatically processes the message using Groq AI to categorize the issue, creates a structured ticket in Airtable, sends a notification to the support team through Slack, and sends an acknowledgement email to the customer.

A separate workflow monitors Airtable for status changes. When a manager marks a ticket as **Resolved**, the automation detects the change and sends a resolution email to the customer.

This reduces repetitive manual work and creates a consistent workflow for handling customer support requests from **initial enquiry through resolution**.


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
* ## Key Features

* **AI-Powered Issue Categorization**
  Uses Groq AI to analyze incoming customer emails and categorize support issues automatically.

* **Automated Ticket Creation**
  Creates a structured support ticket in Airtable from the incoming customer email.

* **Real-Time Support Team Notification**
  Sends a Slack notification to the support team when a new ticket is created.

* **Automated Customer Acknowledgement**
  Sends an acknowledgement email to the customer after the support ticket is created.

* **Ticket Status Monitoring**
  Monitors Airtable records for changes to the support ticket status.

* **Automated Resolution Email**
  When a manager changes the ticket status to **Resolved**, the system automatically sends a resolution email to the customer.

* **Two-Scenario Automation Architecture**
  Separates ticket creation and resolution handling into two independent Make scenarios for easier management and maintenance.

* **Gmail** - Customer email processing and notifications
* **Groq AI** - AI-powered support issue categorization
* ## Testing & Validation

The automation was tested using sample customer support emails and Airtable status updates to validate the complete workflow.

### Scenario 1: Ticket Creation & Acknowledgement

| Test                                  | Expected Result                                    | Status   |
| ------------------------------------- | -------------------------------------------------- | -------- |
| Send a sample customer email to Gmail | Email is detected by the workflow                  | ✅ Passed |
| Process the email with Groq AI        | Support issue is categorized                       | ✅ Passed |
| Create the Airtable ticket            | Ticket record is created with the required details | ✅ Passed |
| Send Slack notification               | Support team receives the new ticket notification  | ✅ Passed |
| Send acknowledgement email            | Customer receives an acknowledgement email         | ✅ Passed |

### Scenario 2: Ticket Resolution

| Test                               | Expected Result                                     | Status   |
| ---------------------------------- | --------------------------------------------------- | -------- |
| Update ticket status to `Resolved` | Airtable detects the record update                  | ✅ Passed |
| Apply `Status = Resolved` filter   | Only resolved tickets continue through the workflow | ✅ Passed |
| Send resolution email              | Customer receives the resolution email              | ✅ Passed |

### Validation

The workflow was validated by checking:

* Successful email detection from Gmail
* Correct AI categorization output
* Successful Airtable record creation
* Correct Slack notification delivery
* Successful acknowledgement email delivery
* Correct detection of the `Resolved` status
* Successful resolution email delivery

These tests confirmed that both automation scenarios performed their intended actions from **customer enquiry through ticket resolution**.

* **Airtable** - Support ticket database and status tracking
* **Slack** - Support team notifications

