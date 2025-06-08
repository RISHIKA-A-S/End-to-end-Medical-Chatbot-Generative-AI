# 🧠 End-to-End Medical Chatbot (Generative AI with Gemini & Pinecone)

An intelligent question-answering medical chatbot built with PDF knowledge ingestion, semantic search using Pinecone, HuggingFace embeddings, and **Google Gemini Pro** for answer generation. It features an interactive web interface using Flask.

---

## 🚀 How to Run Locally?



✅ STEP 1: Clone the Repository

```bash
git clone https://github.com/<your-username>/End-to-end-Medical-Chatbot-Generative-AI.git
cd End-to-end-Medical-Chatbot-Generative-AI



✅ STEP 2: Set up the Environment

conda create -n medibot python=3.10 -y
conda activate medibot


✅ STEP 3: Install Dependencies

pip install -r requirements.txt



✅ STEP 4: Create a .env File in Root Directory

PINECONE_API_KEY=your_pinecone_api_key
GOOGLE_API_KEY=your_gemini_api_key