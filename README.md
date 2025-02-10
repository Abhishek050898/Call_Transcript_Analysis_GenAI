# Call_Transcript_Analysis_GenAI

## 📌 Overview
This repository contains a Jupyter Notebook (`Transcript_Analysis.ipynb`) designed for transcript analysis. The notebook processes textual transcripts to extract Member texts, perform sentiment analysis, and generate outcome ( Issue Resolved / Follow-Up Needed) based on the transcript.

## 🔍 Key Features
✅ **Extracts "Member" responses** from transcripts to analyze customer sentiment.  
✅ **Uses `cardiffnlp/twitter-roberta-base-sentiment`** for **sentiment classification** (Positive, Neutral, Negative).  
✅ **Applies `facebook/bart-large-mnli` (Zero-Shot)** to classify whether an issue is **Resolved** or requires **Follow-Up**. 
✅ **Stores labeled data in FAISS** for fast retrieval & continuous learning (Future Enhancement with larger dataset).   
✅ **Future-ready** with **fine-tuning & self-improving models** using FAISS-triggered retraining (Future Enhancement with larger dataset).

---

# 📂 Project Structure

```
Transcript_Analysis/
│── 📄 README.md                 # Project Documentation
│── 📄 Transcript_Analysis.ipynb  # Jupyter Notebook (Full Code)
│── 📄 requirements.txt           # Required dependencies
│── 📁 data/                      # Folder containing data files
│   │── 📁 transcripts/           # Folder containing raw transcript text files
```
## 📝 Usage
1. Open Jupyter Notebook:
   ```sh
   jupyter notebook
   ```
2. Navigate to `Transcript_Analysis.ipynb` and open it.
3. Run each cell in order to process the transcript and analyze the data.
4. Modify the data path (transcripts) as needed for your specific use case.

---

## 📊 **Models & Techniques Used**
### **1️⃣ Sentiment Analysis**
- **Model Used:** `cardiffnlp/twitter-roberta-base-sentiment`
- **Why?** Trained on tweets, making it effective for short, customer-centric sentences.
- **Output:** Labels (`Positive`, `Neutral`, `Negative`) + Confidence Score

### **2️⃣ Call Outcome Classification**
- **Model Used:** `facebook/bart-large-mnli` (Zero-Shot)
- **Why?** Eliminates the need for labeled training data.
- **Output:** Labels (`Issue Resolved`, `Follow-Up Needed`) + Confidence Score

### **3️⃣ FAISS for Vector Storage & Continuous Learning (Future Enhancement)**
- **Why?** Speeds up classification by storing & retrieving similar cases instead of running deep inference on every request.
- **How?**  
  ✅ Stores **MiniLM embeddings** of past cases and new cases.  
  ✅ When a new case arrives, FAISS searches for **similar past cases** and retrieves a label.  
  ✅ Every **100 new cases**, the system **triggers fine-tuning** for model improvement.

---

## 🚀 Installation

To use this project, clone the repository and install the necessary dependencies:

```sh
# Clone the repository
git clone https://github.com/yourusername/Transcript_Analysis.git
cd Transcript_Analysis

# Create a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

# Install dependencies
pip install -r requirements.txt
```

*Maintained by [Abhishek Kumar](https://github.com/Abhishek050898).*
