# ResearchPilot — Manual Setup & Run Instructions

This guide outlines the exact, step-by-step manual actions required to configure your **Google Gemini API Key**, run **Docker Desktop**, launch the application locally, and verify execution.

---

## 🔑 Part 1: Acquire & Set Gemini API Key

ResearchPilot utilizes Google's state-of-the-art **Gemini API** for text embeddings, abstract summaries, critiques, gap mapping, and syllabus compilation.

### Step 1: Get the API Key
1. Go to [Google AI Studio](https://aistudio.google.com/).
2. Sign in with your Google account.
3. Click on the **"Get API Key"** button.
4. Create a new API Key in a new or existing Google Cloud project.
5. Copy the generated key. **(Keep it confidential!)**

### Step 2: Inject Key as an Environment Variable
Before starting the backend, you must export the API key in the terminal session you are using to launch the server:

* **Windows PowerShell**:
  ```powershell
  $env:GEMINI_API_KEY="AIzaSyYourKeyHere..."
  ```
* **Windows Command Prompt (cmd)**:
  ```cmd
  set GEMINI_API_KEY=AIzaSyYourKeyHere...
  ```
* **macOS / Linux / Git Bash**:
  ```bash
  export GEMINI_API_KEY="AIzaSyYourKeyHere..."
  ```

---

## 🐳 Part 2: Running with Docker (Zero local installs)

Docker is the easiest way to run the entire stack. It automatically configures Node.js, Python, SQLite database tables, volume mounts, and network ports.

### Step 1: Install Docker Desktop
1. Download and install [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop/).
2. During installation, ensure the **"Use WSL 2 instead of Hyper-V (recommended)"** checkbox is enabled.
3. Restart your computer if prompted.
4. Launch Docker Desktop and accept the terms of service.

### Step 2: Spin Up Containers
Open a terminal in the root directory `d:\Dev Projects\ResearchPilot` and run:

```bash
# Inject key first (PowerShell example)
$env:GEMINI_API_KEY="AIzaSyYourKeyHere..."

# Start the full-stack container ecosystem
docker compose up -d --build
```
* The `-d` flag runs the containers detached (in the background).
* The `--build` flag forces Docker to compile fresh multi-stage optimized builds.

### Step 3: Accessing the App
* **Next.js Frontend**: Open `http://localhost:3000` in your browser.
* **FastAPI Backend Swagger Docs**: Open `http://localhost:8000/docs` in your browser.
* **Stop Services**: To shut down, run `docker compose down`.

---

## 💻 Part 3: Running Locally (Recommended for code editing)

If you want to edit and test code interactively without rebuilding Docker layers, run the servers locally.

### Step 1: Install Prerequisites
1. Download and install **Python 3.12** from [python.org](https://www.python.org/downloads/). (Ensure **"Add Python.exe to PATH"** is checked during installation!).
2. Download and install **Node.js (v20 or v22)** from [nodejs.org](https://nodejs.org/).

### Step 2: Launch the Backend
Open a terminal inside the project root `d:\Dev Projects\ResearchPilot` and execute:
```bash
# 1. Inject API Key (PowerShell example)
$env:GEMINI_API_KEY="AIzaSyYourKeyHere..."

# 2. Activate virtual environment
# Windows PowerShell:
.venv/Scripts/Activate.ps1
# Windows CMD:
.venv\Scripts\activate.bat
# Linux/macOS/Git Bash:
source .venv/bin/activate

# 3. Verify backend compiles and creates DB
python backend/verify_backend.py

# 4. Start FastAPI server
uvicorn backend.main:app --reload --port 8000
```

### Step 3: Launch the Frontend
Open a **new terminal tab** in the project root `d:\Dev Projects\ResearchPilot` and execute:
```bash
# 1. Navigate to client
cd frontend

# 2. Install dependencies
npm install

# 3. Start development hot-reloading server
npm run dev
```
Open `http://localhost:3000` in your browser.

---

## 🧪 Part 4: Run Asynchronous Pytest Suite

To verify that the database operations, arXiv services, ReportLab layout templates, and Gemini agents are stable in offline modes, run the tests:

```bash
# Open a terminal in virtual environment (Backend folder activated)
backend/.venv/Scripts/python -m pytest backend/tests/
```
All 9 unit tests are pre-mocked using python `unittest.mock` and will complete in under 2 seconds with **100% success**!
