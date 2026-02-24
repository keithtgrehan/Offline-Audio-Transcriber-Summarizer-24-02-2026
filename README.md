# Offline-Audio-Transcriber-Summarizer-24-02-2026
# Offline Audio Transcriber & Summarizer (OATS)

Local-first pipeline:
Audio file → offline transcription (faster-whisper) → deterministic checks → validated local LLM extraction (Ollama) → structured JSON + markdown report.

## Goals
- Fully offline transcription + action-item extraction
- Deterministic-first, LLM only when gated + schema-validated
- Reproducible run bundles (inputs, config, transcript, extraction, report)

## Stack
- ASR: `faster-whisper`
- Audio IO: `soundfile`
- Local LLM: `ollama` (Python client)
- Validation: `pydantic v2`
- CLI UX: `rich`

## Quickstart
```bash
git clone https://github.com/keithtgrehan/Offline-Audio-Transcriber-Summarizer-24-02-2026.git
cd Offline-Audio-Transcriber-Summarizer-24-02-2026
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install -e .

# ensure Ollama is running locally, and pull the default model
ollama pull llama3.2:3b

# run
python -m oats path/to/audio.wav --mode validated_llm --sentiment off
