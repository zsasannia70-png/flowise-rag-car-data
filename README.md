# Car Data Chatflow - Flowise RAG Pipeline

## Abstract
This project implements a Retrieval-Augmented Generation (RAG) pipeline using Flowise. It enables conversational question-answering over PDF documents by extracting, splitting, and embedding the text into an in-memory vector store. This approach allows users or applications to accurately retrieve contextual information from uploaded car data PDFs while maintaining a conversational history for follow-up questions. It holds significant academic and business value by streamlining data extraction from reports, manuals, and specifications without manual searching.

## Architecture
This Flowise RAG workflow combines Several components to achieve reliable document retrieval and conversational QA:

1. **Document Loader**: **PDF File** Loader for importing PDF documents.
2. **Text Splitter**: **Recursive Character Text Splitter** (Chunk Size: 1000, Chunk Overlap: 200) to chunk documents.
3. **Embeddings**: **Google Gemini Embedding** (`gemini-embedding-001`) to vectorize the text chunks.
4. **Vector Store**: **In-Memory Vector Store** for exact, linear search of similar embeddings.
5. **Chat Model**: **MistralAI** (`mistral-tiny` model) acting as the core Language Model.
6. **Memory**: **Buffer Memory** to retain conversational history across prompts.
7. **Chain**: **Conversational Retrieval QA Chain** tying the Vector Store retriever, LLM, and Buffer Memory together to form contextual answers.

## Prerequisites
To run this Flowise chatflow, you will need the following credentials configured in your Flowise instance:
*   **Google Generative AI API Key**: Required for the Gemini Embeddings node (`googleGenerativeAI` credential).
*   **Mistral API Key**: Required for the ChatMistralAI node (`mistralAIApi` credential).

## Installation
1. Ensure you have [Flowise](https://github.com/FlowiseAI/Flowise) installed and running locally or deployed.
2. Open your Flowise dashboard.
3. Click on **Chatflows** in the sidebar.
4. Click the **Add New** button in the top right corner.
5. In the canvas, click the **Settings** gear icon (or "Load Chatflow" button) and select **Load Chatflow**.
6. Select the `Car Data Chatflow.json` file from this repository.
7. Once loaded, click **Save**, resolve any missing credentials (add your Google and Mistral API keys using the Credentials menu), and click **Chat** to interact with the flow.
