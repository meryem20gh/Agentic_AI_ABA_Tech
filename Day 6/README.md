# Day 6: RAG-Powered Legal Document Assistant

This workflow demonstrates a Retrieval-Augmented Generation (RAG) pipeline for legal document analysis and question answering.

## Overview

Day 6 introduces a vector search workflow that combines:
- Document ingestion from uploaded files
- Text chunking for semantic indexing
- Embedding generation with Google Generative AI
- Vector storage and retrieval via Chroma DB
- Prompt construction for a legal AI assistant
- Answer generation using the Groq model

The result is a context-aware assistant that answers legal questions using only the information found in the provided documents.

## Workflow Summary

1. **Read File**
   - Loads an uploaded legal document and returns its raw text.
2. **Split Text**
   - Splits the document into chunks for better retrieval and semantic search.
3. **Google Generative AI Embeddings**
   - Converts text chunks into dense embeddings.
4. **Chroma DB**
   - Stores embeddings and serves as the vector search index.
5. **Chat Input**
   - Accepts a user question through the playground interface.
6. **Retrieval Query**
   - The user message is sent to Chroma DB as a search query.
7. **Prompt Template**
   - Builds a legal assistant prompt using the retrieved context and the user question.
   - The prompt enforces strict instructions to answer only from the provided document and to remain formal and neutral.
8. **Groq Model**
   - Generates the final answer based on the assembled legal context.
9. **Type Convert + Chat Output**
   - Ensures the generated text is converted into a message and displayed in the chat output.

## Key Components

- `Read File`: Imports the input document content.
- `Split Text`: Splits long documents into retrievable chunks.
- `Google Generative AI Embeddings`: Creates vector embeddings for semantic search.
- `Chroma DB`: Vector store for semantic retrieval.
- `Prompt Template`: Defines a legal assistant prompt with strict response rules.
- `Groq`: Language model for answer generation.
- `Chat Output`: Displays the response back to the user.

## Usage

1. Open `Day 6/j6-RAG.json` in the workflow platform.
2. Upload the legal document you want to analyze.
3. Run the pipeline.
4. Enter a legal question through `Chat Input`.
5. Review the generated answer in `Chat Output`.

## Notes

- The prompt is designed to avoid hallucinations by instructing the assistant to use only the provided context.
- This workflow is ideal for legal Q&A, contract analysis, and regulatory document review.
- Configure your Google Generative AI API key and Chroma DB persistence before running the workflow.

## File

- `j6-RAG.json`
