# Sentinel-AI: Your Autonomous OS Co-Pilot

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-brightgreen)](https://www.python.org/downloads/)
[![LangGraph](https://img.shields.io/badge/Orchestration-LangGraph-orange)](https://www.langchain.com/langgraph)
[![Ollama](https://img.shields.io/badge/LLM-Llama%203-blueviolet)](https://ollama.ai/)
[![Status](https://img.shields.io/badge/Status-Active-success)]()

**Sentinel-AI** is an intelligent, voice-activated assistant that automates complex tasks and streamlines your digital workflow directly from your terminal.  
It acts as a bridge between natural language and system-level operations, enabling you to manage files, schedule meetings, send emails, control hardware, and more using simple conversational commands.  

Powered by **LangGraph**, Sentinel-AI can plan and execute multi-step operations, integrating seamlessly with system tools and external APIs.  
Think of it as your personal OS co-pilot always ready to help you work faster and smarter.

---

## ✨ Key Features

### 🗣 Natural Language OS Control
- **Wake Word Detection** with [Porcupine](https://picovoice.ai/products/porcupine/) — hands-free activation using "Hey Sentinel".
- **Speech-to-Text** via Google Speech Recognizer for accurate command recognition.
- **Text-to-Speech** for lifelike audible responses.

### 🧠 Multi-Agent Orchestration
- Built with **LangGraph** for intelligent task planning and routing.
- Handles **multi-step workflows** such as:
  > “Find the latest project summary in my Downloads, draft an email to the team, and schedule a follow-up meeting for Friday.”

### 🔧 OS Automation Toolkit

- **Calendar Scheduling** — create Google Meet events & appointments.
- **Hardware Control** — toggle Bluetooth, Wi-Fi, etc.
- **File Operations** — search, organize, and clean up files.

### 🔐 Secure Credential Management
- Stores API keys and credentials securely using `.env` and [Pydantic Settings](https://docs.pydantic.dev/latest/).

---

## 🏗 Architecture Overview

**Core Components:**
- **Input Handler** — listens for wake word, converts speech to text.
- **Core Orchestrator** — intent recognition & planning via **Llama 3** (Ollama).
- **Agents & Tools** — stateless tools and stateful agents for task execution.
- **Execution Engine** — runs tools securely using environment variables.
- **Output Handler** — formats and speaks the result back to the user.

---

## 🛠 Tech Stack

- **Language:** Python 3.10+
- **LLM:** Llama 3 via [Ollama](https://ollama.ai/)
- **Voice Interface:** Porcupine (wake word), Google Speech Recognizer (STT)
- **Orchestration:** LangGraph
- **APIs:** Gmail API, Google Calendar API, Travily API Key
- **Config:** Pydantic Settings + `.env`

---

## ⚙ Installation

### Prerequisites
- Python 3.10+
- Git
- Microphone
- [Ollama](https://ollama.ai/) installed with Llama 3 model (`ollama pull llama3`)
- Recommended: NVIDIA RTX 4060+ GPU (6GB+ VRAM)

### 1. Clone Repository
```bash
git clone https://github.com/MrBeerappa/46_REBOOTBMSIT.git
cd Sentinel-AI-Backend
python3 -m venv .venv
source .venv/bin/activate     # macOS/Linux
# OR
.venv\Scripts\activate        # Windows

pip install -r requirements.txt

cp .env.example .env
python main.py

