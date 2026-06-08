# Day 10: HR Assistant

This workflow demonstrates an HR-oriented assistant that combines retrieval, prompt generation, and LLM reasoning to answer employee or policy-related questions from internal knowledge sources.

## Overview

Day 10 introduces an HR assistant pattern built around:
- Chat input for user questions
- Chroma-based retrieval over HR-related content
- Prompt templating for grounded answer generation
- Python-based logic for additional processing
- LLM response generation and chat output

The goal is to provide context-aware answers using stored HR or company knowledge instead of relying only on generic model knowledge.

## Workflow Summary

1. **Chat Input**
   - Receives the employee or HR question from the user.
2. **Chroma Retrieval**
   - Searches stored documents or embeddings for relevant context.
3. **Type Conversion / Parsing**
   - Normalizes retrieved data into the format needed by the next stage.
4. **Prompt Template**
   - Builds a grounded prompt that combines the question with retrieved context.
5. **Python REPL / LLM Processing**
   - Applies logic and generates a final answer using the model.
6. **Chat Output**
   - Returns the assistant response to the user.

## Key Components

- `Chat Input`: Captures the user question.
- `Chroma`: Performs semantic retrieval from stored HR knowledge.
- `Type Converter`: Prepares retrieval output for downstream use.
- `Prompt Template`: Formats the user query with relevant context.
- `Python REPL`: Enables optional logic or post-processing.
- `Language Model / Groq`: Generates the final HR assistant answer.
- `Chat Output`: Displays the final response.

## Usage

1. Open `Day 10/HR assistant.json` in the workflow platform.
2. Configure the retrieval and model components with your credentials.
3. Load or connect the HR/company knowledge source used by Chroma.
4. Ask an HR-related question through the chat input.
5. Review the generated answer grounded in the retrieved context.

## Notes

- This workflow is useful for internal HR Q&A, policy explanation, or employee support assistants.
- Retrieval improves answer grounding and reduces hallucinations from generic model knowledge.
- The workflow can be extended with more structured HR policies, FAQs, and employee documents.

## File

- `HR assistant.json`
