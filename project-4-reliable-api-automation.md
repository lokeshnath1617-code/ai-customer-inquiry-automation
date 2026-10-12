# Project 4 — Reliable API Automation

## Overview
This project demonstrates how to build a reliable API automation workflow using n8n.

## Tools Used
- n8n
- HTTP Request node
- Edit Fields (Set) nodes
- IF node
- HTTPBin test API

## What the Workflow Does
1. Sends a GET request to an API endpoint.
2. Sends a demonstration Authorization header.
3. Routes successful requests through a success branch.
4. Handles an HTTP 500 error through the error output.
5. Validates the returned URL using an IF condition.
6. Produces a clear message when validation passes or fails.

## Tests Completed
- API request succeeded.
- HTTP 500 error reached the error-handling node.
- Matching URL followed the true branch.
- Unexpected comparison URL followed the false branch.
- Validation failure message was produced.

## Key Learning
I learned how to send HTTP requests, inspect API responses, configure error handling, preserve response data, and validate API results using conditional logic.

## Important Note
The Authorization header used a fake demonstration token with HTTPBin. This tested sending a header, not authentication against a real secured API.

## Project Status
Core workflow tests completed. Ready for further documentation and portfolio review.
