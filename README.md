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

🛠️ Installation & Setup
Clone the Repository

Bash
git clone https://github.com/yourusername/phishguard.git
cd phishguard
Install Dependencies

Bash
pip install -r requirements.txt
Initialize Models

Ensure all trained model files (url_cnn_model.keras, hybrid_url_model.pkl, etc.) are placed within the /models/ directory as specified in the project structure.

Run the API

Bash
python phishguard_api.py
Chrome Extension Setup

Open chrome://extensions/ in your browser.

Enable Developer Mode.

Click Load Unpacked and select the extension/ folder.

🌐 API Usage
Analyze URL
POST /analyse

JSON
{
  "url": "https://example-phishing-site.com"
}
Response
JSON
{
  "verdict": "PHISHING",
  "confidence": 0.87,
  "url_score": 0.82,
  "html_score": 0.91
}
📈 Performance & Limitations
Accuracy: The URL hybrid model achieves ~96% accuracy, while the BiLSTM content model reaches ~80%.

Current Limitations: Accuracy is dependent on successful scraping; JavaScript-heavy sites may require further optimization.

🔮 Future Roadmap
Integration of Transformer models (BERT) for better NLP analysis.

Cloud-based deployment for global accessibility.

Real-time threat intelligence feed integration.

📜 License
This project is licensed under the MIT License.
