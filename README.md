# VoiceAgent

VoiceAgent is a Python-based voice assistant bridge for a pharmacy support workflow. It runs a local WebSocket server that forwards Twilio audio events to the Deepgram Conversation API and responds with pharmacy-related function calls.

## Key Features

- Local WebSocket service on `localhost:5000` for Twilio integration.
- Uses Deepgram for speech/audio handling and OpenAI-style function-calling agent behavior.
- Provides pharmacy assistant capabilities:
  - `get_drug_info` for drug details and pricing.
  - `place_order` for placing orders with predefined drug quantities.
  - `lookup_order` for checking order status by ID.
- In-memory pharmacy database in `pharmacy_functions.py`.

## Requirements

- Python 3.12 or newer
- `python-dotenv`
- `websockets`

## Installation

1. Create and activate a Python virtual environment.
   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```
2. Install dependencies.
   ```powershell
   python -m pip install -r requirements.txt
   ```
   If `requirements.txt` is not available, install directly:
   ```powershell
   python -m pip install python-dotenv websockets
   ```

## Configuration

1. Create a `.env` file in the project root.
2. Set your Deepgram API key:
   ```text
   DEEPGRAM_API_KEY=your_deepgram_api_key_here
   ```
3. Review `config.json` for speech, agent, and function settings.

## Running the Project

Start the server with:
```powershell
python main.py
```

The server listens on `localhost:5000` and expects Twilio WebSocket events. It uses `config.json` and the Deepgram API to process audio and function calls.

## Project Files

- `main.py` - Main application logic. Connects to Deepgram, handles Twilio audio streams, and dispatches function calls.
- `pharmacy_functions.py` - Contains the pharmacy function definitions and in-memory database.
- `config.json` - Deepgram and agent configuration, including speech settings, prompt, and function definitions.
- `pyproject.toml` - Python packaging metadata and dependencies.

## Function Behavior

- `get_drug_info(drug_name)` - Returns details for supported drugs.
- `place_order(customer_name, drug_name)` - Creates a new in-memory order and returns a confirmation.
- `lookup_order(order_id)` - Retrieves an existing order by ID.

## Notes

- The current implementation uses an in-memory database, so orders are lost when the application stops.
- Ensure your Deepgram API key is valid and the environment is activated before running.


