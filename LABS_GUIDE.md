# Labs Guide — What Each One Does

## Lab 1: How LLMs Actually Work

**Goal:** Understand model parameters and how they affect output.

### Configurable:
- **Model** — Pick Haiku, Sonnet, or Opus
- **System Prompt** — Instructions for the model
- **User Prompt** — Your actual question
- **Temperature** (0-2) — Controls randomness
  - 0 = Same output every time (deterministic)
  - 1.0 = Balanced
  - 2.0 = Maximum creativity
- **Top-P** (0-1) — Nucleus sampling. Lower = more focused
- **Max Tokens** — Hard limit on output length

### See:
- Generated response in real-time
- Token counts (input + output)
- Latency (how long it took)
- Stop reason (why generation stopped)

### Try This:
1. Set temperature to 0 → generate same prompt twice → same output
2. Set temperature to 2 → generate same prompt twice → different outputs
3. Slide max tokens down → watch response get cut off mid-sentence

---

## Lab 2: Context Windows & Memory

**Goal:** Learn how to handle long conversations within token limits.

### Configurable:
- **Model** — Pick model (each has 200k context)
- **Memory Strategy**:
  - **No Strategy** — Keep all history (hits limit fast)
  - **Sliding Window** — Keep last N turns (fast, loses old context)
  - **Summarization** — Compress old messages (good balance)
  - **Semantic** — Keep recent + relevant messages (simulated)
- **Keep Last N Turns** — (if using window or summarization)

### See:
- Conversation history growing
- Token counter filling up (visual progress bar)
- Red bar when approaching context limit
- Model response based on conversation state

### Try This:
1. Have a 10-message conversation with "No Strategy"
2. Watch token counter grow
3. Switch to "Sliding Window" → see token count drop
4. Have same conversation again → model remembers less old context
5. Compare "Summarization" — keeps important info, reduces tokens

---

## Lab 3: Cost & Latency Tradeoffs

**Goal:** See real differences between models and calculate costs.

### Configurable:
- **Prompt** — Same prompt tested on all models
- **Max Tokens** — Output limit
- **Daily API Calls** — For cost estimation (100-100k)
- **Avg Input Tokens** — For monthly projection
- **Avg Output Tokens** — For monthly projection

### See:
- **Latency comparison graph** — Which model is fastest?
- **Token usage table** — Input/output per model
- **Cost per API call** — Real pricing
- **Monthly cost projection** — At your usage levels

### Pricing Reference (per 1M tokens):
| Model | Input | Output |
|-------|-------|--------|
| Haiku | $1 | $5 |
| Sonnet | $3 | $15 |
| Opus | $15 | $75 |

### Try This:
1. Enter a complex prompt (e.g., "Explain quantum computing in detail")
2. Click "Compare All Models"
3. Note: Haiku is fastest & cheapest, Opus is slowest & most capable
4. Use the cost calculator: enter 10,000 daily calls → see monthly bill

---

## Lab 4: Grounding & Guardrails

**Goal:** Prevent hallucinations using retrieval-augmented generation (RAG).

### Configurable:
- **Question** — Your query
- **Use RAG** — Toggle on/off to see the difference
- **Documents to Retrieve** — How many docs to include (1-5)
- **Guardrail Level**:
  - **Strict** — Refuse off-topic questions
  - **Moderate** — Prioritize docs, allow general knowledge
  - **None** — Answer anything (hallucination risk)

### See:
- Retrieved documents highlighted
- Documents fed into system prompt
- Response grounded in real information
- Without RAG, model may hallucinate

### Try This:
1. Ask: "How much does Claude cost?"
2. Toggle RAG on → see pricing documents retrieved
3. Toggle RAG off → model tries from memory (may be outdated)
4. Set Guardrail to "Strict" → ask off-topic question → model refuses
5. Set Guardrail to "None" → same question → model answers (but less reliable)

---

## Lab 5: Evaluation & Testing

**Goal:** A/B test prompts and use LLM-as-judge to score them.

### Configurable:
- **Test Question** — Same question for both prompts
- **Prompt A & B** — Two different system prompts to compare
- **Use LLM-as-Judge** — Toggle scoring on/off

