# RAG System with LangChain, OpenAI, and ChromaDB

This project demonstrates the creation of a Retrieval-Augmented Generation (RAG) system, leveraging LangChain, OpenAI’s embedding models, and ChromaDB for efficient data retrieval. The system is designed to extract data from documents, create embeddings, store them in a ChromaDB database, and use these embeddings for efficient information retrieval during the question-answering process.

## Project Structure

The project is divided into three main steps, implemented in the following notebooks:

### 1. **PDF Text Extraction** (`0_PDF_text_extractor.ipynb`)
   - **Objective**: Extract text from PDF files using various Python libraries.
   - **Libraries used**:
     - `PyPDF2`
     - `pdfplumber`
     - `PyMuPDF`
   - **Key Functions**:
     - Text extraction from PDFs using three different libraries.
     - This notebook provides functions for extracting text using `PyPDF2`, `pdfplumber`, and `fitz` (PyMuPDF), offering multiple extraction methods to handle different types of PDFs.
   
### 2. **Creating Chroma Database** (`1_Creating_Chroma_database.ipynb`)
   - **Objective**: Create a vector database using OpenAI's text embedding models and store the embeddings in ChromaDB.
   - **Libraries used**:
     - `langchain_community`
     - `langchain_chroma`
     - `langchain_openai`
   - **Key Steps**:
     - Loading text documents from a specified directory using `TextLoader` and `DirectoryLoader`.
     - Splitting text into chunks using `CharacterTextSplitter` or `RecursiveCharacterTextSplitter` for better performance in vector search.
     - Using OpenAI's embedding models (`text-embedding-3-small`) to generate document embeddings.
     - Storing these embeddings into a ChromaDB vector database for future retrieval.

### 3. **Retrieving from Local Database** (`2_Retrieve_from_local_Database.ipynb`)
   - **Objective**: Retrieve relevant text chunks from ChromaDB and use them to answer questions.
   - **Libraries used**:
     - `langchain_chroma`
     - `langchain_openai`
     - `langchain`
   - **Key Steps**:
     - Initializing a `Chroma` object and loading the stored embeddings.
     - Performing vector searches to retrieve relevant text chunks based on a query.
     - Using `RetrievalQA` from LangChain to combine the retrieved information with OpenAI’s LLMs, generating accurate responses based on previously unseen data.

## Requirements

To run this project, you will need the following Python libraries:

```bash
pip install PyPDF2 pdfplumber pymupdf pdfminer langchain_community langchain_chroma langchain_openai langchain
```

Additionally, ensure you have an OpenAI API key to access the embedding models and LLMs. The key should be set as an environment variable before running the notebooks.

## Usage

1. **Extract text from PDFs**: Use the `0_PDF_text_extractor.ipynb` to extract text from your PDF files using any of the supported libraries.
2. **Create a ChromaDB vector database**: Run `1_Creating_Chroma_database.ipynb` to load documents, generate embeddings, and store them in ChromaDB.
3. **Retrieve and answer questions**: Finally, use `2_Retrieve_from_local_Database.ipynb` to query the stored embeddings and generate responses using a LangChain-powered retrieval system.

## Future Work

- Extend the system to handle more file formats (e.g., Word documents, CSVs).
- Experiment with different OpenAI embedding models to improve the retrieval accuracy.
- Add error handling and optimizations for large-scale document databases.
