# PensionRAG
Pension RAG model for 606 Final
# Pension Fund Benefit Estimation Using RAG and LLMs

## 🚀 Project Summary
Pension plan documents are long, complex, and difficult for the average enrollee to navigate.  
This project uses a **Retrieval-Augmented Generation (RAG)** approach to **automate pension estimate calculations** by intelligently extracting pension rules, applying them to user inputs, and producing accurate, explainable retirement projections.

The project specifically targets the NYCERS Tier 6 plan, but the system is designed to be generalizable to other pension funds in the future.

## 🧱 Tech Stack

- **Python 3.10**
- **pdfplumber** + **PyMuPDF (fitz)** – Clean parsing of pension PDFs
- **LlamaIndex** – Document ingestion, retrieval, metadata reranking
- **FAISS** – Vector database for fast semantic search
- **all-mpnet-base-v2** – Embedding model for semantic retrieval
- **Mistral-7B-Instruct** – Language model for step-by-step pension reasoning
- **Python math engine** – Final pension calculations done programmatically for precision
- **Streamlit** (or Gradio) – Frontend user interface (✅ built)
- **(Optional) MLflow** – Model/version tracking (pending)

## 🛠️ System Architecture Overview

1. **Parse PDFs** using pdfplumber + fitz  
2. **Semantic Chunking** with SentenceSplitterNodeParser  
3. **Embed Chunks** using all-mpnet-base-v2  
4. **Index into FAISS** for fast semantic search  
5. **Retrieve Top-K Chunks** based on user query  
6. **Metadata-Aware Reranking** to boost pension formulas  
7. **Manual Context Injection** into custom LLM prompts  
8. **LLM Step-by-Step Reasoning** (Mistral 7B)  
9. **Final Calculation** performed via Python for precise pension math  
10. **Frontend UI** for user interaction and dynamic pension estimate generation

## 📈 Sample Output

| User Input | Model Output |
|:-----------|:-------------|
| "I’m 60 with 28 years of service and a $110K salary" | Correct pension formula retrieved, early retirement penalty applied, and final pension calculated via Python. |
| "I’m 63 with 17 years of service and 3 years of military buyback" | Correct eligibility, military service credited, full pension calculated and explained. |

*Screenshots coming soon!*

## ⚡ Challenges and Solutions

| Challenge | Solution |
|:---------|:---------|
| LLM math hallucination | Offloaded final pension calculation to Python for precision |
| Retrieval missing pension formulas | Added metadata tagging and reranking |
| LLaMA 3.2 runaway text generation | Switched to Mistral-7B for more focused answers |
| Table parsing from PDFs | Used pdfplumber + custom chunking strategies |

## 🧪 Future Research Directions

- Extend support for additional pension funds and tiers  
- Automate penalty table extraction without manual metadata tagging  
- Create a full interactive dashboard for multiple retirement scenario comparisons  
- Integrate MLflow for version control and experimental tracking  
- Explore fine-tuning smaller LLMs for pension-specific reasoning tasks  

## 🖥️ Running the Project

```bash
# Clone the repo
git clone https://github.com/cwndrohan/pension-rag-capstone.git

# Install requirements
pip install -r requirements.txt

# Launch the Streamlit UI
streamlit run app.py
