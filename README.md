# GrowEasy-Core

> Main-repo for the GrowEasy intelligent agricultural assistant platform — combining Backend, Frontend, and ML Service into one place.

GrowEasy helps farmers make data-driven decisions through real-time weather & soil analysis, machine learning crop prediction, and AI-powered agronomist advisory.

**Demo:** https://youtu.be/bj9CQxPEIYs

---

## Repositories

| Service | Repo | Tech Stack |
|---|---|---|
| Backend (BE) | [GrowEasy](https://github.com/RidwanRamdhani/GrowEasy) | Go, Gin, PostgreSQL, Gemini AI |
| Frontend (FE) | [GrowEasy-UI](https://github.com/RidwanRamdhani/GrowEasy-UI) | React 19, Vite, CSS |
| ML Service | [Hackathon-AI](https://github.com/Rayya12/Hackathon-AI) | Python, Scikit-learn, LightGBM |

---

## Features

- **Crop Prediction** — ML model (Random Forest / Gradient Boosting) predicts the most suitable crop based on soil & weather conditions
- **AI Chatbot** — Google Gemini-powered chatbot
- **Weather Integration** — Real-time & historical weahter data via Open-Meteo API
- **Soil Analysis** — Soils data via SoilGrids API
- **History Tracking** — Saves past analyses
- **Secure Auth** — JWT-based user registration & login

---

## Architecture

```
User
 │
 ▼
GrowEasy-UI (React Frontend)
 │
 ▼
GrowEasy (Go Backend)
 ├──► Open-Meteo API      (Weather data)
 ├──► SoilGrids API       (Soil data)
 ├──► Hackathon-AI        (ML crop prediction)
 ├──► Google Gemini API   (AI advisory & chat)
 └──► PostgreSQL          (User data & history)
```

---

## Getting Started

### Clone with all submodules

```bash
git clone --recurse-submodules https://github.com/RidwanRamdhani/GrowEasy-Core.git
cd GrowEasy-Core
```

If already cloned without submodules:

```bash
git submodule update --init --recursive
```


---

### 1. ML Service

```bash
cd Hackathon-AI

# Create conda environment
conda create -n groweasy-ml python=3.10
conda activate groweasy-ml

# Install dependencies
pip install -r requirements.txt

# Run the service
python main.py
```

---

### 2. Backend

```bash
cd GrowEasy
```
Create a .env file in the backend root directory. You can use a template or add the following variables:

```env
PORT=8080
DB_HOST=localhost
DB_USER=postgres
DB_PASSWORD=yourpassword
DB_NAME=groweasy_db
DB_PORT=5432
JWT_SECRET=your_super_secret_key
GEMINI_API_KEY=your_gemini_api_key
GIN_MODE=release
GEMINI_MODEL=gemini-3.1-flash-lite-preview
```

```bash
go mod download
go run main.go
```

---

### 3. Frontend

```bash
cd GrowEasy-UI

# Copy and fill in environment variables
cp .env.example .env
```

Create a .env file in the Front end root directory. You can use a template or add the following variables:

```env
VITE_API_URL=http://localhost:8080
```

```bash
npm install
npm run dev
```

---

## Main-repo Structure

```
GrowEasy-Core/
├── GrowEasy/       → Go Backend
├── GrowEasy-UI/    → React Frontend
├── Hackathon-AI/   → ML Service
└── .gitmodules
```

Each subdirectory is an independent Git repository managed as a submodule. Commit history for each service remains fully separate — checkout each repository for more detailed information.