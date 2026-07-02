# AstroVoxis 🚀

AstroVoxis is a next-generation AI voice assistant that leverages the real-time capabilities of LiveKit combined with the reasoning power of Google Gemini and the lightning-fast voice models from OpenAI.

## 🧠 Architecture Overview

AstroVoxis uses a modular architecture for real-time voice processing:

```mermaid
graph TD
    User((User)) <-->|WebRTC (Audio)| LiveKit[LiveKit Cloud]
    LiveKit <-->|WebRTC (Audio)| Agent[AstroVoxis Agent Worker]
    
    subgraph AI Processing Pipeline
        Agent -->|1. Raw Audio| VAD[Silero VAD]
        VAD -->|2. Speech Detected| STT[OpenAI STT<br/>Speech-to-Text]
        STT -->|3. Transcribed Text| LLM[Google Gemini<br/>Core Brain]
        LLM -->|4. Response Text| TTS[OpenAI TTS<br/>Text-to-Speech]
        TTS -->|5. Synthesized Audio| Agent
    end

    subgraph Function Calling / Tools
        LLM -.->|Calls API| API[api.py<br/>Smart Home Tools]
        API -.->|Returns Data| LLM
    end
    
    classDef default fill:#1e1e1e,stroke:#333,stroke-width:2px,color:#fff;
    classDef user fill:#4a90e2,stroke:#2b5e9b,stroke-width:2px,color:#fff;
    classDef livekit fill:#e53935,stroke:#b71c1c,stroke-width:2px,color:#fff;
    classDef openai fill:#00a67e,stroke:#007a5d,stroke-width:2px,color:#fff;
    classDef gemini fill:#f4b400,stroke:#f57f17,stroke-width:2px,color:#fff;
    classDef api fill:#8e24aa,stroke:#6a1b9a,stroke-width:2px,color:#fff;
    
    User:::user
    LiveKit:::livekit
    STT:::openai
    TTS:::openai
    LLM:::gemini
    API:::api
```

## ✨ Key Features

- **Ultra-Low Latency:** Streaming audio via LiveKit WebRTC ensures natural conversational flow.
- **Smart Interruptions:** Silero VAD seamlessly detects when the user speaks and interrupts the AI gracefully.
- **Function Calling:** Connects directly to external APIs (e.g., Temperature Control logic) via Gemini's tool-calling capabilities.
- **High-Quality Voice:** OpenAI's robust Text-to-Speech engines provide lifelike and emotive responses.

## 🛠️ Setup & Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/SihanUdayaratna03/AstroVoxis.git
   cd AstroVoxis
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv ai
   .\ai\Scripts\Activate.ps1
   ```

3. **Install the dependencies:**
   ```bash
   pip install livekit-agents livekit-plugins-google livekit-plugins-openai livekit-plugins-silero python-dotenv
   ```

4. **Configure your Environment Variables:**
   Rename `.env.example` to `.env` and fill in your keys:
   ```env
   LIVEKIT_URL="wss://your-livekit-url"
   LIVEKIT_API_KEY="your-api-key"
   LIVEKIT_API_SECRET="your-api-secret"
   GEMINI_API_KEY="your-gemini-key"
   OPENAI_API_KEY="your-openai-key"
   LIVEKIT_WORKER_PORT=8082
   ```

## 🚀 Running the Agent

Start the background worker:
```bash
python main.py start
```

Once the worker starts, head over to your **LiveKit Sandbox/Console**, select your agent from the testing dropdown, and connect to the room to start chatting with AstroVoxis!
