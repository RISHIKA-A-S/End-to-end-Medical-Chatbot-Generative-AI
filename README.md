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


✅ STEP 1: Clone the Repository

git clone https://github.com/<your-username>/End-to-End-Medical-Chatbot.git
cd End-to-End-Medical-Chatbot




✅ STEP 2: Set up the Environment

conda create -n medibot python=3.10 -y
conda activate medibot



✅ STEP 3: Install Dependencies

pip install -r requirements.txt




✅ STEP 4: Set Environment Variables

Create a .env file in the root directory with:




PINECONE_API_KEY=your_pinecone_api_key
PINECONE_ENVIRONMENT=your_pinecone_env
PINECONE_INDEX_NAME=medical-chatbot-index


🧾 Folder Structure

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



⚙️ How It Works

PDFs are parsed and chunked into small contexts.

Each chunk is embedded using HuggingFace models.

Embeddings are stored in Pinecone vector DB.

When the user asks a question:

Top relevant chunks are retrieved from Pinecone.

Context + user query is passed to the Ollama LLM (like mistral, llama3).

A natural language answer is generated.


![Image](https://github.com/user-attachments/assets/7301ec3e-b123-49f3-8a07-31e40db76f89)


🧪 Example Queries

"What are the symptoms of Type 2 diabetes?"

"Explain the side effects of Metformin."

"How does hypertension affect kidney function?"


🔒 Disclaimer
This project is for educational/demo purposes only. Not intended for actual clinical decision-making or diagnosis.


📄 License
This project is licensed under the MIT License.


🤝 Contributing
PRs, feedback, and issues are welcome! Let’s improve healthcare AI together.



