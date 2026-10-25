
# 🧠 End-to-End Medical Chatbot
### Generative AI | RAG | Ollama | Pinecone | Flask

An intelligent **medical question-answering chatbot** built using Generative AI and Retrieval-Augmented Generation (RAG). The application retrieves relevant information from medical PDF documents and uses a locally hosted Large Language Model (LLM) to generate context-aware responses.

The project combines **Hugging Face embeddings, Pinecone vector search, Ollama, and Flask** to create a document-based medical information assistant.

## 🚀 Features

- 📄 **PDF Knowledge Ingestion:** Extracts text from medical PDF documents.
- ✂️ **Intelligent Text Chunking:** Splits extracted text into smaller chunks for efficient retrieval.
- 🔍 **Semantic Search:** Finds relevant medical information based on the meaning of a query.
- 🧠 **Hugging Face Embeddings:** Converts text into numerical vector representations.
- 📚 **Pinecone Vector Database:** Stores and retrieves document embeddings efficiently.
- 🤖 **Local LLM Inference:** Generates responses using models such as Llama or Mistral through Ollama.
- 💬 **Context-Aware Answers:** Uses retrieved document passages to help ground responses in the provided knowledge base.
- 🌐 **Interactive Web Interface:** Provides a chatbot interface using Flask, HTML, and CSS.
- 🔐 **Environment-Based Configuration:** Keeps API credentials outside the application source code.
- 🧩 **Modular Architecture:** Separates document ingestion, retrieval, response generation, and web application logic.

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Programming Language | Python |
| Backend Framework | Flask |
| Embedding Models | Hugging Face Transformers |
| Vector Database | Pinecone |
| Large Language Models | Llama / Mistral |
| LLM Runtime | Ollama |
| PDF Processing | PyMuPDF / pdfminer.six |
| Frontend | HTML, CSS |
| Environment Configuration | Python dotenv |
| AI Architecture | Retrieval-Augmented Generation (RAG) |

## 🏗️ System Architecture

The chatbot follows a Retrieval-Augmented Generation workflow consisting of two main stages: document ingestion and question answering.

