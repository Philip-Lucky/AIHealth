
## **AI Health**

**AI Health**  platform is a next-generation patient portal designed specifically for diagnostic centers, built to tackle a common issue: lab reports are often hard to understand.

Patients typically receive reports filled with complex numbers and medical terms, leaving them unsure about what the results actually mean. This solution bridges that gap by combining:

**Smart Screening:** Instant risk insights for conditions like diabetes, heart disease, and more.
**AI-Powered Guidance:** An interactive “medical assistant” that breaks down reports into simple, easy-to-understand language.

It’s a complete end-to-end system—diagnostic centers get a powerful dashboard to manage patients efficiently, while patients gain a secure, user-friendly portal that helps them truly understand their health.

---

## Features

- **For Patients:**
    - **Smart Reports:** Upload a PDF and get an instant AI summary.
    - **Health Assistant:** Chat with an AI that knows your medical history.
    - **Risk Screening:** ML models check your vitals (Diabetes, Kidney, Liver, etc.).

- **For Doctors & Clinics:**
    - **Patient Dashboard:** View all patient records in one place.
    - **Trend Analysis:** Visualize patient health metrics over time.
    - **Secure & compliant:** Role-based access and data isolation.

###  Supported Screenings
We use trained ML models (XGBoost/RandomForest) to screen for:
*   **Diabetes:** (Glucose, BMI, Insulin)
*   **Heart Disease:** (Cholesterol, BP, ECG)
*   **Liver & Kidney Health**
*   **Lung Cancer Risk**

### Under the Hood
*   **RAG Architecture:** We use separate vector stores for each user to prevent data leakage.
*   **Vision AI:** Gemini Pro Vision reads raw PDF reports so you don't have to type data manually.
*   **Security:** Full JWT authentication and session management.

---

## Quick Start

### Step 1: Docker (
Spin up the entire stack with one command:

```bash
# Clone the repository
git clone [https://github.com/pavanbadempet/AI-Healthcare-System.git](https://github.com/Philip-Lucky/AIHealth)
cd AI-Healthcare-System

# Configure environment
cp .env.example .env
# Edit .env and add your GOOGLE_API_KEY

# Launch all services
docker-compose up --build
```


### Step 2: Development

**Prerequisites**: Python 3.10+, pip

```bash
# Install dependencies
# Install dependencies (Full Feature Set)
pip install -r requirements-full.txt

# OR for Lite Version (No PySpark/Heavy ML)
# pip install -r requirements.txt

# Start Backend (Terminal 1)
uvicorn backend.main:app --reload --port 8000

# Start Frontend (Terminal 2)
streamlit run frontend/main.py
```

### Option 3: Quick Scripts 
```powershell
# Run everything
.\scripts\runners\run_app.bat

# Run E2E tests
.\scripts\runners\run_e2e_tests.ps1
```

---

## 🛠️ Technology Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Frontend** | Streamlit | Responsive UI & Data Visualization |
| **Backend** | FastAPI, Pydantic | REST API & Request Validation |
| **ML/AI** | XGBoost, Scikit-Learn | Disease Classification Models |
| **GenAI** | Gemini Pro, LangChain | Chat Assistant & RAG Pipeline |
| **Vector DB** | FAISS | Semantic Search & Memory |
| **Database** | SQLite | User Data & Chat History |
| **DevOps** | Docker, Kubernetes (AWS EKS) GitHub Actions | Containerization & CI/CD |
| **Hosting** | Streamlit Cloud, Render | Production Deployment |

---

## 🧪 Testing

```bash
# Run all tests with coverage
pytest tests/ --cov=backend --cov-report=term-missing

# Run specific test suites
pytest tests/unit/           # Unit tests
pytest tests/integration/    # Integration tests
pytest tests/e2e/            # End-to-end tests (requires running app)
```

### CI/CD Pipeline
GitHub Actions automatically runs on every push:
- ✅ Unit & Integration Tests
- ✅ Code Coverage Reporting
- ✅ Placeholder Model Generation for CI

---

## 📁 Project Structure

```
├── backend/                # FastAPI backend
│   ├── main.py             # API entrypoint
│   ├── prediction.py       # ML prediction logic
│   ├── agent.py            # AI chat agent
│   ├── rag.py              # RAG pipeline
│   ├── vision_service.py   # Lab report analyzer
│   └── *.pkl               # Trained ML models
├── frontend/               # Streamlit frontend
│   ├── main.py             # App entrypoint
│   ├── views/              # Page components
│   └── components/         # Reusable UI components
├── mlops/                  # MLOps pipeline
│   ├── data_ingestion.py   # Data loading
│   ├── data_processing.py  # Feature engineering
│   └── model_training.py   # Training scripts
├── tests/                  # Test suites
│   ├── unit/               # Unit tests
│   ├── integration/        # API integration tests
│   └── e2e/                # End-to-end tests
├── scripts/                # Utility scripts
├── docker-compose.yml      # Multi-container setup
└── render.yaml             # Render deployment config
```

---

## 🌐 Deployment

### Frontend (Streamlit Cloud)
1. Fork/Push to GitHub
2. Connect repository to [Streamlit Cloud](https://streamlit.io/cloud)
3. Set `BACKEND_URL` environment variable

### Backend (Render)
1. Connect repository to [Render](https://render.com)
2. Uses `render.yaml` for auto-configuration
3. Set required environment variables:
   - `GOOGLE_API_KEY` - Gemini API key
   - `SECRET_KEY` - JWT signing key

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
