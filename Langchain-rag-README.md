# LangChain & RAG Learning

A simple learning repository to understand **LangChain** and **RAG
(Retrieval-Augmented Generation)** --- what they are, why they are used,
and how they work.

## What is LangChain?

**LangChain** is an open-source framework for building applications
powered by Large Language Models (LLMs).

It helps connect an LLM with:

-   Prompts
-   Tools and APIs
-   Agents
-   External data
-   Retrieval systems
-   Application logic

### Simple Flow

``` text
User Request
     ↓
LangChain
     ↓
LLM
     ↓
Response
```

With tools:

``` text
User Request
     ↓
LangChain Agent
     ↓
LLM
     ↓
Decides which tool is required
     ↓
Tool / API
     ↓
Tool Result
     ↓
LLM
     ↓
Final Response
```

## Main LangChain Concepts

### LLM

The **Large Language Model** is the reasoning and text-generation
component.

Examples include GPT, Claude, and Gemini.

### Prompt

A prompt contains the instructions and context given to the LLM.

``` text
System Instructions
       +
User Question
       ↓
      LLM
       ↓
    Response
```

### Tools

Tools allow an AI application to interact with external systems.

Examples:

``` text
Calculator
Database
Search API
Calendar API
CRM API
Custom Functions
```

### Agent

An **Agent** uses an LLM to decide what action or tool should be used.

``` text
User Request
     ↓
Agent + LLM
     ↓
"Which tool do I need?"
     ↓
Tool Call
     ↓
Result
     ↓
Final Answer
```

## What is RAG?

**RAG** stands for **Retrieval-Augmented Generation**.

RAG allows an LLM to answer questions using relevant information
retrieved from external knowledge such as:

-   Text files
-   PDFs
-   Documentation
-   Knowledge bases
-   Databases
-   Company information

Instead of relying only on the LLM's existing knowledge, RAG retrieves
relevant information first and gives it to the LLM as context.

## How RAG Works

``` text
Documents
   ↓
Split into Chunks
   ↓
Create Embeddings
   ↓
Store in Vector Store
```

When the user asks a question:

``` text
User Question
      ↓
Create Question Embedding
      ↓
Similarity Search
      ↓
Retrieve Relevant Chunks
      ↓
Send Context + Question to LLM
      ↓
Generate Final Answer
```

### Complete RAG Flow

``` text
Documents → Chunks → Embeddings → Vector Store
                                      ↑
                                      │
User Question → Embedding → Similarity Search
                                      ↓
                              Relevant Knowledge
                                      ↓
                                     LLM
                                      ↓
                                  Final Answer
```

## RAG Components

### 1. Documents

The external knowledge source.

Example:

``` text
company-policy.txt
manual.pdf
documentation.txt
```

### 2. Chunking

Large documents are divided into smaller pieces.

``` text
Large Document
     ↓
Chunk 1
Chunk 2
Chunk 3
Chunk 4
```

This makes retrieval more efficient.

### 3. Embeddings

An embedding model converts text into numerical vectors that represent
its semantic meaning.

``` text
"How do I reset my password?"
             ↓
       Embedding Model
             ↓
      Numerical Vector
```

### 4. Vector Store

A Vector Store stores document embeddings so they can be searched by
meaning.

Examples include:

-   MemoryVectorStore
-   Pinecone
-   Qdrant
-   Chroma
-   pgvector

### 5. Similarity Search

The user's question is also converted into an embedding.

The Vector Store compares it with stored vectors and returns the most
semantically relevant document chunks.

``` text
Question
   ↓
Embedding
   ↓
Compare with stored vectors
   ↓
Most Relevant Chunks
```

### 6. Generation

The retrieved information is provided to the LLM.

``` text
Question
    +
Retrieved Context
    ↓
   LLM
    ↓
Final Answer
```

## Simple RAG Example

Suppose a document contains:

``` text
Employees receive 20 paid leave days each year.
```

User asks:

``` text
How many paid leave days do employees get?
```

RAG flow:

``` text
Question
   ↓
Search Vector Store
   ↓
Retrieve:
"Employees receive 20 paid leave days each year."
   ↓
LLM
   ↓
"Employees receive 20 paid leave days per year."
```

## LangChain + RAG Together

LangChain can manage the different parts of a RAG application.

``` text
                User Question
                      ↓
                  LangChain
                      ↓
                 Retriever
                      ↓
                Vector Store
                      ↓
             Relevant Knowledge
                      ↓
                     LLM
                      ↓
                 Final Answer
```

LangChain can also combine RAG with Agents and Tools:

``` text
                  User
                    ↓
             LangChain Agent
                    ↓
                   LLM
             ┌──────┴──────┐
             ↓             ↓
         RAG Search      Tool / API
             ↓             ↓
         Knowledge        Result
             └──────┬──────┘
                    ↓
                   LLM
                    ↓
             Final Response
```

## LangChain vs RAG

  -----------------------------------------------------------------------
  LangChain                           RAG
  ----------------------------------- -----------------------------------
  Framework                           AI architecture/pattern

  Connects LLMs, tools, agents and    Retrieves external knowledge for an
  retrieval                           LLM

  Used to build AI applications       Used to improve knowledge-grounded
                                      answers

  Can be used without RAG             Can be implemented with or without
                                      LangChain
  -----------------------------------------------------------------------

## Basic Node.js Setup

Install:

``` bash
npm install langchain @langchain/openai dotenv
```

Add to `package.json`:

``` json
{
  "type": "module"
}
```

Create `.env`:

``` env
OPENAI_API_KEY=your_openai_api_key
```

Never commit a real API key to a public repository.

Add `.env` to `.gitignore`:

``` gitignore
node_modules/
.env
```

## Quick Summary

``` text
LLM
= Reasoning and response generation

LangChain
= Framework for connecting LLMs with prompts,
  tools, agents, retrieval and application logic

Agent
= Uses an LLM to decide which action/tool to use

RAG
= Retrieves relevant external knowledge before
  the LLM generates an answer

Embedding
= Numerical representation of semantic meaning

Vector Store
= Stores and searches embeddings

Similarity Search
= Finds knowledge that is semantically closest
  to the user's question
```

## Repository Purpose

This repository is intended for **learning and experimenting with
LangChain and RAG fundamentals** using simple Node.js examples.
