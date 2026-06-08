# Day 8: Structured Data Extraction

This workflow focuses on converting unstructured text into structured, validated JSON output using LLM-based extraction and Pydantic schemas.

## Overview

Day 8 introduces structured extraction patterns that help transform raw input into reliable business data. The workflow combines:
- File input and text loading
- Groq-based language model inference
- Structured output generation with schema guidance
- Pydantic validation for consistent results
- Type conversion for downstream use in other workflows

The goal is to generate clean, machine-readable objects from free-form documents or messages.

## Workflow Summary

1. **Read File / File Input**
   - Loads the source document or text content to analyze.
2. **Groq Model**
   - Uses an LLM to interpret the input and identify structured information.
3. **Structured Output**
   - Applies schema-based extraction to convert the content into JSON-like data.
4. **Pydantic Validation**
   - Ensures the extracted output conforms to the expected fields and data types.
5. **Type Converter**
   - Normalizes the generated data for downstream processing or integration.

## Key Components

- `Read File`: Loads the input text or document.
- `Groq Model`: Produces the extraction reasoning and output.
- `Structured Output`: Formats results into a predefined schema.
- `Pydantic / Schema Validation`: Enforces consistent field structure and types.
- `Type Converter`: Prepares the extracted data for further use.

## Usage

1. Open `Day 8/extraction.json` or `Day 8/extraction pydatic.json` in the workflow platform.
2. Configure the Groq model credentials.
3. Upload or supply the input text/document.
4. Define the output schema if needed.
5. Run the workflow and inspect the structured output.

## Notes

- This workflow is useful for invoice extraction, form parsing, metadata retrieval, and structured summarization.
- Schema-guided extraction improves consistency and reduces invalid output.
- Pydantic-based validation is especially helpful when the extracted structure must be reused in applications or databases.

## Files

- `extraction.json`
- `extraction pydatic.json`
