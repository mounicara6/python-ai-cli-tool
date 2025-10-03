Python AI CLI Tool
==================

A small Python CLI that talks to a locally running Ollama server (default: http://localhost:11434).
The CLI supports two commands:

1. list  - list models available locally (GET /api/tags)
2. run   - run a prompt against a chosen model (POST /api/generate)

Requirements
------------
- Python 3.8+
- Install dependencies: pip install -r requirements.txt

Usage
-----
# show help
python -m ai_cli --help

# list local models
python -m ai_cli list

# run a prompt (model name must match one from `list`)
python -m ai_cli run --model llama3.2 "Explain HTTP in simple terms"

Notes
-----
- The tool expects an Ollama server listening on http://localhost:11434 (the default for `ollama serve`).
- This project uses the official Ollama REST endpoints documented at https://docs.ollama.com/api
- The code is intentionally straightforward and written to look like a normal developer project.
