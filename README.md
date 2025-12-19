# Realtime AI Backend (WebSockets + Supabase)

## 📌 Project Overview
This submission is a high-performance, asynchronous backend designed to simulate a real-time conversational agent. It demonstrates core backend engineering patterns including **bi-directional WebSockets**, **LLM token streaming**, **complex tool execution**, and **automated data persistence**.

**Key Features Implemented:**
* **Real-time Streaming:** Immediate token-by-token AI responses via WebSockets.
* **Complex Tooling:** A custom "Server Time" tool that triggers internal logic instead of LLM generation.
* **Automated Summarization:** A background task that auto-generates and saves a session summary immediately upon disconnection.
* **Persistence:** Granular event logging to a remote PostgreSQL database (Supabase).

---

## ⚠️ Important: File Naming
For the commands below to work, please ensure the backend python file is named exactly:
**`main.py`**

---

## 🚀 Setup & Run Instructions

The environment is pre-configured with live API keys and a database connection. You do not need to set up local environment variables.

### Step 1: Install Dependencies
Open your terminal/command prompt in this folder and run:
```bash
pip install -r requirements.txt

Step 2: Start the Backend Server
Run the following command to start the Uvicorn server:
python -m uvicorn main:app --reload

You should see a success message indicating the server is running at http://127.0.0.1:8000.

Step 3: Launch the Frontend
Simply double-click the index.html file included in this repository to open it in your web browser.

⚙️ Technical Details (Reference Only)
Database Schema: The application connects to a live Supabase instance. For reference, the schema used is:

sessions: Stores session_id, start_time, end_time, and summary.

logs: Stores granular chat events (sender, message, timestamp).

Model: Uses gemini-2.5-flash for high-speed, low-latency text generation.

⚙️ Technical Stack
Backend Framework: FastAPI (Python)

AI Model: Google Gemini 2.5 Flash

Database: Supabase (PostgreSQL)

Protocol: WebSockets (ws://)