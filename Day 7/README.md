# Day 7: Hybrid RAG Retrieval

This workflow extends the RAG pattern by combining semantic retrieval with lexical ranking to produce a stronger and more reliable context for answer generation.

## Overview

Day 7 introduces a hybrid retrieval pipeline that improves document selection before the final response is produced. The workflow combines:
- Document ingestion and chunking
- Embedding generation with Google Generative AI
- Vector search in Chroma DB
- BM25-style keyword ranking
- Reciprocal Rank Fusion (RRF) to merge both retrieval signals
- Final answer generation with the Groq model

The result is a more robust RAG assistant that can retrieve relevant context even when the user query uses different wording from the source document.

## Workflow Summary

1. **Read File**
   - Loads the source document that will be used as retrieval context.
2. **Split Text**
   - Divides the document into smaller passages for indexing.
3. **Google Generative AI Embeddings**
   - Creates vector embeddings for semantic retrieval.
4. **Chroma DB**
   - Stores the chunks and supports similarity-based search.
5. **Hybrid Fusion Logic**
   - Uses Python-based RRF logic to combine semantic and keyword-based results.
6. **Prompt Template + Groq Model**
   - Builds the final answer using the most relevant merged context.
7. **Chat Output**
   - Returns the final response to the user in the chat interface.

## Key Components

- `Read File`: Loads the document content.
- `Split Text`: Creates retrievable chunks.
- `Google Generative AI Embeddings`: Generates vector representations.
- `Chroma DB`: Stores embeddings and performs similarity search.
- `Python Interpreter`: Executes the hybrid ranking logic (BM25 + RRF).
- `Prompt Template`: Formats the retrieved context into a final answer prompt.
- `Groq Model`: Produces the final generated response.

## Usage

1. Open `Day 7/j7-RAG hybrid (2).json` in the workflow platform.
2. Configure the embedding, Chroma DB, and Groq credentials.
3. Load the document to index.
4. Ask a question through the chat input.
5. Review the final answer generated from the hybrid retrieved context.

## Notes

- This workflow is ideal for improving retrieval quality in domain-specific Q&A systems.
- Hybrid retrieval usually performs better than pure semantic search in noisy or keyword-heavy documents.
- The fusion logic is designed to make retrieval more stable and more context-aware.

## File

- `j7-RAG hybrid (2).json`