### Rubric (auto-scored):
- **Relevance** (25%) — Does it answer the question?
- **Accuracy** (25%) — Is it correct?
- **Clarity** (25%) — Is it well-explained?
- **Completeness** (25%) — Does it cover all aspects?

### See:
- Both responses side-by-side
- Judge scores for each criterion
- Total score (0-10)
- Which prompt won

### Try This:
1. Set Prompt A to "Be concise"
2. Set Prompt B to "Be detailed with examples"
3. Ask: "What is machine learning?"
4. See which prompt scores higher
5. Iterate: refine your prompt based on scores

---

## Lab 6: Agents & Tool Use

**Goal:** See how agents plan and execute multiple tools.

### Configurable:
- **User Task** — What you want the agent to do
- **Available Tools**:
  - **Calculator** — Math operations
  - **Weather API** — Get weather for cities
  - **Web Search** — Find information online
  - **Database Query** — Search records
- **Max Iterations** — Stop after N steps or when done

### Agent Loop:
1. **Thinking** — Agent reads your task
2. **Decision** — Which tool should I use?
3. **Execution** — Tool runs, returns result
4. **Feedback** — Agent gets result, decides next step
5. **Repeat** — Until task is done or max iterations hit

### See:
- Step-by-step trace (Thinking → Tool Call → Result)
- Which tools agent selected
- Tool responses fed back to agent
- Final answer from agent

### Try This:
1. Enable: Calculator, Weather, Search
2. Task: "What is 42 * 10, and what's the weather in New York?"
3. Watch agent decide → call Calculator → get 420
4. Watch agent decide → call Weather → get "72°F, sunny"
5. Watch agent combine both results into final answer

---

## Tips for All Labs

### 1. Start Simple
Don't configure everything at once. Pick one slider/toggle and change it, then observe the impact.

### 2. Use Real Prompts
Don't just test "hello" — use realistic questions you actually care about.

### 3. Compare
- Lab 1: Run same prompt with temp 0 vs 2
- Lab 2: Compare memory strategies on same conversation
- Lab 3: Compare models on your actual use case
- Lab 4: Toggle RAG on/off
- Lab 5: A/B test your real prompts
- Lab 6: Try with/without tools

### 4. Monitor Costs
Keep an eye on token counts. Lab 3's cost calculator shows real impact of your choices.

### 5. Take Notes
What you learn here maps to the course concepts. Write down insights.

---

## Common Patterns to Explore

### Pattern 1: Temperature vs Creativity
- Lab 1 → Set temperature to 0 → Generate 3x same prompt
- Observe: Output is identical
- Then set to 1.5 → Generate 3x → Output varies
- Insight: Higher temp = more creative but less consistent

### Pattern 2: Context Decay
- Lab 2 → Have 20-message conversation with "No Strategy"
- Ask: "What was my name from message 1?"
- Observe: Model probably forgets
- Switch to "Summarization" → Ask again → Better recall
- Insight: Memory strategy matters for long conversations

### Pattern 3: Model Cost-Quality Tradeoff
- Lab 3 → Test same complex prompt on all 3 models
- Haiku is fastest & cheapest, but might miss nuance
- Sonnet balances speed/quality/cost
- Opus is slowest but most capable
- Insight: Use Haiku for simple tasks, Opus for complex reasoning

### Pattern 4: RAG as Guardrail
- Lab 4 → Ask a factual question (e.g., "What's my name?")
- Without RAG: Model has no ground truth, might guess
- With RAG: Model only uses retrieved documents
- Insight: RAG prevents hallucinations, improves factuality

### Pattern 5: Prompt Quality Matters
- Lab 5 → Write a vague prompt vs a detailed prompt
- Score them on same question
- Detailed usually wins
- Insight: Prompt engineering is real work

### Pattern 6: Tools Enable Reasoning
- Lab 6 → Same task with/without tools
- With tools: Agent can do math, search, look things up
- Without tools: Agent must reason from memory
- Insight: Tool access expands what agents can do

---

**Ready to explore? Start at Lab 1, work through to Lab 6. Each builds on concepts from the previous one.**
