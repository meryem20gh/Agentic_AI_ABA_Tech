# Day 1: Automated Email Sorting Workflow

## Overview
This folder contains the first agentic workflow implementation for the Agentic AI ABA Tech project. The workflow demonstrates automated email classification and sorting using AI-powered agents.

## Contents
- **Automated_email_sorting.json**: A visual workflow definition for automated email processing and categorization

## Workflow Architecture

### Components
The workflow integrates the following components:
- **TextInput**: Receives email content as input
- **GroqModel**: Large Language Model for email understanding and analysis
- **TypeConverter**: Converts message data to structured formats
- **Parser**: Extracts and structures email classification results

## Purpose
This workflow automates the process of:
- Receiving email text input
- Analyzing email content using AI models
- Classifying emails into categories
- Parsing and structuring output for downstream processing

## How to Use
1. Import the JSON file into your agentic workflow platform
2. Configure the GroqModel with your API credentials
3. Provide email text as input through the TextInput component
4. Execute the workflow to get categorized email outputs

## Next Steps
- Customize email categories based on your requirements
- Integrate with email systems (SMTP, IMAP)
- Add persistence layer for storing categorized emails
- Extend workflow with additional processing steps

## Related
See the main [README.md](../README.md) for project overview and other workflows.
