# App Screenshots & Walkthrough

## Header & Navigation

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                               │
│  AI Concepts Playground                                      ✓ API Key Set   │
│  Interactive labs to practice concepts from the AI for PMs course            │
│                                                                               │
│  [Lab 1] [Lab 2] [Lab 3] [Lab 4] [Lab 5] [Lab 6]                            │
│   LLM    Context  Cost &  Ground   Eval   Agents                             │
│  Basics  Window  Latency  & RAG   Testing & Tools                            │
│                                                                               │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Lab 1: How LLMs Actually Work

```
┌──────────────────────────────┬──────────────────────────────┐
│ Configuration                │ Output                       │
├──────────────────────────────┼──────────────────────────────┤
│                              │                              │
│ Model                        │ Generated Text               │
│ [Haiku ▼]                    │                              │
│                              │ Quantum computing uses       │
│ System Prompt                │ quantum mechanics to solve   │
│ [You are helpful...]         │ problems exponentially       │
│                              │ faster than classical...     │
│ User Prompt                  │                              │
│ [Explain quantum...]         │ ─────────────────────────────│
│ ~42 tokens                   │                              │
│                              │ Input: 89 tokens            │
│ Temperature: 1.00            │ Output: 45 tokens           │
│ ▁▂▃▄▅▆▇█ (slider)           │ Latency: 342ms              │
│ ⚖️ Balanced                  │ Stop Reason: end_turn       │
│                              │                              │
│ Top-P: 0.95                  │                              │
│ ▁▂▃▄▅▆▇█ (slider)           │                              │
│ Filters to top 95%           │                              │
│                              │                              │
│ Max Tokens: 256              │                              │
│ [256    ]                    │                              │
│                              │                              │
│ [→ Generate] (100% width)    │                              │
│                              │                              │
└──────────────────────────────┴──────────────────────────────┘
```

**What You Learn:**
- Adjust temperature 0 → 2 → see creativity vs consistency
- Higher top-p = more options considered
- Max tokens = hard cutoff on length

---

## Lab 2: Context Windows & Memory

```
┌──────────────────────────────┬──────────────────────────────┐
│ Configuration                │ Conversation                 │
├──────────────────────────────┼──────────────────────────────┤
│                              │                              │
│ Model                        │ Conversation History         │
│ [Claude Haiku (200k) ▼]      │ ┌─────────────────────────┐  │
│                              │ │ 👤 You:                 │  │
│ Memory Strategy              │ │ My name is Alice and    │  │
│ ◉ No Strategy                │ │ I work in finance.      │  │
│ ○ Sliding Window             │ └─────────────────────────┘  │
│ ○ Summarization              │ ┌─────────────────────────┐  │
│ ○ Semantic (Simulated)       │ │ 🤖 Claude:              │  │
│                              │ │ Nice to meet you! What  │  │
│ Context Status               │ │ area of finance?        │  │
│ Tokens Used: 387 / 200000    │ └─────────────────────────┘  │
│ ▁▁▂▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁ 0.2%   │ ┌─────────────────────────┐  │
│                              │ │ 👤 You:                 │  │
│ Messages in Context: 4       │ │ Risk assessment.        │  │
│                              │ └─────────────────────────┘  │
│ [→ Send]                     │ ┌─────────────────────────┐  │
│                              │ │ 🤖 Claude:              │  │
│ [Type your message...]       │ │ That's critical. What's │  │
│                              │ │ your current challenge? │  │
│                              │ └─────────────────────────┘  │
│                              │                              │
│                              │ [Type message...] [→ Send]   │
│                              │                              │
└──────────────────────────────┴──────────────────────────────┘
```

**What You Learn:**
- Token counter fills up as conversation grows
- Different strategies handle long conversations
- Trade-off: more context vs. token cost

---

## Lab 3: Cost & Latency Tradeoffs

