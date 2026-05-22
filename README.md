# symbion0130

Solo developer. Async Python, applied LLM systems, end-to-end ownership.

## Currently

Building a personal AI assistant and behavioral-safety research
harness in Python — ~8,800 lines. Multi-provider LLM orchestration
(Anthropic, OpenAI, Ollama), judge-model safety layer, offline eval
harness with rule-based grading, hybrid BM25 + cosine retrieval,
async-first pipelines with circuit breakers, FastAPI + WebSocket web
UI, Electron desktop shell. Codebase is private. Reusable pieces
extracted as standalone libraries — see below.

## Open source

Each is a focused library with tests, MIT-licensed, `pip install`-able:

- **[llm-evals](https://github.com/symbion0130/llm-evals)** — rule-based grading for LLM applications. Deterministic, cheap, fast. Never asks one LLM to grade another. Clause-aware negation, quote-aware skip, tool-judgment rules.
- **[pyresilience](https://github.com/symbion0130/pyresilience)** — async resilience primitives (circuit breaker, rate limiter, retry) sized for LLM provider failure modes. 529-aware `.trip()` path skips the retry budget on capacity errors.
- **[safe-llm-tools](https://github.com/symbion0130/safe-llm-tools)** — three security primitives every LLM-agent codebase needs: math without `eval`, URL fetch without SSRF, file ops without path traversal.
- **[hybrid-retrieve](https://github.com/symbion0130/hybrid-retrieve)** — BM25 + cosine hybrid retrieval with multiplicative (not additive) recency decay, so a fresh-but-unrelated doc never beats an old-but-on-topic one. Pure Python, no FAISS.
- **[mcp-stdio-client](https://github.com/symbion0130/mcp-stdio-client)** — async Python manager for stdio-transport MCP servers. Pool management, tool namespacing, clean shutdown via `AsyncExitStack`.

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
