# Llama Chatbot

An AI-powered chatbot with document understanding, web search, and persistent memory. Supports PDF/TXT file uploads for contextual Q&A, real-time web search via Tavily, and long-term user memory extraction.

Built with Flask, Groq LLM, Docling, and Supabase (PostgreSQL). Deployable on Render or Vercel.

## Features

- **Document Q&A** — Upload PDF or TXT files; the AI reads and answers from the document content using Docling for accurate text extraction (including scanned PDFs via OCR).
- **Web Search** — Toggle real-time web search (powered by Tavily API) to get up-to-date answers.
- **Conversation Memory** — Short-term history within each chat and long-term user facts extracted and stored automatically.
- **Mobile UI** — Responsive design with sidebar drawer, hamburger menu, and smooth animations.
- **Multi-model ready** — Uses Groq API (`openai/gpt-oss-120b`), easily swappable to any Groq-hosted model.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Flask |
| LLM | Groq API (Llama / OpenAI models) |
| Document Extraction | Docling (AI-powered PDF parsing with OCR) |
| Vector Store | None — full document context injected into LLM prompt |
| Database | Supabase (PostgreSQL) / SQLite (local dev) |
| Auth | Flask-Login, Werkzeug |
| Web Search | Tavily API |
| Frontend | Vanilla JavaScript, HTML, CSS |
| Deployment | Render (gunicorn) / Vercel (serverless) |

## Quick Start

```bash
git clone https://github.com/karanamabhiram117-wq/llama-chatbot.git
cd llama-chatbot
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Create a `.env` file:

```env
GROQ_API_KEY=your_groq_key
TAVILY_API_KEY=your_tavily_key
SECRET_KEY=your_secret_here
# DATABASE_URL=postgresql://...  (optional — uses SQLite locally if unset)
```

Run:

```bash
python app.py
```

Open `http://localhost:5000`.

## Project Structure

```
├── app.py                 # Flask app (Supabase PostgreSQL, for Render)
├── api/index.py           # Flask app (SQLite, for Vercel)
├── templates/
│   ├── index.html         # Chat UI (Render)
│   ├── login.html
│   └── register.html
├── api/templates/         # Mirrored templates for Vercel
├── requirements.txt
├── render.yaml
└── vercel.json
```

## Deployment

### Render

`app.py` with Supabase PostgreSQL. Set environment variables (`DATABASE_URL`, `GROQ_API_KEY`, etc.) in Render dashboard.

### Vercel

`api/index.py` with SQLite. Deploy as a Python serverless function.

## License

MIT
