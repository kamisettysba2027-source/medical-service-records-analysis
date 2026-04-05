# 🏥 Medical Service Records Analysis (NLP + ML)

## 📌 Problem Statement
Medical service records contain unstructured text describing issues, failures, and maintenance notes.  
Analyzing this data manually is time-consuming and inconsistent.

This project uses **Natural Language Processing (NLP)** and **Machine Learning** to:
- Extract meaningful topics from service records
- Identify high-risk patterns
- Classify records for better decision-making

---

## 🎯 Objectives
- Clean and preprocess noisy medical service text data
- Discover hidden themes using topic modeling
- Classify records into important vs non-important events
- Improve recall for critical cases (business priority)

---

## ⚙️ Approach

### 1. Data Cleaning
- Text normalization, spelling correction
- Removal of noise patterns (e.g., repeated zeros)
- Combined multiple text fields for better context

### 2. Topic Modelling
- **LDA** for interpretable topics
- **BERTopic** for advanced clustering using embeddings
- Topic evaluation using coherence scores

### 3. Classification
- Models used:
  - XGBoost
  - LightGBM
  - Transformer-based models (BERT)
- Handling class imbalance using **SMOTEENN**
- Focus on **Recall optimization** (critical events detection)

---

## 🛠️ Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- BERTopic, Gensim
- Transformers (BERT)
- XGBoost, LightGBM
- Matplotlib, Seaborn

---

## 📁 Project Structure
notebooks/ → Data processing & modeling
data/ → Input datasets
outputs/ → Visualizations & results


---

## ▶️ Execution Flow

1. Run data cleaning notebook  
2. Perform topic modelling  
3. Run classification model  

---

## 📊 Key Results

- Improved detection of critical service events using recall-focused optimization  
- Identified key failure patterns using LDA and BERTopic  
- Enhanced model performance using:
  - Probability calibration
  - Better text representation
  - Class imbalance techniques  

---

## 📈 Outputs

- Topic visualizations (LDA & BERTopic)
- Event risk analysis plots
- Classification results with evaluation metrics
- Interactive topic maps

---

## 🚀 Setup Instructions

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Download spaCy model
python -m spacy download en_core_web_sm