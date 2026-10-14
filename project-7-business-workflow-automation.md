# Project 7 — Business Workflow Automation

## Overview
This n8n workflow receives customer inquiries through a webhook, validates required customer details, and prepares a structured inquiry summary for valid submissions.

## Workflow
Webhook → Edit Fields (Prepare Inquiry Data) → IF (Validate Inquiry)

### Valid Inquiry Path
When the customer name and email are present:
- Status: `Valid inquiry — ready for processing`
- Creates an inquiry summary containing the customer name, email, and requested service.

### Invalid Inquiry Path
When the customer name or email is missing:
- Status: `Invalid inquiry — customer name or email is missing`
- Action required: `Request the missing customer details`

## Testing
- Valid inquiry: Tested successfully; the True branch executed and produced the expected fields.
- Missing email: Tested successfully; the Invalid Inquiry branch executed and produced the expected output.

## Tools
- n8n
- Webhook
- Edit Fields
- IF node
- HTTP POST requests with JSON

## Limitations
This is a portfolio demonstration. It validates and structures inquiries but does not yet send notifications or store customer data in an external system.