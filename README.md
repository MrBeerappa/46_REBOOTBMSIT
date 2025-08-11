# Sentinel-AI: Your Autonomous OS Co-Pilot


An intelligent, voice-activated agent for automating complex tasks and streamlining your digital workflow directly from your terminal.
<br>
Sentinel-AI is an advanced autonomous agent designed to serve as a powerful co-pilot for your operating system. It bridges the gap between natural language and complex system-level actions, allowing you to execute tasks, manage communications, and control your digital environment through simple, intuitive commands. By leveraging a sophisticated multi-agent architecture powered by LangGraph, Sentinel-AI goes beyond simple scripting to understand intent, plan multi-step operations, and interact with a variety of system tools and external APIs. This project aims to reduce the friction of repetitive digital chores and empower users to achieve more with less effort, transforming the way you interact with your machine.

📖 Table of Contents

✨ Core Features
🏗️ System Architecture
🛠️ Technology Stack
⚙️ Installation & Configuration
🚀 Usage & Command Reference

✨ Core Features

Sentinel-AI is equipped with a suite of powerful features designed for modern productivity and automation. The feature set is built to be both highly functional and easily extensible.

🗣️ Natural Language Command Interface

Interact with your OS using natural, conversational language. Sentinel-AI features:
Wake Word Detection: Uses Porcupine to listen for the "Hey Sentinel" hotword, allowing for hands-free activation.
Speech-to-Text (STT): Employs Google Speech Recognizer to accurately understand your spoken commands.
Text-to-Speech (TTS): Provides lifelike audible feedback and responses for a seamless conversational experience.

🧠 Multi-Agent Orchestration Engine

At its core, Sentinel-AI utilizes a sophisticated orchestration engine built with LangGraph that intelligently delegates tasks to specialized agents. When a complex command is received, the orchestrator analyzes the user's intent, breaks the request down into a logical, cyclical graph of operations, and assigns each step to the most appropriate agent or tool. This modular design allows it to handle complex, multi-step workflows that a monolithic script could not, such as "Find the latest project summary in my downloads, draft an email to the project team with the summary attached, and schedule a follow-up meeting for Friday."

🔧 Extensible OS Automation Toolkit

Go beyond simple commands with a rich set of built-in tools for real-world productivity. This toolkit is designed to be a practical foundation for day-to-day tasks, with the ability for developers to easily add more.
Email Management: Compose and send emails through your configured account directly via voice command.
Calendar & Meeting Scheduling: Instantly create Google Meet events and schedule appointments without opening a browser.
Hardware Control: Programmatically toggle system-level settings like Bluetooth and Wi-Fi.
File System Operations: Execute advanced file operations, such as searching for documents, organizing files, and performing routine system cleanup.

🔐 Secure Credential Management

Security is a foundational principle of Sentinel-AI. The agent integrates securely with your system's environment variables (.env file) to manage API keys, passwords, and other sensitive credentials. This practice ensures that your private information is never hard-coded into the source code or exposed in logs.

🏗️ System Architecture

Understanding the architecture of Sentinel-AI is key for both advanced users and developers. The system is designed for modularity, scalability, and ease of extension using a stateful, graph-based approach.

Component Breakdown

The logical flow of a command through the Sentinel-AI system involves several key components working in concert:
Input Handler: This is the entry point for all user interaction. It continuously listens for the wake word (Porcupine). Once activated, it captures audio and uses the Google Speech Recognizer to convert spoken words into a normalized text string.
Core Orchestrator (The "Brain"): This is the central nervous system of Sentinel-AI, built on LangGraph. It receives the command and leverages a locally-hosted Llama 3 model via Ollama to perform intent recognition and task planning. LangGraph defines the task as a stateful graph, allowing for complex, cyclical reasoning and dynamic routing between different tools and agents.
Agent & Tool Registry: This component serves as a directory of all available capabilities.
Tools: Simple, stateless functions designed to perform a single, atomic action (e.g., send_email, set_bluetooth_state).
Agents: More complex, stateful workers for multi-step tasks that may require memory or context.
Execution Engine: Once the Core Orchestrator formulates a plan, the Execution Engine invokes the selected tools. It securely retrieves any required parameters (like API keys) from the environment, executes the function, and captures the output.
Output Handler: This is the final component. It receives the result from the Execution Engine, formats it for human consumption, and presents it back to the user as an audible response generated by the Text-to-Speech (TTS) engine.

🛠️ Technology Stack

Sentinel-AI is constructed using a carefully selected stack of modern, powerful technologies chosen for their performance and robustness.
Core Language: Python (3.10+)
Environment Manager: Pip with venv
AI & Machine Learning:
Orchestration/Agents: LangGraph, for creating stateful, multi-agent applications.
LLM Provider: Ollama serving Llama 3 for local, private, and powerful language understanding and reasoning.
Wake Word Detection: Porcupine for highly accurate and efficient hotword detection.
Speech-to-Text (STT): Google Speech Recognizer for reliable voice command transcription.
Text-to-Speech (TTS): A selected TTS engine (e.g., Coqui TTS, ElevenLabs) for generating natural-sounding voice responses.
Framework & APIs:
External Service APIs: Integrations with Google Gmail API and Google Calendar API.
Configuration Management:
Pydantic-Settings for managing environment variables in a type-safe and validated manner.

⚙️ Installation & Configuration

Follow these steps carefully to install and configure Sentinel-AI on your local machine.

Prerequisites

Python (version 3.10 or newer).
Git for cloning the repository.
An audio input device (microphone).
Ollama installed and running with the Llama 3 model pulled (ollama pull llama3).

Hardware Requirements

To run the Llama 3 model effectively, the following hardware is recommended as a minimum:
GPU: NVIDIA RTX 4060 or any equivalent GPU with at least 6GB of VRAM.

1. Clone the Repository

Open your terminal and run the following command:

Bash


git clone https://github.com/AsimAftab/Sentinel-AI-Backend.git
cd Sentinel-AI-Backend



2. Set Up a Virtual Environment

Isolate the project's dependencies to avoid conflicts with your global Python installation.
On macOS and Linux:
Bash
python3 -m venv .venv
source .venv/bin/activate


On Windows:
Bash
python -m venv .venv
.venv\Scripts\activate



3. Install Dependencies

With the virtual environment activated, install all required Python packages:

Bash


pip install -r requirements.txt



4. Configure Environment Variables

Sentinel-AI requires API keys to connect to external services.
First, copy the example environment file:

Bash


cp .env.example .env


Next, open the newly created .env file in a text editor and fill in your API keys and other settings.
IMPORTANT: The .env file contains sensitive information. It is already listed in .gitignore, and you must NEVER commit it to version control.

🚀 Usage & Command Reference

Once Sentinel-AI is installed, configured, and Ollama is running, you can start the agent.

Running the Agent

To start the agent in its primary interactive voice mode, run the following command from the project's root directory:

Bash


python main.py


Wait for the agent to initialize and display a message like [INFO] Sentinel-AI is listening.... Once you see this, you can activate it by saying the wake word.

Example Voice Commands

Activate:"Hey Sentinel..."
Send an Email:"...send an email to Jane Doe at jane.doe@example.com. The subject is 'Project Update' and the body is 'Hi Jane, just wanted to let you know the project is on track for our deadline.'"
Schedule a Meeting:"...create a Google Meet named 'Urgent Sync' for tomorrow at 10 AM with john.smith@example.com."
Control Hardware:"...turn my Bluetooth off."
