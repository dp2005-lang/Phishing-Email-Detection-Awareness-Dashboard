# Phishing-Email-Detection-Awareness-Dashboard
PHISHGUARD is a defensive cybersecurity dashboard that detects phishing emails using sender, content, URL, attachment, rule-based and ML analysis. It provides explainable risk scores, security recommendations, analytics, history tracking, and phishing awareness training using safe synthetic data.
# 🛡️ PHISHGUARD

## Phishing Email Detection & Security Awareness Dashboard

**PHISHGUARD** is a defensive cybersecurity platform designed to identify and analyze potential phishing emails using a combination of **rule-based detection, sender analysis, content analysis, static URL inspection, attachment analysis, and machine-learning techniques**.

The system converts technical indicators into an understandable **risk score, threat classification, explainable findings, and recommended security actions**, making it suitable for cybersecurity education, awareness training, and security-operations demonstrations.

> **Project Type:** Defensive Cybersecurity • Email Security • Machine Learning • Security Analytics
> **Data:** Synthetic / Authorized Data Only
> **Deployment:** Google Colab / Local Environment

---

## 🎯 Project Objective

Phishing remains one of the most common social-engineering techniques used to deceive users into clicking malicious links, opening dangerous attachments, or revealing sensitive information.

PHISHGUARD aims to address this problem by providing a centralized dashboard that can:

* Analyze suspicious email content
* Detect social-engineering indicators
* Examine sender patterns
* Perform static URL analysis
* Identify suspicious attachment filenames
* Generate an explainable risk score
* Classify emails by risk level
* Provide recommended security actions
* Maintain analysis history
* Visualize security analytics
* Provide phishing-awareness education

The project focuses on **defensive detection and user awareness**, rather than offensive phishing activity.

---

# ✨ Key Features

### 🔍 Email Threat Analysis

Users can submit:

* Sender email address
* Email subject
* Email body
* Attachment filename

The system analyzes the submitted information and produces a security assessment.

---

### 🧠 Multi-Layer Detection

PHISHGUARD does not rely on a single indicator.

It combines multiple analysis layers:

```text
Email
  │
  ├── Sender Analysis
  │
  ├── Content Analysis
  │
  ├── URL Analysis
  │
  ├── Attachment Analysis
  │
  └── Machine Learning
          │
          ▼
   Risk Engine
          │
          ▼
 Explainable Assessment
```

---

### 👤 Sender Analysis

The sender analyzer examines characteristics such as:

* Sender format
* Domain structure
* Domain length
* Excessive subdomains
* Unusual characters
* Suspicious sender patterns
* Potential display-name/domain mismatch

The system does **not automatically consider an unfamiliar domain malicious**.

---

### 📝 Content Analysis

The content engine searches for common phishing and social-engineering signals, including:

* Urgency
* Threats
* Credential requests
* Password requests
* Financial pressure
* Reward/prize language
* Personal-information requests
* Generic greetings
* Excessive punctuation
* Unusual capitalization

---

### 🔗 Static URL Analysis

URLs are inspected without visiting them.

The analyzer can identify:

* HTTP instead of HTTPS
* Raw IP addresses
* Excessive subdomains
* Suspicious keywords
* Unusually long URLs
* URL-shortener patterns
* Unusual URL structures

> **Important:** PHISHGUARD does not automatically open, crawl, or interact with analyzed URLs.

HTTPS is treated as an encryption property, **not proof that a website is trustworthy**.

---

### 📎 Attachment Analysis

PHISHGUARD analyzes attachment **filenames only**.

Potentially risky extensions include:

```text
.exe
.scr
.bat
.cmd
.js
.vbs
.ps1
.msi
```

The system also detects suspicious patterns such as:

```text
invoice.pdf.exe
document.docx.exe
image.jpg.exe
```

> Attachments are never executed.

---

# 📊 Explainable Risk Scoring

The system generates a risk score from:

```text
0 ─────────────────────────────── 100
│                                  │
Low Risk                    High Risk
```

### Classification

| Risk Score | Classification                 |
| ---------: | ------------------------------ |
|       0–20 | 🟢 LOW RISK                    |
|      21–40 | 🔵 MODERATE RISK               |
|      41–70 | 🟠 SUSPICIOUS                  |
|     71–100 | 🔴 HIGH RISK / LIKELY PHISHING |

The score is supported by individual analysis components rather than being presented as an unexplained prediction.

> These thresholds are project-level detection assumptions and should be calibrated against appropriate validation data for production use.

---

# 🤖 Machine Learning

PHISHGUARD includes a machine-learning component using:

* TF-IDF text representation
* Logistic Regression
* Multinomial Naive Bayes
* Random Forest experimentation
* Train/test evaluation
* Precision
* Recall
* F1-score
* Accuracy
* Confusion matrix

The machine-learning component complements the rule-based engine rather than replacing explainable security indicators.

