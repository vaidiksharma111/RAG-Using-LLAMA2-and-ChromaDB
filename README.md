# Customer Support Chatbot using LLaMA 2 and ChromaDB

## Introduction
This project implements a customer support chatbot using the LLaMA 2 model for generating responses and ChromaDB for storing and retrieving customer support interactions. The chatbot is designed to provide accurate and contextual responses by leveraging past customer interactions and the LLAMA 2 language model.

## Features
- Utilizes the LLaMA 2 model from Hugging Face for generating responses.
- Uses ChromaDB for efficient vector-based retrieval of customer support data.
- Integrates Sentence Transformers for embedding queries.
- Provides contextual responses by combining similar past interactions with recent queries.
- Supports conversational continuity using a cache of recent interactions.
- Deploys as a Flask-based web application, accessible via ngrok.

## Prerequisites
- Python 3.8+
- CUDA-compatible GPU (for optimal performance)
- Libraries: 
  - transformers
  - sentence-transformers
  - chromadb
  - datasets
  - accelerate
  - faiss-cpu
  - torch
  - huggingface_hub
  - flask
  - flask-ngrok
  - pyngrok

## Installation
1. Install the required packages:
   ```bash
   pip install transformers sentence-transformers chromadb datasets accelerate faiss-cpu torch huggingface_hub flask flask-ngrok pyngrok
   ```

2. Set your Hugging Face token:
   ```bash
   export HF_TOKEN=your_huggingface_token
   ```

3. Set your ngrok authentication token:
   ```bash
   export NGROK_AUTH_TOKEN=your_ngrok_token
   ```

## Running the Application
1. Start the Flask server with ngrok:
   ```bash
   python RAG_using_LLama2_Chromadb.py
   ```

2. Access the application via the public URL printed in the terminal.

## API Usage
Send a POST request to the endpoint to get a response:
```
POST /generate_response
{
    "query": "Your customer query here"
}
```

## Example Response
```
{
    "response": "Here is the support answer."
    "retrieved_documents": [ 
{"query": "Also double charged for checked…", "response": "Follow these steps...", "bleu_score":9.92e-232,  
"bert_score": 1.23
...
]
}
```

## Notes
- The chatbot maintains a cache of the last 5 interactions for contextual continuity.
- It leverages past queries and responses to generate relevant answers.
- If the chatbot cannot find relevant information, it will indicate so.