```
┌──────────────────────────────┬──────────────────────────────┐
│ Model Comparison             │ Monthly Cost Calculator       │
├──────────────────────────────┼──────────────────────────────┤
│                              │                              │
│ Prompt                       │ Daily API Calls: 1000 ▁▃▅▇█  │
│ [What is ML?]                │                              │
│                              │ Avg Input Tokens: 500 ▁▃▅▇█  │
│ Max Tokens: 256              │                              │
│ [256    ]                    │ Avg Output Tokens: 200 ▁▃▅▇█ │
│                              │                              │
│ [→ Compare All Models]       │ ─────────────────────────────│
│                              │                              │
│ Latency Comparison:          │ Model      | Cost/Call | Mo. │
│                              │ ──────────────────────────── │
│ ║ 450ms  ┃ 320ms   ┃ 1200ms  │ Haiku      | $0.000625| $18 │
│ ║        ┃         ┃         │ Sonnet     | $0.00200 | $60 │
│ ║ Haiku  ┃ Sonnet  ┃ Opus    │ Opus       | $0.0145  │$435 │
│                              │                              │
│ Results Table:               │ Pricing per 1M tokens:       │
│ Model   │ Latency │ Tokens   │ ───────────────────────────  │
│ ─────────────────────────    │ Model  │ Input  │ Output    │
│ Haiku   │ 450ms   │ 89/45    │ Haiku  │ $1     │ $5        │
│ Sonnet  │ 320ms   │ 89/48    │ Sonnet │ $3     │ $15       │
│ Opus    │ 1200ms  │ 89/52    │ Opus   │ $15    │ $75       │
│         │         │          │                              │
│ (Haiku fastest & cheapest)   │                              │
│                              │                              │
└──────────────────────────────┴──────────────────────────────┘
```

**What You Learn:**
- Real model comparison data
- Pricing breakdown
- Cost optimization strategies

---

## Lab 4: Grounding & Guardrails

```
┌──────────────────────────────┬──────────────────────────────┐
│ Configuration                │ Response                     │
├──────────────────────────────┼──────────────────────────────┤
│                              │                              │
│ Question                     │ Retrieved Documents (2)      │
│ [How much does Claude cost?] │                              │
│                              │ [Token Pricing]              │
│ ☑ Use RAG                    │ Haiku costs $1 per 1M input  │
│   (Retrieval-Augmented)      │ tokens and $5 per 1M output  │
│                              │ tokens. Sonnet costs $3 and  │
│ Documents to Retrieve: 2     │ $15 respectively. Opus costs │
│ [2      ]                    │ $15 and $75...               │
│                              │                              │
│ Guardrail Level              │ [Claude API Guide]           │
│ ◉ Strict                     │ Claude is an AI assistant... │
│ ○ Moderate                   │ The Claude API allows...     │
│ ○ None                       │                              │
│                              │ ─────────────────────────────│
│ [→ Ask]                      │                              │
│                              │ Generated Response           │
│                              │                              │
│                              │ Claude has three pricing     │
│                              │ tiers. Haiku is $1/$5,       │
│                              │ Sonnet is $3/$15, and Opus   │
│                              │ is $15/$75 per 1M tokens.    │
│                              │                              │
│                              │ System: ~145 tokens          │
│                              │ Output: 28 tokens            │
│                              │                              │
└──────────────────────────────┴──────────────────────────────┘
```

**What You Learn:**
- RAG grounds responses in real documents
- Guardrails control scope
- Prevents hallucinations

---

## Lab 5: Evaluation & Testing

