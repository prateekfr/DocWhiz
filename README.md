# DocWhiz - Intelligent Document-Based Chatbot

## Overview

**DocWhiz** is an AI-powered chatbot designed to help users interact with their documents in a more intuitive and efficient way. Simply upload a document and ask questions — DocWhiz will extract relevant content and provide responses strictly based on the data within your file. It supports multiple document formats, uses advanced embedding techniques, and integrates with Google's Gemini API for natural language understanding.

Unlike general-purpose chatbots, DocWhiz is focused entirely on the contents of your uploaded files — it never fabricates answers and ensures high accuracy by referencing only the embedded data.

## Key Features

- **Multi-format Support**: Accepts PDF, DOCX, TXT, CSV, XLSX, and PPTX files
- **Smart Text Retrieval**: Powered by FAISS for fast and relevant chunk retrieval
- **Efficient Embeddings**: Uses `sentence-transformers/all-MiniLM-L6-v2` for dense vector representations
- **AI-Powered Responses**: Integrates Google’s Gemini API for contextual answers
- **User-Friendly Interface**: Built with Streamlit for seamless interaction
- **Strictly Document-Based**: Ensures all responses are grounded in your uploaded content

## How It Works

1. **Upload Document**: Users upload their document through the Streamlit interface.
2. **Text Extraction**: DocWhiz processes and extracts readable text from the document.
3. **Chunking and Embedding**: Extracted text is split into logical chunks and embedded into vector space.
4. **FAISS Storage**: Embedded vectors are indexed using FAISS for quick similarity search.
5. **User Query**: Users submit a question via the chat interface.
6. **Relevant Content Retrieval**: DocWhiz finds the most relevant chunks using vector similarity.
7. **Answer Generation**: Gemini API crafts a response based only on the retrieved chunks.
8. **Response Display**: The final answer is shown in the Streamlit chat interface.

## Installation Guide

### Step 1: Clone the Repository

```bash
git clone https://github.com/prateekfr/DocWhiz.git
cd DocWhiz
```

### Step 2: Create a Virtual Environment

```bash
conda create -n venvdoc python==3.10.10 -y 
```

### Step 2: Activate Virtual Environment

```bash
conda activate venvdoc
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables

Create a `.env` file in the project root and add your Google API key:

```
GOOGLE_API_KEY=your_api_key_here
```

## Usage

### 1. Start the Streamlit App

```bash
streamlit run app.py
```

### 2. Upload Documents

- Use the sidebar to upload a document.
- The system will extract, embed, and store the text in FAISS.

### 3. Ask Questions

- Enter a query related to the uploaded document.
- The chatbot retrieves relevant document chunks and queries Gemini for a response.

## Project Structure

```
askmydoc/
├── faiss_vectorstore/          # FAISS database storage
├── document_loader.py          # Handles document text extraction
├── text_enbedding.py           # Chunks and embeds text into FAISS
├── main.py                     # FAISS retrieval + Gemini API call
├── streamlit.py                # Streamlit UI for chatbot
├── requirements.txt            # Required Python packages
├── .env.example                # Example .env file for API keys
└── README.md                   # Project documentation
```