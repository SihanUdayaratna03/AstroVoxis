# AstroVoxis

AstroVoxis is an AI voice assistant powered by LiveKit and Google Gemini. It utilizes OpenAI for fast and accurate Speech-to-Text (STT) and Text-to-Speech (TTS), while relying on Google's Gemini language model as the core conversational intelligence.

## Features
- Voice Activity Detection (VAD) using LiveKit's built-in Silero
- High quality STT and TTS using OpenAI Whisper and OpenAI TTS
- Conversational intelligence via Google Gemini
- Function calling tools (e.g. Temperature Control)

## Setup
1. Clone the repository
2. Run `python -m venv ai`
3. Activate the environment `.\ai\Scripts\Activate.ps1`
4. Install dependencies: `pip install -r requirements.txt` (or install manually)
5. Copy `.env.example` to `.env` and fill in your keys.
6. Start the agent: `python main.py start`
