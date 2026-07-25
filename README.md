# Llama Chatbot

An AI-powered chatbot with document understanding, web search, and persistent memory. Supports PDF/TXT file uploads for contextual Q&A, real-time web search via Tavily, and long-term user memory extraction.

Built with Flask, Groq LLM, Docling, and PostgreSQL.

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
| Database | PostgreSQL / SQLite (local dev) |
| Auth | Flask-Login, Werkzeug |
| Web Search | Tavily API |
| Frontend | Vanilla JavaScript, HTML, CSS |
| Deployment | Render (gunicorn) |

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
GROQ_API_KEY=your_groq_api_key
TAVILY_API_KEY=your_tavily_api_key
SECRET_KEY=your_secret_key
DATABASE_URL=postgresql://...  # Optional — uses SQLite locally if not set
```

Run:

```bash
python app.py
```

Open `http://localhost:5000`.

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `GROQ_API_KEY` | Yes | API key for Groq LLM access |
| `TAVILY_API_KEY` | No | API key for web search feature |
| `SECRET_KEY` | No | Flask session secret (auto-generated if not set) |
| `DATABASE_URL` | No | PostgreSQL connection string (uses SQLite locally if not set) |

## Project Structure

```
├── app.py                 # Flask app (PostgreSQL, for Render)
├── api/index.py           # Flask app (SQLite, for Vercel)
├── templates/
│   ├── index.html         # Chat UI
│   ├── login.html
│   └── register.html
├── api/templates/         # Mirrored templates for Vercel
├── requirements.txt
├── render.yaml
└── README.md
```

## Deployment

### Render

Deploy `app.py` with PostgreSQL. Set the required environment variables in the Render dashboard.

## License

MIT
