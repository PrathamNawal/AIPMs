# Build AI: A PM's Guide

Learn to build AI products, step by step. An interactive learning tool with hands-on labs, case studies, and decision frameworks.

**Now supports both Anthropic Claude and local Ollama!** ⭐

## About

This single-page app contains 6 hands-on labs covering:

1. **Lab 1: How LLMs Actually Work** — Temperature, top-p, token generation, limitations
2. **Lab 2: Context Windows & Memory** — Token counting, memory strategies, context limits
3. **Lab 3: Cost & Latency Tradeoffs** — Model comparison, pricing, cost calculations
4. **Lab 4: Grounding & Guardrails** — RAG (Retrieval-Augmented Generation), safety
5. **Lab 5: Evaluation & Testing** — LLM-as-judge, A/B testing, metrics
6. **Lab 6: Agents & Tool Use** — Agent loops, tool orchestration, iteration

## Running Locally

### Prerequisites
- Node.js 18+
- **Either:**
  - Anthropic API key (free trial at [console.anthropic.com](https://console.anthropic.com))
  - **OR** Ollama installed locally ([ollama.ai](https://ollama.ai))

### Setup

```bash
# Install dependencies
npm install

# Start dev server (http://localhost:5173)
npm run dev
```

### First Run
1. Click "Set API" button in header
2. Choose your provider:
   - **Anthropic Claude** — Most capable, paid (free trial available)
   - **Ollama (Local)** — Free, runs on your machine
3. Enter credentials and click "Save & Continue"
4. Start learning!

See [OLLAMA_SETUP.md](./OLLAMA_SETUP.md) for detailed Ollama instructions.

### Building for Production

```bash
# Build static files
npm run build

# Output in ./dist/ — ready for Netlify, GitHub Pages, etc.
```

## How It Works

- **API Key**: Stored locally in browser storage only. Never sent to our servers. You control all API calls.
- **Direct API Calls**: All Claude API calls go directly from your browser using your API key.
- **No Backend**: This is purely a frontend app. Deploy anywhere (Netlify, GitHub Pages, Vercel).

## Deployment

### GitHub Pages

```bash
# Build
npm run build

# Deploy ./dist to GitHub Pages
# (Use your repo's deploy action or push ./dist to gh-pages branch)
```

### Netlify

```bash
# Netlify detects Vite automatically
# Connect your repo to Netlify, it will:
# 1. Run: npm run build
# 2. Deploy ./dist
```

## Tech Stack

- **React 19** — UI framework
- **Vite 8** — Build tool (fast, light)
- **Anthropic Claude API** — LLM calls

## License

MIT
