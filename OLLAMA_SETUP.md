# Using Ollama with AI Concepts Playground

Now the app supports both **Anthropic Claude** and **local Ollama**. Pick whichever you prefer.

## Option 1: Use Anthropic Claude (Recommended)

### Setup

1. Get free API key: https://console.anthropic.com
2. Open the app: http://localhost:5173
3. Click "Set API" in header
4. Select **Anthropic Claude**
5. Paste your API key
6. Start exploring!

**Pros:**
- Most capable models (Haiku, Sonnet, Opus)
- Real pricing data available in Lab 3
- No local setup required

**Cons:**
- Costs money (but has free trial)
- Requires internet

---

## Option 2: Use Ollama (Local & Free)

### Setup

#### 1. Install Ollama

Download from https://ollama.ai

#### 2. Run Ollama

```bash
ollama serve
```

This starts Ollama on `http://localhost:11434`

#### 3. Pull a Model

In another terminal:

```bash
# Recommended for learning (fast, good quality)
ollama pull mistral

# Or try these
ollama pull llama2
ollama pull neural-chat
ollama pull dolphin-mixtral
```

#### 4. Open the App

http://localhost:5173

#### 5. Configure App

1. Click "Set API" in header
2. Select **Ollama (Local)**
3. Enter URL: `http://localhost:11434` (or your custom URL)
4. Click "Save & Continue"

#### 6. Pick Your Model

In each lab, the **Model** dropdown now shows available Ollama models:
- Mistral
- Llama 2
- Neural Chat
- (any other models you pulled)

**Pros:**
- Completely free (after one-time download)
- No internet required
- Privacy (data stays local)
- Fast (GPU acceleration if available)

**Cons:**
- Need 8GB+ RAM + storage per model
- Slower than cloud (depends on GPU)
- Cost calculator won't show real pricing (free models)

---

## Switching Between Claude and Ollama

1. Click the "✓ Claude Ready" (or "✓ Ollama Ready") button in header
2. Choose your provider
3. Re-enter credentials
4. Click "Save & Continue"

The app stores your preference in browser localStorage.

---

## Troubleshooting Ollama

### "Connection refused" error
- Make sure Ollama is running: `ollama serve`
- Check URL is correct (default: `http://localhost:11434`)
- Try a different port if 11434 is taken

### Model not found
- Pull the model first: `ollama pull <model-name>`
- Check available models: `ollama list`

### App is slow
- Ollama might not have GPU acceleration
- Check: `ollama show llama2` for GPU info
- Mistral is usually faster than Llama 2

### Out of memory
- Models require 4-8GB each
- Use smaller models (Mistral ~7B is a good balance)
- Close other apps

---

## Recommended Models

| Model | Size | Speed | Quality | RAM Needed |
|-------|------|-------|---------|-----------|
| Mistral | 7B | Fast | Very Good | 5GB |
| Llama 2 | 7B | Medium | Good | 5GB |
| Neural Chat | 7B | Medium | Good | 5GB |
| Dolphin Mixtral | 8x7B | Slow | Excellent | 20GB |

For learning: **Mistral** is the best balance.

---

## Lab-by-Lab Differences (Claude vs Ollama)

### Lab 1: LLM Basics
- **Claude:** Shows real token counts and latency
- **Ollama:** Token estimates (all models ~same, can't customize top-p/top-k in this version)

### Lab 2: Context Window
- **Claude:** Full 200k context window
- **Ollama:** Depends on model (Mistral = 8k)
- Memory strategies still work and teach the concepts

### Lab 3: Cost & Latency
- **Claude:** Real pricing, shows cost comparison
- **Ollama:** All models free, still shows latency comparison

### Lab 4: Grounding & RAG
- **Claude:** Fully functional with guardrails
- **Ollama:** Works, but may hallucinate more (smaller models)

### Lab 5: Evaluation
- **Claude:** LLM-as-judge is Claude
- **Ollama:** LLM-as-judge is your Ollama model

### Lab 6: Agents & Tools
- Both work identically

---

## Using Both (Advanced)

You can actually switch between Claude and Ollama in the same session:

1. Start with Claude to learn concepts
2. Click "✓ Claude Ready" button
3. Switch to Ollama
4. Click "Save & Continue"
5. All labs now use Ollama

This is great for comparing how different backends handle the same tasks!

---

## Real-World Use Case

**Ideal Learning Path:**

1. **Lab 1-2 with Claude** — Learn core concepts with best models
2. **Lab 3 with Claude** — See real pricing data
3. **Switch to Ollama** — Download Mistral
4. **Lab 4-6 with Ollama** — Practice RAG, evaluation, agents locally
5. **Compare side-by-side** — See how smaller models differ

---

That's it! Pick your provider and start learning. The app works great with either one. 🚀
