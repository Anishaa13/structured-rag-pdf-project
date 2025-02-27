
# Streamlit + LangChain PDF Q&A

This repository contains a web application that allows users to upload a PDF document, ask questions about its contents, and receive contextually relevant answers powered by OpenAI's Large Language Models (LLMs). It uses the following key components:

- **LangChain** for text chunking, embeddings, and prompt management.
- **OpenAI** for generating text embeddings (`text-embedding-ada-002`) and answering queries.
- **Chroma** as a vector database to store and retrieve embeddings.
- **Streamlit** for the user interface, where users can:
  1. Provide their personal OpenAI API key.
  2. Upload a PDF.
  3. Enter questions and get real-time answers.

---

## Table of Contents
1. [Features](#features)
2. [Project Structure](#project-structure)
3. [Requirements](#requirements)
4. [Setup and Usage](#setup-and-usage)
    - [Environment Variables](#environment-variables)
5. [How It Works](#how-it-works)
    - [Text Splitting](#text-splitting)
    - [Embedding Generation](#embedding-generation)
    - [Vector Database](#vector-database)
    - [Query & Answer Flow](#query--answer-flow)
6. [Running with Docker](#running-with-docker)
7. [License](#license)
8. [Contact](#contact)

---

## Features
- **PDF Ingestion**: Converts a PDF into structured text chunks.
- **Retrieval-Augmented Generation**: Retrieves the most relevant text chunks for a given query before passing them to an OpenAI model.
- **User-Provided API Key**: Enables secure usage of your own OpenAI API key.
- **Streamlit UI**: A clear and minimal interface for uploading PDFs and asking questions.
- **Optional Structured Output**: Uses Pydantic models to ensure consistent answer formatting.

---

## Project Structure
```
.
├── app.py              # Main Streamlit application (example)
├── requirements.txt    # Python dependencies
├── Dockerfile          # Docker configuration (optional)
├── data/
│   └── example.pdf     # Sample PDF for testing
├── vectorstore_chroma/ # Directory where Chroma DB can persist data
├── .env                # Environment variables (OPENAI_API_KEY, etc.)
└── README.md           # This file
```

---

## Requirements
- Python 3.8+
- [pip](https://pip.pypa.io/en/stable/installation/)
- [Streamlit](https://docs.streamlit.io/)
- [LangChain](https://github.com/hwchase17/langchain)
- [OpenAI Python Client](https://pypi.org/project/openai/)
- [Chroma](https://docs.trychroma.com/)
- [PyPDF2 / pypdf](https://pypdf2.readthedocs.io/en/latest/) (for PDF parsing)
- [python-dotenv](https://pypi.org/project/python-dotenv/)

---

## Setup and Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/username/repo-name.git
   cd repo-name
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   or use a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   # . venv/Scripts/activate  # Windows
   pip install -r requirements.txt
   ```

3. **Environment Variables**
   - Create a file named `.env` in the project root (or wherever your application expects it) with the following content:
     ```bash
     OPENAI_API_KEY=<your-openai-api-key>
     ```
   - Alternatively, you can input your key via the Streamlit UI as the app is configured that way.

4. **Run the Streamlit app**:
   ```bash
   streamlit run app.py
   ```
   
   By default, Streamlit runs on [http://localhost:8501](http://localhost:8501).

---

## How It Works

### Text Splitting
- The PDF is read using `PyPDFLoader` or a similar library.
- The text is split into chunks (e.g., 1500 characters long) using `RecursiveCharacterTextSplitter` to ensure each chunk is small enough for token limits.

### Embedding Generation
- The application uses OpenAI’s `text-embedding-ada-002` model to convert each chunk into a high-dimensional vector.
- This allows semantic searching and similarity scoring.

### Vector Database
- Chunks are stored in a Chroma database, which supports similarity-based searches.
- Duplicate chunks are avoided by generating UUIDs based on their content.
- The database can be persisted locally (`vectorstore_chroma/`) so repeated queries are faster.

### Query & Answer Flow
1. The user enters a query in the Streamlit app.
2. The system retrieves relevant chunks via similarity search against the Chroma DB.
3. These chunks are concatenated into a prompt that is passed to an LLM (e.g., GPT-3.5 or GPT-4).
4. The LLM formulates an answer based on the context. The final answer is displayed to the user.

---

## Running with Docker

1. **Build the Docker image**:
   ```bash
   docker build -t streamlit-app .
   ```

2. **Run the container**:
   ```bash
   docker run -p 8501:8501 streamlit-app
   ```

3. **Open** [http://localhost:8501](http://localhost:8501) in your browser.

```

---

## License
This project is distributed under the [MIT License](LICENSE.md) (or whichever license you choose). Feel free to modify it to suit your needs.

---

## Contact
For questions or feedback, please reach out to:
- **Name**: Anisha Sharma
- **Email**: anishasharma.works@gmail.com

---



## 📜 License
This project is open-source under the **MIT License**.  


