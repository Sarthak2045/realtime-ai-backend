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

**Note to Reviewer:** The project is pre-configured with active API keys for immediate testing. However, the instructions below include the database setup step so you can review the schema or deploy it to your own instance if desired.

### Step 1: Install Dependencies
Open your terminal/command prompt in this folder and run:
```bash
pip install -r requirements.txt

Step 2: Database Setup (Supabase)
If you are using the pre-configured keys in main.py, you can skip this. If you wish to review the table structure or set up your own database, follow these instructions:

Open the file schema.sql provided in this repository.

Copy the entire content of the file.

Go to your Supabase Dashboard -> SQL Editor.

Paste the code and click Run.

This will create the sessions table (for metadata) and the logs table (for chat history).

Step 3: Start the Backend Server
Run the following command to start the Uvicorn server:

python -m uvicorn main:app --reload

You should see a success message indicating the server is running at http://127.0.0.1:8000.

Step 4: Launch the Frontend
Simply double-click the index.html file included in this repository to open it in your web browser.

🧪 How to Test the Features
Once the app is running, try the following interactions to verify the assignment requirements:

Verify Streaming: * Type "Hello" in the chat.

Result: You will see the AI response stream in real-time (token by token).

Verify Complex Tool Interaction:

Ask "What time is it?".

Result: The AI will detect the intent, execute the internal get_server_time() Python function, and return the precise server time.

Verify Automation & Persistence:

Click the "End Session" button in the top right.

Result: The WebSocket will close, and the backend logs will show that a summary is being generated and saved to the Supabase database automatically.

⚙️ Technical Stack
Backend Framework: FastAPI (Python)

AI Model: Google Gemini 2.5 Flash

Database: Supabase (PostgreSQL)

Protocol: WebSockets (ws://)