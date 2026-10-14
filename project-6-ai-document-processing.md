# Project 6: AI Document Processing Automation

## Overview
This project uses n8n and a local Ollama language model to analyze document text, extract key information, and return a structured summary. It also validates input so empty documents are handled safely.

## Tools Used
- n8n
- Webhook
- Edit Fields
- IF node
- Ollama 3.2

## Workflow
Webhook → Edit Fields → IF

- **True branch:** Ollama → Document Summary
- **False branch:** Invalid Document

## How It Works
1. The Webhook receives a POST request containing `document_text`.
2. Edit Fields extracts the incoming document text.
3. The IF node checks whether the document text is empty.
4. If text is present, Ollama analyzes it and extracts the main topic, key points, dates or deadlines, and action items.
5. Document Summary adds a success status while preserving the AI response.
6. If the document text is empty, the Invalid Document node returns a clear status message.

## Testing
### Valid document
A sample project meeting document was submitted through the webhook. The full workflow executed successfully through Ollama and Document Summary. The expected success status and AI-generated analysis were present in the output.

### Empty document
A request with an empty `document_text` was submitted. The workflow routed to the Invalid Document branch and returned the configured validation message.

## Skills Practiced
- Webhook-based automation
- JSON input handling
- Input validation and conditional routing
- Local AI integration using Ollama
- Prompt design for information extraction
- End-to-end workflow testing
- Error and invalid-input handling

## Limitations
- The workflow currently accepts document text in a JSON request; it does not directly upload or parse PDF or Word files.
- AI-generated summaries should be reviewed for accuracy before being used for important decisions.
- This project was tested locally; public deployment and production security have not been configured.

## Current Status
The valid-document and empty-document paths have both been tested successfully. The documentation is ready for portfolio preparation