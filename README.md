# symbion0130

Solo developer. Async Python, applied LLM systems, end-to-end ownership.

## Currently

Building a personal AI assistant and behavioral-safety research
harness in Python — ~8,800 lines. Multi-provider LLM orchestration
(Anthropic, OpenAI, Ollama), judge-model safety layer, offline eval
harness with rule-based grading, hybrid BM25 + cosine retrieval,
async-first pipelines with circuit breakers, FastAPI + WebSocket web
UI, Electron desktop shell. Codebase is private. Extracting reusable
pieces into standalone public repos — links will appear here.

## Stack

Python (async end-to-end), FastAPI + WebSockets, SQLite, Anthropic /
OpenAI / Ollama, Electron, Playwright (browser-level verification),
Windows-first packaging.

## Approach

Designing for graceful degradation — every external call is wrapped,
nothing in the hot path blocks. Treating prompts as testable artifacts:
~120-entry rule-based eval suite that never asks one LLM to grade
another. DB migrations additive only; logs append-only.

## Contact

symbion.0130@gmail.com
