# 🛡️ PhishGuard: AI-Powered Phishing Detection System

PhishGuard is a hybrid machine learning system that detects phishing websites by analyzing both URL structure and webpage content (HTML text). By combining deep learning (CNN, BiLSTM) with high-performance gradient boosting (XGBoost), PhishGuard provides a multi-layered defense against malicious web threats.

## 🚀 Overview
Unlike traditional approaches that rely solely on blacklists or URL patterns, PhishGuard utilizes a dual-engine analysis to produce a highly accurate phishing verdict.

- **🔗 URL Analysis:** Character-level patterns and structural feature engineering.
- **🌐 Content Analysis:** Real-time scraping and NLP-based inspection of HTML text.

---

## 🏗️ System Architecture
The system follows a sequential pipeline to ensure comprehensive coverage:

1. **URL Preprocessing:** Character-level analysis via **CNN**.
2. **Feature Extraction:** 15 engineered features (Length, Entropy, TLD, etc.).
3. **Hybrid URL Scoring:** **XGBoost** combines CNN output with structural features.
4. **Web Scraping:** Dynamic extraction of HTML content using BeautifulSoup.
5. **Content Analysis:** **BiLSTM** processes text to detect urgency and phishing language.
6. **Decision Engine:** Probability-based fusion of URL and Content scores.

---

## 🧠 Models & Methodology

| Model | Target | Description |
| :--- | :--- | :--- |
| **CNN** | URL Strings | Learns character-level suspicious patterns (e.g., random strings, IP-based URLs). |
| **XGBoost** | Hybrid URL | Processes 15 engineered features + CNN probability for a robust URL score. |
| **BiLSTM** | HTML Content | Analyzes webpage text for phishing intent, urgency, and deceptive language. |

### 📊 Verdict Logic
The final confidence score determines the risk level:
* **≥ 75%**: 🚩 Phishing
* **50–74%**: ⚠️ Suspicious
* **30–49%**: 🔍 Low Suspicion
* **< 30%**: ✅ Legitimate

---

## ⚙️ Tech Stack
* **Core:** Python, TensorFlow/Keras, XGBoost, Scikit-learn
* **Data:** Pandas, NumPy, BeautifulSoup
* **Deployment:** Flask (Backend API), Chrome Extension (Frontend)

---

## 📂 Project Structure
```text
phishguard/
├── models/             # Trained .keras, .pkl, and tokenizer files
├── extension/          # Chrome Extension source code (Manifest v3)
├── notebooks/          # Development and training logs (PhishGuard.ipynb)
├── phishguard_api.py   # Flask API for real-time inference
└── requirements.txt    # Project dependencies
