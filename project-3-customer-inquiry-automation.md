# Project 3: AI Customer Inquiry Automation

## Overview
An AI-powered workflow built with n8n to help small businesses process customer inquiries, classify interest, and generate appropriate email replies.

## Business Problem
Small businesses often handle customer inquiries manually. This can take time and make it harder to respond consistently, especially when information is incomplete.

## Solution
I built an automation that receives customer inquiries through a webhook, validates the required information, uses AI to classify the inquiry, generates an appropriate response, and sends the response through Gmail.

## Workflow
1. Receive customer information through a webhook.
2. Extract the customer's name, email, and message.
3. Validate that the required fields are present.
4. Use AI to classify the inquiry as interested or not interested.
5. Generate a suitable professional reply.
6. Send the reply through Gmail.
7. Merge the branch results and record a final status.
8. Route incomplete inquiries to a validation-status output without sending them through the AI and Gmail branches.

## Technologies Used
- n8n
- Webhooks and HTTP requests
- AI with Ollama
- Gmail integration
- Conditional logic
- JSON data
- Input validation

## Testing
- Tested an interested-customer inquiry successfully.
- Verified that AI generated a professional reply.
- Confirmed that Gmail sent the reply.
- Tested an inquiry with a missing message.
- Verified that the invalid inquiry followed the validation branch.

## Skills Demonstrated
- Workflow design
- API and webhook concepts
- Data extraction and mapping
- AI integration
- Conditional branching
- Input validation
- Email automation
- End-to-end testing

## Project Status
Built and tested as a local demonstration project.

## Future Improvements
- Add clearer error handling for AI or Gmail failures.
- Add secure deployment and production configuration.
- Store inquiry results in a database or spreadsheet.
- Add stronger email validation and duplicate-inquiry handling.
- Test additional edge cases before client deployment.
