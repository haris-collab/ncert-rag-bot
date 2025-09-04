# 📘 NCERT RAG Bot

An **AI Tutor for Class 10 NCERT books** powered by a Retrieval-Augmented Generation (RAG) pipeline.  
You can upload or use the included NCERT PDFs, and the bot will answer questions conversationally.

---

## 🚀 Features
- Extracts text from NCERT PDF and splits into smart chunks.
- Embeds chunks into a **Chroma Vector Database**.
- Uses **Ollama** as the local LLM backend (default: `phi3-fast`).
- Provides a **Streamlit UI** for chat interaction.
- Conversational memory: remembers your questions & context.

---

## 📂 Project Structure
```
ncert-rag-bot/
│── data_ingestion.py # Extracts text from PDF and saves as ncert_text.txt
│── chunking.py # Splits extracted text into overlapping chunks
│── rag_pipeline.py # Builds the RAG QA pipeline
│── streamlit_app.py # Streamlit UI for chatting
│── ncert_science_class10.pdf # Example NCERT PDF
│── jesc106 2.pdf # Another example PDF
│── Modelfile # Ollama model config (optional)
│── README.md # This file
│── .gitignore
│── venv/ # Virtual environment (not pushed to GitHub)
│── ncert_db/ # Chroma database (ignored in Git)
│── ncert_text.txt # Extracted text (ignored in Git)
```


---

## 🛠️ Setup Guide

Follow these steps sequentially:

### 1️⃣ Clone the Repository

```
git clone https://github.com/haris-collab/ncert-rag-bot.git
cd ncert-rag-bot
```


2️⃣ Create & Activate Virtual Environment
```
python3 -m venv venv
```
```
source venv/bin/activate   # On macOS/Linux
```
```
venv\Scripts\activate      # On Windows
```

3️⃣ Install Dependencies
```
pip install -r requirements.txt
```

4️⃣ Install Ollama
Ollama is required to run local LLMs like phi3-fast.

macOS:
```
brew install ollama
```
Linux:
```
curl -fsSL https://ollama.com/install.sh | sh
```
Windows:
Download installer from ```https://ollama.com/download.```

Verify installation:
```
ollama --version
```


5️⃣ Pull the Model
This project uses phi3-fast as the default model.
```
ollama pull phi3-fast
```
You can change this later inside rag_pipeline.py.



6️⃣ Extract Text from PDF
By default, the repo includes:
ncert_science_class10.pdf
jesc106 2.pdf
Run text extraction:
```
python data_ingestion.py
```
This creates a ncert_text.txt file.



7️⃣ Run the Tutor in Streamlit
streamlit run streamlit_app.py
Open your browser at:
```
http://localhost:8501
```
Now you can chat with your AI Tutor 🎉


🧑‍💻 Changing the PDF
If you want to use another PDF:
Place your PDF inside the repo folder.
Update the path in data_ingestion.py:
```
pdf_file = "your_new_file.pdf"
```
Re-run:
```
python data_ingestion.py
```
📌 Notes
The vector DB (ncert_db/) and extracted text (ncert_text.txt) are ignored in GitHub for cleaner repos.
If you change the PDF, always re-run Step 6 before launching Streamlit.
Ollama must be running in the background when you start the tutor.


📝 Notes
To use your own PDFs, place them in the project root and update data_ingestion.py.
Chroma DB files (ncert_db/) and extracted text (ncert_text.txt) are auto-generated.
Encourage contributions! Fork the repo and submit pull requests 🎉
