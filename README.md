# 🧠 End-to-End Medical Chatbot (Generative AI using Ollama & Pinecone)

An intelligent **medical question-answering chatbot** built with:

- 🔍 Custom PDF knowledge ingestion
- 📚 Semantic search using **Pinecone**
- 🧠 Local LLM inference via **Ollama** (e.g., LLaMA, Mistral)
- 🌐 Web interface powered by **Flask**

---

## 🚀 Features

- Ingests and indexes medical PDFs.
- Performs **semantic search** using **HuggingFace embeddings** + **Pinecone vector DB**.
- Generates answers using **local models** via **Ollama** (no API cost).
- Fully functional **Flask-based** web UI for easy interaction.
- Modular and scalable architecture for healthcare use cases.

---

## 🛠️ Tech Stack

| Component          | Technology               |
|-------------------|--------------------------|
| Embeddings         | HuggingFace Transformers |
| Vector Store       | Pinecone                 |
| LLM Inference      | Ollama (LLaMA/Mistral)   |
| Backend            | Flask                    |
| PDF Parsing        | PyMuPDF / pdfminer.six   |

---

## 🧪 Setup Instructions (Run Locally)

### ✅ STEP 1: Clone the Repository

```bash
git clone https://github.com/<your-username>/End-to-End-Medical-Chatbot.git
cd End-to-End-Medical-Chatbot


✅ STEP 2: Set up the Environment
bash
Copy
Edit
conda create -n medibot python=3.10 -y
conda activate medibot


✅ STEP 3: Install Dependencies
bash
Copy
Edit
pip install -r requirements.txt


✅ STEP 4: Set Environment Variables
Create a .env file in the root directory with:

env
Copy
Edit
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=your_pinecone_env
PINECONE_INDEX_NAME=medical-chatbot-index


🧾 Folder Structure
graphql
Copy
Edit
.
├── app.py                  # Flask Web App
├── ingest.py               # PDF Ingestion & Vectorization
├── query.py                # Search & Response logic
├── templates/
│   └── index.html          # Web UI
├── static/
│   └── styles.css
├── data/                   # Your PDF medical files
├── .env                    # Environment variables
├── requirements.txt


