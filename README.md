# Research Assistant Workflow

This repository documents an automated **Research Assistant workflow** built using **n8n**. The workflow accepts a user query, performs AI-assisted reasoning with optional web search, and produces a **PDF report** as output.

---

## Overview

The workflow is designed to:

1. Receive a chat/query from a user
2. Process the query using an AI Agent powered by Google Gemini
3. Optionally enrich responses with real-time web search via Tavily
4. Convert the AI-generated response into HTML
5. Export the final result as a PDF document

This setup is suitable for research summaries, reports, insights generation, and automated document creation.

---

## Workflow Architecture

The workflow consists of the following nodes, executed sequentially:

### 1. When Chat Message Received

**Type:** Trigger Node

* Entry point of the workflow
* Activates when a user sends a chat message
* Passes the user query to the AI Agent

---

### 2. AI Agent

**Type:** AI Agent Node

* Core reasoning and response generation component
* Uses a conversational LLM to interpret the user query
* Supports tool usage and memory

**Connected Components:**

* **Chat Model:** Google Gemini Chat Model
* **Memory:** Simple Memory (for short-term conversational context)
* **Tool:** Tavily Search (optional web research)

---

### 3. Google Gemini Chat Model

**Type:** Chat Model

* Provides natural language understanding and generation
* Responsible for producing structured, high-quality responses
* Handles reasoning, summarization, and report-style outputs

---

### 4. Simple Memory

**Type:** Memory Node

* Stores short-term conversation context
* Enables continuity across multiple user messages
* Improves coherence and follow-up responses

---

### 5. Search in Tavily

**Type:** Tool / Search Node

* Performs real-time web searches when invoked by the AI Agent
* Used for factual verification, current information, or research enrichment
* Returns search results to the AI Agent for synthesis

---

### 6. Convert to HTML

**Type:** Markdown to HTML

* Converts the AI Agent’s Markdown-formatted output into HTML
* Ensures structured formatting for document generation
* Preserves headings, lists, and emphasis

---

### 7. Convert to PDF

**Type:** Convert to Text File (PDF)

* Transforms the generated HTML into a PDF document
* Final deliverable for the user
* Suitable for sharing, printing, or archiving

---

## Data Flow Summary

1. User sends a chat message
2. AI Agent processes the request using Gemini
3. Tavily Search is used if external data is required
4. Response is generated in Markdown format
5. Markdown is converted to HTML
6. HTML is exported as a PDF

---

## Use Cases

* Automated research reports
* AI-powered document generation
* Knowledge assistant with PDF export
* Research summaries with live web data

---

## Requirements

* n8n (self-hosted or cloud)
* Google Gemini API credentials
* Tavily API key (optional but recommended)
* PDF conversion support enabled in n8n

---

## Notes

* The workflow is modular and can be extended with additional tools (e.g., database lookup, email delivery, cloud storage upload).
* Prompt engineering within the AI Agent node significantly affects output quality.

---

## License

This project is provided for educational and experimental purposes. Add your preferred license before publishing.



