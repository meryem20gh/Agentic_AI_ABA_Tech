# Day 9: Security Guard & DB-Aware Threat Detection

This day focuses on security-first agent design by combining prompt-injection detection, smart routing, and database-aware tool use to protect downstream AI workflows.

## Overview

Day 9 introduces a security guard pattern for agentic systems. The workflows use:
- Prompt-injection and jailbreak detection
- Smart routing between safe and unsafe requests
- Groq-based reasoning for classification and justification
- Type conversion and parser components for structured handling
- MongoDB-backed tool integration in the DB variant

The main goal is to detect malicious or unsafe user prompts before they can influence the assistant or trigger unwanted actions.

## Workflow Summary

1. **Chat Input / Prompt Template**
   - Receives the user message and prepares the safety prompt.
2. **Groq Model / Language Model**
   - Evaluates the input for prompt injection, jailbreak, or security-risk behavior.
3. **Smart Router**
   - Routes the message into safe or threat categories based on the analysis.
4. **Parser / Type Converter**
   - Formats and normalizes the output for downstream response generation.
5. **MongoDB Query Tool (DB variant)**
   - Adds database-backed tool support for the more advanced security workflow.
6. **Blocked / Safe Response Path**
   - Produces either a protected response or a refusal message with justification.

## Key Components

- `Prompt Template`: Builds the security and response prompts.
- `Groq Model`: Performs LLM-based safety evaluation.
- `Smart Router`: Classifies requests as `Threat` or `Not a threat`.
- `Parser`: Extracts structured justification or parsed text.
- `Type Converter`: Normalizes data for decision flow.
- `MongoDB Query`: Adds database-access capability in the DB variant.

## Usage

1. Open `Day 9/Agent security.json` for the main security-filter workflow.
2. Open `Day 9/Agent security DB.json` for the database-enabled variant.
3. Configure the required Groq and MongoDB settings.
4. Submit a user message to test detection for prompt injection or unsafe requests.
5. Review the routed response, justification, and any blocked output.

## Notes

- This workflow is useful for building safer copilots, support agents, and internal assistants.
- The security logic is designed to stop prompt-injection attempts before the main agent logic runs.
- The DB variant demonstrates how security-sensitive tools can be combined with persistent data access.

## Files

- `Agent security.json`
- `Agent security DB.json`