![End-to-End Medical Chatbot Architecture](https://github.com/user-attachments/assets/7301ec3e-b123-49f3-8a07-31e40db76f89)

### 🔄 Application Workflow

#### 1. Document Ingestion Pipeline

1. Medical PDF documents are uploaded or placed in the `data/` directory.
2. Text is extracted using a PDF parsing library.
3. Extracted text is divided into smaller chunks.
4. Hugging Face embedding models convert each chunk into a vector representation.
5. The vectors, along with associated text or metadata, are stored in Pinecone.

#### 2. Question-Answering Pipeline

1. The user enters a medical question through the web interface.
2. Flask receives the question and passes it to the query-processing module.
3. The question is converted into an embedding using the same embedding model.
4. Pinecone performs a similarity search to retrieve the most relevant document chunks.
5. The retrieved context and user question are passed to an LLM through Ollama.
6. The LLM generates a natural-language response using the available context.
7. Flask returns the answer to the user through the chatbot interface.

### 🧩 RAG Pipeline

```text
Medical PDF Documents
        |
        v
   Text Extraction
        |
        v
    Text Chunking
        |
        v
 Hugging Face Embeddings
        |
        v
  Pinecone Vector Database
        |
        |         User Question
        |                |
        |                v
        |         Query Embedding
        |                |
        +------> Semantic Search
                         |
                         v
                 Relevant Context
                         |
                         v
                  Ollama LLM
                 (Llama / Mistral)
                         |
                         v
                 Generated Answer
                         |
                         v
                  Flask Web UI
```

## 📂 Project Structure

```text
End-to-End-Medical-Chatbot/
│
├── app.py                  # Flask web application
├── ingest.py               # PDF ingestion and vector indexing
├── query.py                # Semantic retrieval and answer generation
│
├── templates/
│   └── index.html          # Chatbot web interface
│
├── static/
│   └── styles.css          # Frontend styling
│
├── data/                   # Medical PDF documents
├── .env                    # Environment variables
├── .gitignore              # Files excluded from Git
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

## ⚙️ Installation and Setup

Follow these steps to run the application locally.

### Prerequisites

Ensure the following are installed:

- Python 3.10
- Git
- Conda or Python virtual environment
- Ollama
- A Pinecone account and API key

### Step 1: Clone the Repository

Replace `your-username` with your GitHub username.

```bash
git clone https://github.com/your-username/End-to-End-Medical-Chatbot.git

cd End-to-End-Medical-Chatbot
```

### Step 2: Create a Virtual Environment

Using Conda:

```bash
conda create -n medibot python=3.10 -y

conda activate medibot
```

Alternatively, use Python's built-in virtual environment:

```bash
python -m venv medibot
```

Activate it on Windows:

```bash
medibot\Scripts\activate
```

Activate it on macOS or Linux:

```bash
source medibot/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

Ensure that `requirements.txt` contains the libraries required by your implementation, including Flask, the selected Hugging Face packages, the Pinecone SDK, the Ollama integration, the PDF parser, and `python-dotenv`.

### Step 4: Configure Environment Variables

Create a `.env` file in the project root directory.

```env
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_INDEX_NAME=medical-chatbot-index
```

Add any additional configuration required by your Pinecone SDK version and application code.

**Important:** Never upload API keys or secrets to GitHub. Add `.env` to your `.gitignore` file.

Example `.gitignore` entries:

```gitignore
.env
.venv/
medibot/
__pycache__/
*.py[cod]
.DS_Store
```

### Step 5: Install and Start Ollama

Download Ollama from:

https://ollama.com/

Pull a supported language model.

For Llama 3:

```bash
ollama pull llama3
```

Alternatively, for Mistral:

```bash
ollama pull mistral
```

Verify that the model is available:

```bash
ollama list
```

Ensure that the model name configured in `query.py` matches the model installed locally.

Ollama must be running before the chatbot sends generation requests.

### Step 6: Prepare the Medical Knowledge Base

Place your medical PDF documents in the `data/` directory.

Example:

```text
data/
├── diabetes_guide.pdf
├── hypertension_guide.pdf
└── medical_reference.pdf
```

Use documents that you have permission to process.

### Step 7: Ingest and Index Documents

Run the ingestion script:

```bash
python ingest.py
```

This process extracts text, creates chunks, generates embeddings, and stores the resulting vectors in Pinecone.

Before ingestion, ensure that the Pinecone index exists and that its vector dimension and similarity metric are compatible with your embedding model.

### Step 8: Run the Flask Application

Start the web application:

```bash
python app.py
```

Open the local URL displayed in the terminal. For a typical Flask development configuration, it is:

http://127.0.0.1:5000

You can now ask questions through the chatbot interface.

> The commands above assume that your Python files implement the described workflow. Adjust the configuration and commands to match your actual code.

## 💬 Example Queries

Try asking questions such as:

- What are the common symptoms of Type 2 diabetes?
- What side effects of metformin are described in the provided documents?
- How can hypertension affect kidney function?
- What lifestyle recommendations are mentioned in the medical reference?
- Summarize the important points from the retrieved medical information.

The answers depend on the content of the indexed documents, the quality of retrieval, and the selected language model.

## 🧠 Why Retrieval-Augmented Generation?

Traditional LLMs generate responses using information learned during training. RAG supplements generation with relevant information retrieved from an external knowledge base.

The main advantages include:

- **Domain-specific knowledge:** Answers can draw on the supplied medical documents.
- **Context-aware generation:** Relevant passages are provided to the model before it generates a response.
- **Updatable knowledge base:** New documents can be indexed without retraining the language model.
- **Local inference option:** Ollama can run supported models locally, reducing reliance on paid hosted LLM inference APIs.
- **Improved traceability potential:** Retrieved passages can be displayed alongside answers when source tracking is implemented.

RAG does not guarantee factual accuracy. The generated response must still be evaluated against reliable sources.

## 🔐 Security and Responsible Use

- Store API keys and credentials in environment variables.
- Exclude `.env` and sensitive documents from version control.
- Validate user inputs and handle errors safely.
- Avoid logging confidential medical information.
- Treat retrieved document text as untrusted input.
- Apply appropriate access controls before deploying the application publicly.
- Evaluate the quality and reliability of generated responses.

### ⚠️ Medical Disclaimer

This project is intended for educational and demonstration purposes only. It is not a medical device and must not be used as a substitute for professional medical advice, diagnosis, or treatment.

The chatbot may generate incomplete, inaccurate, or misleading information. Always consult a qualified healthcare professional for medical concerns. For emergencies, contact local emergency services.

## 🔮 Future Enhancements

- [ ] Display source documents and page references with generated answers.
- [ ] Add conversation history and multi-turn question answering.
- [ ] Implement hybrid search using semantic and keyword retrieval.
- [ ] Add a reranking model to improve retrieval relevance.
- [ ] Introduce secure user authentication and document-level access control.
- [ ] Support additional document formats.
- [ ] Evaluate retrieval quality and answer faithfulness using a curated test dataset.
- [ ] Add safeguards for emergency-related questions.
- [ ] Improve the user interface with streaming responses and loading indicators.
- [ ] Add automated unit and integration tests.

## 🤝 Contributing

Contributions, suggestions, bug reports, and feature requests are welcome!

1. Fork the repository.
2. Create a new feature branch.
3. Implement your changes.
4. Test your changes.
5. Submit a pull request with a clear description.

## 📄 License

This project is intended to be distributed under the MIT License. Include a `LICENSE` file containing the MIT License text before claiming that the repository is officially licensed under it.

## 👩‍💻 Author

**Your Name**

- GitHub: [your-username](https://github.com/your-username)
- LinkedIn: [Your LinkedIn Profile](https://www.linkedin.com/)

---

⭐ If you find this project useful, consider giving the repository a star!

**Built with Python, Flask, Hugging Face, Pinecone, and Ollama.**

Like this project? Drop a ⭐ — it helps more than you think!
