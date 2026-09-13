# UU LLM Guest Lecture

Teaching material for a guest lecture on building applications with LLMs, authored by Dmitrijs Kass. It pairs the lecture slides with a hands-on Jupyter notebook that works through a single running case study: a natural-language-to-SQL (NL2SQL) assistant, used to motivate function/tool calling, structured output, few-shot prompting, and retrieval-augmented generation (RAG).

## What's in the notebook

`uu_guest_lecture_llms.ipynb` walks through, in order:

- **Function (tool) calling** - routing a user's question to one of a fixed set of categories (e.g. "needs SQL" vs. "needs help") by handing Claude a set of tools and letting it choose.
- **Structured output** - the same tool-calling mechanism restricted to exactly one tool, used to reliably infer which database table(s) a question needs.
- **Few-shot prompting** - teaching Claude a database's real naming conventions from a couple of examples, for SQL generation.
- **RAG** - loading a PDF, chunking it, embedding it locally, and answering questions grounded in the retrieved text instead of the model's own assumptions.

## Requirements

The notebook calls the Anthropic API, which requires a **paid Anthropic account** - no other paid API keys are needed (embeddings for the RAG section run locally, for free).

## Setup

1. Install [`uv`](https://docs.astral.sh/uv/) (see its [installation guide](https://docs.astral.sh/uv/getting-started/installation/) if you don't have it yet).
2. Create the virtual environment:
   ```bash
   uv venv
   ```
3. Install the project's dependencies into it:
   ```bash
   uv sync
   ```
4. Create a `.env` file in the repo root with your Anthropic API key:
   ```
   ANTHROPIC_API_KEY=sk-ant-...
   ```
5. Launch the notebook using that environment:
   ```bash
   uv run jupyter notebook
   ```
