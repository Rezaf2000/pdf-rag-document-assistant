# PDF RAG Document Assistant

A compact Streamlit question-answering app for locally indexed PDF documents. The implementation uses LangChain, Chroma, sentence-transformer embeddings, and an Ollama `llama3.2` model.

## Problem and architecture

A language model cannot answer from private PDFs without context. `chatbot.py` loads files from `data/`, splits text into overlapping chunks, embeds them with `all-MiniLM-L6-v2`, and persists them in Chroma. For each question it retrieves four chunks, builds a context-grounded prompt, and generates an answer through Ollama.

## Repository map

| Path | Purpose |
| --- | --- |
| `chatbot.py` | PDF loading, indexing, retrieval, prompting, and Streamlit UI |
| `data/` | Place local PDF documents here |
| `requirements.txt` | Python dependencies |

## Existing upstream interface

![Upstream RAG interface](https://github.com/user-attachments/assets/03a48938-0bfc-4599-bd2a-29ce358ea403)

The [original README](UPSTREAM_README.md) contains a second retrieval screenshot. These are upstream UI captures, not evidence of a fresh run or a measured answer-quality benchmark.

## Usage

Install `requirements.txt`, put PDFs in `data/`, make the Ollama `llama3.2` model available, then use `streamlit run chatbot.py`. The original README mentions an OpenAI key, but the checked-in `chatbot.py` actually instantiates Ollama. This fork documents the checked-in code.

## Source and license

Based on and adapted from [ambrose-kutti/RAG](https://github.com/ambrose-kutti/RAG). The [original documentation](UPSTREAM_README.md), code, screenshots, and [MIT license](LICENSE) are retained.