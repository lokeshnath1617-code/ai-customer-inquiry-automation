# Project 8 — Lead Management Automation

## Overview
An n8n workflow that receives lead information through a webhook, validates required fields, stores valid leads in Google Sheets, and sends a Gmail notification.

## Business Problem
Small businesses may receive enquiries through forms or other systems and need a simple way to record leads and notify their team without manually copying information.

## Workflow
1. Receive a POST request through an n8n Webhook.
2. Extract the lead ID, customer name, customer email, and requested service.
3. Validate that the customer name and email are provided.
4. For valid leads:
   - Set the lead status to `New`.
   - Append the lead details to Google Sheets.
   - Send a notification through Gmail.
   - Return a success response.
5. For invalid leads:
   - Set the lead status to `Invalid`.
   - Record an explanatory error detail within the workflow.
   - Return an error response without sending an email or adding a row to the lead sheet.

## Technology Stack
- n8n
- Docker Desktop (local development)
- Webhooks and JSON
- Google Sheets
- Gmail
- HTTP POST requests

## Sample Request — Valid Lead

```json
{
  "lead_id": "LEAD-DEMO-001",
  "customer_name": "Demo Customer",
  "customer_email": "demo@example.com",
  "service_requested": "AI Automation"
}
```

Expected behaviour:
- A row is added to Google Sheets.
- A Gmail notification is sent to the configured recipient.
- A success response is returned.

## Sample Request — Invalid Lead

```json
{
  "lead_id": "LEAD-DEMO-002",
  "customer_name": "Demo Customer",
  "customer_email": "",
  "service_requested": "AI Automation"
}
```

Expected behaviour:
- The lead is rejected by validation.
- Google Sheets and Gmail are skipped.
- An error response explains that the customer name and email are required.

## Setup Instructions
1. Install Docker Desktop and run n8n locally.
2. Import the exported workflow JSON into n8n.
3. Configure the Webhook node and use its Test URL for local testing.
4. Connect a Google Sheets account and select a spreadsheet with the required column headers.
5. Connect a Gmail account and configure the notification recipient.
6. Review node connections and credentials.
7. Execute the workflow and send a POST request with a valid test lead.
8. Send an invalid test lead to verify the validation branch.

Use your own credentials and test data. Never publish OAuth secrets, access tokens, passwords, or private customer information in this repository.

## Testing
The following behaviours were tested during development:
- Valid lead: Google Sheets row creation and Gmail notification succeeded.
- Invalid lead: the validation branch returned the expected error response, while Google Sheets and Gmail were skipped.

These tests confirm the tested paths only; they do not establish that every external-service failure is handled.

## Limitations
- The workflow requires configured Google Sheets and Gmail credentials.
- The current implementation validates the presence of the customer name and email; it does not fully validate email format.
- External-service failures and retry behaviour need further testing and improvement.
- The local n8n instance must be running for local webhook tests.
- The workflow has not yet been established as production-ready.

## Future Improvements
- Add robust error handling and retries.
- Validate email formats and other required fields.
- Add duplicate-lead detection.
- Improve monitoring and failure notifications.
- Add AI-assisted lead classification as a separate enhancement.

## Privacy and Security
Use placeholder data in examples. Keep credentials private and review exported workflow JSON before publishing it.