```
┌──────────────────────────────┬──────────────────────────────┐
│ Setup                        │ Results                      │
├──────────────────────────────┼──────────────────────────────┤
│                              │                              │
│ Test Question                │ LLM-as-Judge Scores          │
│ [What is machine learning?]  │                              │
│                              │ Prompt A      │ Prompt B     │
│ Prompt A (Variant 1)         │ ┌──────────┐  │ ┌──────────┐│
│ [Be concise]                 │ │          │  │ │          ││
│                              │ │   7.8    │  │ │   8.2    ││
│ Prompt B (Variant 2)         │ │   /10    │  │ │   /10    ││
│ [Be detailed with examples]  │ └──────────┘  │ └──────────┘│
│                              │                              │
│ ☑ Use LLM-as-Judge          │ Score Breakdown              │
│   for scoring                │ ────────────────────────────  │
│                              │ Criterion  │ Prompt A | B   │
│ [→ Compare]                  │ ────────────────────────────  │
│                              │ Relevance  │   8     | 9    │
│                              │ Accuracy   │   8     | 8    │
│                              │ Clarity    │   7     | 8    │
│                              │ Complete   │   8     | 8    │
│                              │                              │
│ Scoring Rubric:              │ Prompt B wins slightly       │
│ • Relevance (25%)            │                              │
│ • Accuracy (25%)             │                              │
│ • Clarity (25%)              │ Prompt A Response            │
│ • Completeness (25%)         │ Machine learning is a field  │
│                              │ of AI that learns from data. │
│                              │                              │
│                              │ Prompt B Response            │
│                              │ Machine learning is a subset │
│                              │ of AI where systems learn    │
│                              │ from examples. For instance, │
│                              │ email spam filters learn...  │
│                              │                              │
└──────────────────────────────┴──────────────────────────────┘
```

**What You Learn:**
- A/B testing methodology
- LLM-as-judge evaluation
- Rubric-based scoring

---

## Lab 6: Agents & Tool Use

```
┌──────────────────────────────┬──────────────────────────────┐
│ Configuration                │ Agent Trace                  │
├──────────────────────────────┼──────────────────────────────┤
│                              │                              │
│ User Task                    │ [1] Agent processing...      │
│ [What is 42*10, and weather  │                              │
│  in New York?]               │ [1] Assistant:               │
│                              │ I'll help you calculate 42   │
│ Available Tools              │ times 10 and get the weather │
│ ☑ Calculator                 │ in New York.                 │
│ ☑ Weather API                │                              │
│ ☑ Web Search                 │ 🔧 Calling Calculator        │
│ ☐ Database Query             │                              │
│                              │ ✓ Calculator                 │
│ Max Iterations: 5            │ Result: 420                  │
│ [5      ]                    │                              │
│                              │ 🔧 Calling Weather API       │
│ [→ Run Agent]                │                              │
│                              │ ✓ Weather API                │
│                              │ Result: 72°F, sunny          │
│                              │                              │
│                              │ [2] Assistant:               │
│                              │ 42 * 10 = 420, and the      │
│                              │ weather in New York is 72°F, │
│                              │ sunny with 5mph wind.        │
│                              │                              │
│                              │ ✓ Agent completed task      │
│                              │                              │
└──────────────────────────────┴──────────────────────────────┘
```

**What You Learn:**
- Agent loops (think → act → observe → repeat)
- Multi-tool orchestration
- Step-by-step execution trace

---

## Light Mode Color Scheme

```
Background:    #ffffff (white)
Text Primary:  #1a1a1a (dark gray)
Text Secondary:#666666 (medium gray)
Border:        #ddd (light gray)
Accent:        #0066cc (blue)
Accent Light:  #e6f2ff (light blue)
Success:       #059669 (green)
Warning:       #d97706 (orange)
Error:         #dc2626 (red)
```

All text is readable on white. No dark mode toggle.

---

## Responsive Design

**Desktop (1400px):**
- 2-column layout (controls left, output right)

**Tablet (1000px):**
- Stacks to 1 column
- Full width inputs

**Mobile (768px):**
- Single column
- Touch-friendly buttons
- Readable tables

---

## Interactive Elements

### Sliders
```
Temperature: 1.00
▁▂▃▄▅▆▇█ ← Draggable slider
⚖️ Balanced ← Live feedback
```

### Buttons
```
Primary:   [→ Generate] (blue background)
Secondary: [✓ API Key Set] (light background)
Active:    [Lab 1: LLM Basics] (highlighted)
```

### Forms
```
Text Input:  [Your text here...]
Textarea:    [Multi-line text...]
Dropdown:    [Option ▼]
Checkbox:    ☑ Use RAG
Radio:       ◉ Strict  ○ Moderate  ○ None
```

### Output Boxes
```
┌─ Generated Text ─────────────┐
│ Model output appears here... │
│ Can be multi-line, wraps     │
│ nicely                       │
└──────────────────────────────┘
```

---

**Open http://localhost:5173 to see the real app!**
