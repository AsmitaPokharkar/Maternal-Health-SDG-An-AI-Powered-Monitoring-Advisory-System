# Maternal-Health-SDG-An-AI-Powered-Monitoring-Advisory-System

##  Overview :

Maternal mortality remains a critical global health challenge. **SDG 3.1** aims to reduce the maternal mortality ratio (MMR) to less than 70 per 100,000 live births by 2030. This project builds an **intelligent, AI‑powered system** that:

- Analyses historical MMR data from the **AIKosh SDG National Indicator Framework** dataset.
- Predicts MMR and classifies risk levels (**Low / Medium / High**) using **Random Forest** and **XGBoost**.
- Forecasts MMR trends up to **2030** with linear regression.
- Answers natural language questions via a **RAG (Retrieval-Augmented Generation) assistant** powered by **IBM Granite**.
- Presents interactive visualisations (trends, maps, forecasts) in a **Streamlit dashboard**.

**Target users:** Policymakers, public health researchers, government agencies, and NGOs working to improve maternal health.

---

##  Features :

| Feature | Description |
|---------|-------------|
| **Data Preprocessing** | Loads the AIKosh CSV, filters maternal indicators (MMR, skilled birth attendance, antenatal care, adolescent birth rate, health worker density). |
| **Regression Models** | Random Forest & XGBoost to predict MMR from health indicators. |
| **Risk Classification** | Random Forest classifier labels districts/states as **Low** (<70), **Medium** (70–139), or **High** (≥140) risk. |
| **Time Series Forecast** | Linear trend projection to 2030 – identifies if India will meet SDG 3.1. |
| **RAG Q&A Assistant** | Ask questions like *“Which Indian state has the highest MMR?”* – answers grounded in the dataset using IBM Granite. |
| **Interactive Dashboard** | Built with Streamlit – shows MMR trends, risk maps, forecast chart, and a live chat widget. |
| **Model Export** | Trained models saved as `.pkl` files for easy deployment. |

---

##  Tech Stack :

| Component | Technology |
|-----------|------------|
| **ML Training** | Google Colab (free GPU) – pandas, scikit‑learn, XGBoost |
| **RAG & LLM** | IBM watsonx.ai + IBM Granite (`ibm/granite-3-2-8b-instruct`) |
| **Workflow Orchestration** | LangFlow (visual agent pipeline) |
| **Vector Database** | FAISS / Chroma for retrieval |
| **Dashboard** | Streamlit (with Plotly for maps) |
| **Deployment** | IBM Cloud (optional) or Streamlit Cloud |

---

##  Repository Structure :

```
maternal-health-sdg-tracker/
├── notebooks/
│   └── maternal_health_ml_colab.ipynb   # Full Colab notebook (data loading, EDA, model training)
├── models/
│   ├── maternal_mmr_rf_model.pkl         # Random Forest regressor
│   ├── maternal_mmr_xgb_model.pkl        # XGBoost regressor
│   ├── maternal_risk_clf_model.pkl       # Random Forest classifier
│   └── maternal_trend_model.pkl          # Linear trend forecast model
├── dashboard/
│   ├── app.py                            # Streamlit dashboard
│   └── requirements.txt                  # Python dependencies
├── langflow/
│   └── app.json                          # LangFlow workflow export
├── data/
│   └── ai_kosh_dataset.csv               # (optional – download from AIKosh)
├── docs/
│   ├── ProblemStatement36_MaternalHealth.pdf
│   └── Maternal_Health_SDG_Tracker_Presentation.pptx
├── README.md
└── LICENSE
```

---

##  Getting Started :

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/maternal-health-sdg-tracker.git
cd maternal-health-sdg-tracker
```

### 2. Set Up IBM watsonx.ai (Granite Model)

- Sign up for an **IBM Cloud** account and create a watsonx.ai **Lite** plan (free).
- Create a project and note your `API key` and `Project ID`.
- Ensure the Granite model `ibm/granite-3-2-8b-instruct` is available in your region.

### 3. Install Dependencies

#### For the ML notebook (Google Colab)
Run the provided notebook directly in Colab – all dependencies install automatically.

#### For the Streamlit dashboard
```bash
cd dashboard
pip install -r requirements.txt
```

`requirements.txt`:
```
streamlit
pandas
numpy
plotly
joblib
scikit-learn
ibm-watson-machine-learning
langchain
chromadb
```

### 4. Run the ML Training (Optional – models are already in `/models`)

Open the Colab notebook (`notebooks/maternal_health_ml_colab.ipynb`) and run all cells. It will:
- Download the AIKosh dataset (or upload your own).
- Train the models and save `.pkl` files.

### 5. Launch the Streamlit Dashboard

```bash
streamlit run dashboard/app.py
```

Your dashboard will open at `http://localhost:8501`.  
You can also deploy it for free on **Streamlit Cloud** – connect your GitHub repo.

### 6. Use the RAG Assistant

In the dashboard, you will see a chat box. Type questions like:
- *“What is India’s MMR trend?”*
- *“Is India on track to achieve SDG 3.1 by 2030?”*
- *“Which factors most affect maternal mortality?”*

The assistant uses **IBM Granite** to generate answers grounded in the AIKosh dataset and any uploaded policy documents.

---

##  Future Scope :

- **State/ District‑level analysis** – Integrate NFHS and HMIS data for granular insights.
- **Causal inference** – Estimate impact of policies (e.g., JSY, PMMVY) on MMR.
- **Real‑time data ingestion** – Connect to live health information systems.
- **Multilingual support** – Hindi, Tamil, Marathi using Granite’s multilingual capabilities.
- **Mobile app / WhatsApp bot** – For grassroots health workers.
- **Integration with IBM Cloud Pak for Data** – Enterprise‑grade governance.
---