### Why multiple metrics?

Accuracy alone can hide important security problems.

For phishing detection:

* **Precision** helps reduce false alarms.
* **Recall** helps reduce missed phishing emails.
* **F1-score** balances precision and recall.

> Model performance shown by this project is based on synthetic data and should not be interpreted as real-world production performance.

---

# 📈 Security Dashboard

The dashboard provides a professional security-operations-style interface containing:

### Overview

* Total emails analyzed
* High-risk emails
* Suspicious emails
* Low-risk emails
* Average risk score

### Analytics

* Classification distribution
* Risk-score distribution
* Detection trends
* Analysis history

### Analyzer

* Email input
* Risk score
* Classification
* Sender findings
* Content findings
* URL findings
* Attachment findings
* Recommended actions

### Awareness

Educational guidance covering:

* How to identify phishing
* How to inspect sender addresses
* How to handle suspicious links
* How to handle attachments
* How to protect credentials
* How to verify unusual requests

---

# 🗃️ Analysis History

PHISHGUARD uses SQLite to maintain analysis metadata.

Stored information includes:

* Analysis ID
* Sender domain
* Subject
* Risk score
* Classification
* Timestamp
* Detected indicators

The system is designed to avoid storing complete email bodies by default.

---

# 🧪 Synthetic Dataset

The project generates a synthetic dataset containing hundreds of fictional email samples.

Example categories include:

### Legitimate

* University notifications
* HR updates
* Project meetings
* Training reminders
* Newsletters
* Password-change confirmations

### Phishing

* Fake account verification
* Fake invoices
* Fake password expiration
* Fake delivery notices
* Fake HR requests
* Fake rewards
* Fake security alerts

The project uses safe fictional domains and reserved IP ranges for demonstrations.

Examples:

```text
example.com
example.org
example.net
invalid.test
198.51.100.10
```

No real phishing infrastructure is required.

---

# 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │       User           │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Web Dashboard      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Email Input        │
                    └──────────┬───────────┘
                               │
             ┌─────────────────┼─────────────────┐
             │                 │                 │
             ▼                 ▼                 ▼
      ┌────────────┐   ┌────────────┐   ┌────────────┐
      │  Sender    │   │  Content   │   │    URL     │
      │  Analyzer  │   │  Analyzer  │   │  Analyzer  │
      └─────┬──────┘   └─────┬──────┘   └─────┬──────┘
            │                │                │
            └────────────────┼────────────────┘
                             │
                             ▼
                    ┌──────────────────────┐
                    │   Risk Engine        │
                    │                      │
                    │ Rule + ML Analysis   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Explainable Result   │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
        ┌──────────┐     ┌──────────┐    ┌────────────┐
        │ Dashboard│     │  SQLite  │    │ Awareness  │
        │ Analytics│     │ History  │    │  Training  │
        └──────────┘     └──────────┘    └────────────┘
```

---

# 🛠️ Technology Stack

| Technology          | Purpose                 |
| ------------------- | ----------------------- |
| Python              | Core application        |
| Gradio              | Interactive dashboard   |
| Pandas              | Dataset processing      |
| NumPy               | Numerical operations    |
| Scikit-learn        | Machine learning        |
| TF-IDF              | Text feature extraction |
| Logistic Regression | Classification          |
| Naive Bayes         | ML comparison           |
| Random Forest       | ML experimentation      |
| Plotly              | Security analytics      |
| SQLite              | Analysis history        |
| Regex               | Pattern detection       |
| Joblib              | Model persistence       |

---

# 📁 Project Structure

```text
PHISHGUARD/
│
├── data/
│   └── phishing_email_dataset.csv
│
├── models/
│   └── phishguard_model.joblib
│
├── reports/
│
├── screenshots/
│
├── docs/
│
├── tests/
│   └── automated_test_results.csv
│
├── phishguard.db
│
└── README.md
```

The Google Colab version can also run as a **single-cell implementation** for easy demonstration.

---

# 🚀 Getting Started

## Option 1 — Google Colab

1. Open Google Colab.
2. Create a new notebook.
3. Paste the complete PHISHGUARD code into one cell.
4. Run the cell.
5. Wait for dependency installation and model training.
6. Open the generated Gradio dashboard link.

The application automatically creates:

* Synthetic dataset
* Machine-learning model
* SQLite database
* Test results
* Dashboard

---

## Option 2 — Local Environment

Clone the repository:

```bash
git clone https://github.com/yourusername/phishguard.git
cd phishguard
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python app.py
```

---

# 🧪 Testing

PHISHGUARD includes automated tests covering:

* Legitimate email detection
* Urgency detection
* Credential requests
* Financial requests
* Generic greetings
* URL analysis
* Raw IP detection
* Non-HTTPS URLs
* Multiple URLs
* Suspicious attachments
* Double extensions
* Sender validation
* Risk-score boundaries
* Database persistence
* ML availability
* Analysis-history retrieval

Example:

```text
Automated Security Tests

