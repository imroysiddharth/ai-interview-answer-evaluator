# 🎙️ AI Interview Answer Evaluator

An **AI-powered interview evaluation system** that analyzes spoken interview answers and produces **structured feedback and scores** based on clarity, relevance, and confidence.

The project is **automation-first**, has **minimal UI**, and is designed for **real-world usage** by recruiters, candidates, and interview coaching platforms.

---

## 🚀 Features

* 🎧 Upload interview answers as audio (`.wav`, `.mp3`, `.m4a`)
* 🧠 Speech-to-text using **Whisper (faster-whisper)**
* 📊 LLM-based evaluation using **Google Gemini** (OpenAI optional)
* ✅ Scores for:

  * Clarity
  * Relevance
  * Confidence
  * Overall Score
* 📝 Actionable strengths & improvement suggestions
* 🔌 Clean REST API built with **FastAPI**
* 🎨 Lightweight **Streamlit UI** (frontend only, backend unchanged)
* 🐳 Fully **Dockerized** (backend + UI)

---

## 🏗️ Architecture Overview

```
Audio Input
    ↓
Speech-to-Text (Whisper)
    ↓
Text Cleaning & Normalization
    ↓
LLM Evaluation (Gemini / OpenAI)
    ↓
Scoring Engine
    ↓
JSON Feedback (FastAPI API)
    ↓
Streamlit UI (Optional)
```

---

## 🛠 Tech Stack

### Backend

* Python
* FastAPI
* Whisper (faster-whisper)
* Google Gemini (LLM)
* Optional: OpenAI (fallback)

### Frontend

* Streamlit

### Dev & Infra

* Docker & Docker Compose
* FFmpeg
* Uvicorn
* Watchdog

---

## 📂 Project Structure

```
ai-interview-answer-evaluator/
│
├── app/
│   ├── main.py
│   ├── whisper_service.py
│   ├── evaluator/
│   │   ├── gemini_evaluator.py
│   │   ├── openai_evaluator.py
│   │   └── __init__.py
│   └── UI/
│       └── ui.py
│
├── Dockerfile
├── Dockerfile.ui
├── docker-compose.yml
├── requirements.txt
├── README.md
└── sample_audio/
```

---

## ⚙️ Local Setup (Without Docker)

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/siddharthk2608/ai-interview-answer-evaluator.git
cd ai-interview-answer-evaluator
```

### 2️⃣ Create & Activate Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Install FFmpeg

```bash
brew install ffmpeg   # macOS
sudo apt install ffmpeg  # Linux
```

### 5️⃣ Set Environment Variables

```bash
export GOOGLE_API_KEY="your_gemini_api_key"
```

---

## ▶️ Run the Backend API

```bash
uvicorn app.main:app --reload
```

Swagger UI:

```
http://127.0.0.1:8000/docs
```

---

## 🎨 Run the Streamlit UI (Local)

```bash
streamlit run app/UI/ui.py
```

---

## 🐳 Run with Docker (Recommended)

### Build & Run

```bash
docker-compose up --build
```

### Access

* Backend API → [http://localhost:8000/docs](http://localhost:8000/docs)
* Streamlit UI → [http://localhost:8501](http://localhost:8501)

### Stop Containers

```bash
docker-compose down
```

---

## 📤 API Usage Example

```bash
curl -X POST "http://127.0.0.1:8000/evaluate?question=Tell%20me%20about%20a%20challenging%20project" \
  -F "audio=@answer.wav"
```

---

## 📌 Resume Bullet Points

* Built an **AI-powered interview evaluation platform** using Whisper and LLMs to score spoken answers on clarity, relevance, and confidence
* Designed a **FastAPI-based scoring engine** with clean REST endpoints and JSON feedback
* Implemented a **Dockerized microservice architecture** with Streamlit UI and FastAPI backend
* Integrated **Google Gemini** for automated qualitative assessment of interview responses

---

## 🔒 Notes

* API keys are managed via environment variables
* `.env`, virtual environments, and large media files are excluded via `.gitignore` and `.dockerignore`

---
