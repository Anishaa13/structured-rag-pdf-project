```markdown
# 📄 Structured RAG for PDFs

## 🚀 Project Overview
This project implements **Retrieval-Augmented Generation (RAG) for structured PDFs**, enabling efficient information retrieval and intelligent document querying using **LangChain, ChromaDB, and OpenAI embeddings**.

### ✨ Features:
- **PDF Parsing**: Extract structured text from PDFs using `PyPDFLoader`
- **Text Chunking**: Process and segment text with `RecursiveCharacterTextSplitter`
- **Vector Search**: Store and retrieve embeddings efficiently using **ChromaDB**
- **LLM Integration**: Query documents dynamically using `ChatOpenAI`
- **Interactive UI**: Built with **Streamlit** for seamless exploration

---

## 📂 Dataset & Sources
The project works with **any structured PDF documents**. You can upload PDFs and interactively query them using natural language.

---

## 🔧 Installation & Setup

### 1️⃣ Clone the Repository  
```bash
git clone https://github.com/Anishaa13/structured-rag-pdf-project.git
cd structured-rag-pdf-project
```

### 2️⃣ Install Dependencies  
```bash
pip install -r requirements.txt
```

### 3️⃣ Set Up Environment Variables  
Create a `.env` file in the root directory and add:  
```plaintext
OPENAI_API_KEY=your_openai_api_key_here
```

### 4️⃣ Run the Streamlit App  
```bash
streamlit run app.py
```

---

## 🛠️ Workflow
1. **Upload PDFs** → Extract text with **LangChain**
2. **Chunk Text** → Segment data for improved retrieval
3. **Embed & Store** → Convert text into embeddings and store in **ChromaDB**
4. **Query with LLM** → Retrieve relevant content and generate responses
5. **Display Results** → Streamlit UI for user interaction

---

## 📊 Key Technologies
- **LangChain** (Document processing, LLM integration)
- **ChromaDB** (Efficient vector storage & retrieval)
- **OpenAI Embeddings** (Semantic search & text understanding)
- **Streamlit** (Interactive UI for querying documents)
- **Python** (Core programming language)

---

## 💡 Future Enhancements
- ✅ Add **support for more file formats** (CSV, Word)
- ✅ Improve **chunking strategies** for better retrieval
- ✅ Enhance **UI/UX** with additional filtering options
- ✅ Experiment with **different embedding models** (e.g., Cohere, HuggingFace)

---

## 📜 License
This project is open-source under the **MIT License**.  