T01  Legitimate email             PASS
T02  Urgent phishing email        PASS
T03  Credential request           PASS
T04  Financial request            PASS
T05  Generic greeting             PASS
T06  Safe URL                     PASS
T07  Raw IP URL                   PASS
T08  Non-HTTPS URL                PASS
...
```

Actual test results should always be generated by running the project rather than manually claiming performance.

---

# 🔐 Security & Ethical Considerations

PHISHGUARD was intentionally designed as a **defensive cybersecurity project**.

### The application does NOT:

* Send phishing emails
* Harvest credentials
* Create credential-stealing pages
* Execute attachments
* Automatically visit URLs
* Attack external systems
* Collect real user passwords
* Require real phishing infrastructure

### Safe demonstration principles

Use:

* Synthetic email content
* Fictional domains
* Reserved IP addresses
* Authorized test data
* Local environments
* Isolated demonstrations

---

# ⚠️ Limitations

PHISHGUARD is an educational prototype and should not be treated as a complete enterprise email-security gateway.

Current limitations include:

* Synthetic training data
* Rule-based thresholds
* Limited linguistic understanding
* No live threat-intelligence feeds
* No sandbox execution
* No real-time mail-server integration
* No enterprise authentication system
* No production-grade distributed architecture

Real-world deployment would require extensive validation against representative datasets and operational security requirements.

---

# 🔮 Future Enhancements

Potential future development includes:

* Real-time mail-server integration
* Microsoft 365 / Gmail security integration
* Advanced NLP models
* Transformer-based classification
* Explainable AI visualizations
* Domain reputation integration
* Threat-intelligence feeds
* SPF/DKIM/DMARC analysis
* Attachment sandboxing in an isolated environment
* Role-based access control
* Authentication and authorization
* REST API
* Rate limiting
* SIEM integration
* Security alerting
* PDF security reports
* Analyst feedback loops
* Model retraining pipelines

---

# 📌 Example Workflow

```text
1. User submits an email
          ↓
2. Sender is analyzed
          ↓
3. Email content is analyzed
          ↓
4. URLs are extracted and inspected statically
          ↓
5. Attachment filename is checked
          ↓
6. Rule-based score is generated
          ↓
7. ML model provides additional signal
          ↓
8. Risk engine combines the evidence
          ↓
9. Email receives a classification
          ↓
10. Dashboard explains WHY
          ↓
11. Recommended security actions are displayed
          ↓
12. Analysis metadata is stored
```

---

# 🎓 Academic / Final-Year Project Value

PHISHGUARD demonstrates practical knowledge across multiple cybersecurity and software-engineering areas:

* Cybersecurity fundamentals
* Phishing detection
* Social engineering
* Secure software design
* Machine learning
* Natural language processing
* Data preprocessing
* Explainable detection
* Database management
* Data visualization
* Software testing
* User-interface design
* Security awareness

The project can therefore be presented as a combination of:

> **Cybersecurity + Machine Learning + Web Dashboard + Security Analytics + User Awareness**

---

# 💼 Resume Project Description

**PHISHGUARD — Phishing Email Detection & Awareness Dashboard**

> Developed a defensive cybersecurity dashboard that combines rule-based analysis, TF-IDF machine learning, sender/content inspection, static URL analysis, attachment-risk detection, explainable scoring, SQLite-based history, security analytics, and phishing-awareness education using synthetic data.

---

# 📊 Project Highlights

```text
✓ Synthetic phishing dataset
✓ Explainable risk scoring
✓ Sender analysis
✓ Content analysis
✓ Static URL analysis
✓ Attachment analysis
✓ Machine learning
✓ Security analytics
✓ SQLite persistence
✓ Automated testing
✓ Awareness training
✓ Professional dashboard
✓ Defensive-by-design architecture
```

---

# ⚖️ Disclaimer

PHISHGUARD is developed strictly for **educational, defensive cybersecurity, research, and authorized testing purposes**.

All demonstrations should use synthetic, fictional, or properly authorized data.

The project must not be used to conduct phishing campaigns, harvest credentials, compromise accounts, or interact with systems without authorization.

---

# 👨‍💻 Author

**Debankita Panja**

Cybersecurity • Machine Learning • Software Development

> Replace this section with your GitHub profile, LinkedIn profile, email, and portfolio links before publishing.

---

# ⭐ Support the Project

If you find PHISHGUARD useful for learning cybersecurity, machine learning, or secure application development:

⭐ Star the repository
🍴 Fork the project
🐛 Report issues
💡 Suggest improvements
🤝 Contribute responsibly

---

## 📜 License

This project can be released under the **MIT License** for educational and research use, subject to the project's ethical-use requirements.
