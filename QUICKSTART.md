# Quick Start — 5 Minutes to Learning

## Step 1: Set Up (2 min)

```bash
cd /Users/pnawal/ai-playground
npm install
```

## Step 2: Get API Key (1 min)

Go to https://console.anthropic.com and create a free account. Get your API key (starts with `sk-ant-`).

## Step 3: Run Locally (1 min)

```bash
npm run dev
```

Open http://localhost:5173 in your browser.

## Step 4: Enter API Key (30 sec)

When the app loads, click **"Set API Key"** and paste your key from Step 2.

## Step 5: Start Learning (∞)

Click through the 6 labs:

| Lab | Try This |
|-----|----------|
| **Lab 1** | Slide temperature from 0 → 2, see output randomness change |
| **Lab 2** | Type in conversation, watch token counter fill up |
| **Lab 3** | Click "Compare All Models" to see cost/speed tradeoffs |
| **Lab 4** | Toggle RAG on/off to see how it grounds responses |
| **Lab 5** | Write two different prompts and A/B test them |
| **Lab 6** | Select tools and watch agent orchestrate them |

---

## Deploy to Web (5 min)

### Option A: GitHub Pages (Free)

```bash
# Build
npm run build

# Push to GitHub (replace with your repo)
git add .
git commit -m "Build: AI Concepts Playground"
git push origin main
```

Then in GitHub Settings → Pages → Deploy from `/dist` folder.

Site goes live at: `https://YOUR_USERNAME.github.io/ai-playground`

### Option B: Netlify (Even Easier)

```bash
npm run build
```

Drag `dist/` folder to https://app.netlify.com/drop

Site gets a free `.netlify.app` URL instantly.

---

## Common Issues

| Problem | Solution |
|---------|----------|
| "No API key set" | Click "Set API Key" button in header |
| "API error" | Check if Anthropic API is down, or key is invalid |
| App is slow | Check network (might be throttled), or Anthropic API latency |
| Build fails | `npm install` might have issues, try `npm cache clean --force` |

---

## Next: Customize

Edit `src/labs/Lab1LLMBasics.jsx` and change the default prompt:

```javascript
const [userPrompt, setUserPrompt] = useState('YOUR NEW PROMPT HERE')
```

Then `npm run dev` to see changes live.

---

That's it. You're now experimenting with real AI concepts. 🚀
