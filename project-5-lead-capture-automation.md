# Project 5: Lead Capture and Follow-up Automation

## Overview
This project automates lead capture and validates incoming lead information using n8n. Valid leads receive a personalized follow-up message prepared automatically.

## Tools Used
- n8n
- Webhook
- Edit Fields
- IF node
- Gmail integration (configured, but deactivated during testing)

## Workflow
Webhook → Edit Fields → IF (validate lead) → Prepare Follow-up → Gmail

The invalid branch routes to an Invalid Lead node when required information is missing.

## How It Works
1. The Webhook receives lead information through a POST request.
2. Edit Fields extracts the lead's name, email, and interest.
3. The IF node checks whether the name and email are present.
4. Valid leads continue to Prepare Follow-up, which creates a personalized message.
5. Invalid leads are routed to the Invalid Lead node.
6. The Gmail node is intended to send the follow-up message after the email step is safely verified.

## Testing
- **Invalid lead:** A request missing the email field successfully reached the Invalid Lead branch.
- **Valid lead:** A test request containing a name, email, and interest followed the true branch and reached Prepare Follow-up.
- **Message verification:** The generated follow-up message matched the expected text.
- **Email sending:** Gmail remained deactivated during testing. Successful delivery of an email has not yet been verified.

## Example Follow-up Message
Hi Test Lead, thank you for your interest in AI Automation! We received your inquiry and will follow up with you soon.

## Skills Practiced
- Webhook-based automation
- Receiving and mapping JSON data
- Conditional validation
- Creating personalized messages with expressions
- Testing valid and invalid inputs
- Preventing unintended email sends during testing

## Current Status
The lead-capture, validation, and follow-up message preparation paths have been tested successfully. Gmail delivery and final portfolio export remain to be completed.

## Future Improvements
- Safely test email delivery using a controlled recipient.
- Add clearer error handling and logging.
- Publish a sanitized workflow JSON without personal credentials or private identifiers.
                                                                                                                                                    