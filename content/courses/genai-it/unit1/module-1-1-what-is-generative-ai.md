---
title: "Module 1.1: What is Generative AI — LLMs Explained Simply"
description: "Understand how LLMs and Generative AI actually work — explained in plain language for Indian IT professionals and students. No maths, no jargon."
weight: 1
tags: ["generative-ai", "llm", "beginners", "india", "prompt-engineering"]
---

> **Unit 1 — Understanding GenAI** | Module 1 of 4  
> ⏱ Reading time: ~12 minutes | 📝 Assignment at the end

---

You have probably used ChatGPT, Copilot, or Gemini by now — maybe to draft an email, explain a bug, or summarise a document. But do you know what is actually happening when you type a message and the AI responds?

This module explains what Generative AI is, how Large Language Models work, and why this matters for your career in Indian IT — all without a single equation.

---

## What does "Generative AI" actually mean?

Let us start with the two words separately.

**AI (Artificial Intelligence)** is a broad term for software that can perform tasks that normally require human thinking — recognising images, translating languages, making decisions.

**Generative** means it creates new content. Earlier AI systems were mostly *discriminative* — they classified or predicted things. A spam filter decides: is this email spam or not spam? A recommendation engine decides: which movie should I suggest?

Generative AI is different. It *produces* something new — a paragraph of text, a line of code, an image, a piece of music — that did not exist before.

<!-- VISUAL: discriminative_vs_generative.svg -->
<!-- 
  Side-by-side SVG diagram showing:
  Left panel (gray): "Discriminative AI — classifies or decides"
    Input: an email → Model → Output: Spam / Not spam
    Examples: Spam filters, image classifiers, recommenders
  Right panel (teal): "Generative AI — creates new content"
    Input: a prompt → Model → Output: New text, code, image
    Examples: ChatGPT, Claude, Gemini, DALL-E, Copilot
  Source: Original diagram — CC0, free to use in course
-->

The most powerful form of Generative AI today is built on **Large Language Models (LLMs)**.

---

## What is a Large Language Model?

An LLM is a type of AI trained on an enormous amount of text — books, websites, research papers, code repositories, forum posts, and more. The training data for GPT-3 is estimated to include over 300 billion words.

During training, the model learns one thing at a deep level:

> **Given a sequence of words, what word is most likely to come next?**

That sounds simple. But when you do this billions of times, across hundreds of billions of examples, the model ends up learning something profound — it learns the patterns of human knowledge itself.

It learns that after "The capital of India is", the word "New" followed by "Delhi" is overwhelmingly likely. It learns that after `def calculate_tax(income):`, a line of Python code is expected, not a recipe. It learns the tone of a formal email versus a WhatsApp message.

None of this was explicitly programmed. It emerged from pattern learning at massive scale.

<!-- VISUAL: llm_next_token_prediction.svg -->
<!--
  Illustrative diagram showing:
  Left: text input "The capital of India is ___"
  Arrow pointing right into: "LLM box (175B+ parameters)"
  Arrow pointing right into: probability bar chart
    New Delhi  ████████████████████  94%
    Mumbai     █                      3%
    Kolkata    ▌                      2%
    Other      ▎                      1%
  Caption: "This happens for every single token in a response — hundreds of times per reply."
  Source: Original diagram — CC0, free to use in course
-->

---

## The "Large" in Large Language Model

GPT-3 — the model behind early ChatGPT — has **175 billion parameters**. Each parameter is a numerical value tuned during training to capture patterns in language. Think of each parameter as a tiny dial. Training adjusts all 175 billion dials simultaneously — billions of times — until the model becomes very good at predicting what comes next.

**Why does size matter?**  
Larger models develop what researchers call *emergent abilities* — capabilities that smaller models simply do not have. The ability to reason through multi-step problems, write working code, explain complex concepts — these appeared at scale, not by design.

Importantly, the industry has also learned that *efficiency matters as much as size*. More recent models are not necessarily bigger — they are smarter about how they use their parameters. The exact architecture of models like GPT-4, Claude, and Gemini is not publicly disclosed, but the trend is clear: better results with leaner, more efficient designs.

> **CC-licensed image suggestion:** Wikimedia Commons has a well-known timeline chart of LLM parameter counts over time.  
> Search: `wikimedia commons "language model" parameters timeline`  
> URL: https://commons.wikimedia.org/wiki/File:AI_timeline.svg  
> License: CC BY-SA 4.0 — usable with attribution: *"Source: Wikimedia Commons, CC BY-SA 4.0"*

---

## How does a conversation with ChatGPT actually work?

When you type a message, the model does not "think" the way you do. It runs through the same five mechanical steps — hundreds of times — to build your response one word at a time.

<!-- VISUAL: chatgpt_conversation_flow.svg -->
<!--
  Horizontal 5-step flowchart:
  [1. Tokenise: split text into chunks]
  → [2. Context: load full conversation]
  → [3. Probabilities: score all possible tokens]
  → [4. Sample: pick from top options]
  → [5. Repeat: until response complete]
  Dashed curved arrow looping from step 5 back to step 3
  Caption: "loops back to step 3 for every new token"
  Source: Original diagram — CC0, free to use in course
-->

**Step 1 — Tokenisation:** Your text is broken into tokens (chunks of text — roughly words or parts of words). "Generative AI" becomes two tokens. "Chandrashaker" might become three or four.

**Step 2 — Context window:** The model reads all the tokens in your conversation as one long sequence. Modern models like GPT-4 support up to 128,000 tokens — enough for a full novel.

**Step 3 — Probability calculation:** For every possible next token (~50,000 options), the model assigns a probability score.

**Step 4 — Sampling:** Rather than always picking the top-probability token (which would feel robotic and repetitive), the model samples from the top options — introducing natural variation. This is why the same question asked twice gives slightly different answers.

**Step 5 — Repeat:** Steps 3 and 4 repeat for every token in the response until the model decides to stop. A 200-word reply involves hundreds of these cycles.

This is why responses stream word by word — the model is generating your reply one token at a time, in real time.

---

## What Generative AI is NOT

Three misconceptions cause the most problems for Indian IT professionals — either leading to over-trust or unnecessary dismissal of AI tools.

<!-- VISUAL: genai_misconceptions.svg -->
<!--
  Three side-by-side card panels:
  1. Red card: "No internet (by default)"
     Text: Answers from training data, not live search. This is why it can hallucinate.
     Exception: ChatGPT browse, Perplexity
  2. Amber card: "No true understanding"
     Text: Sophisticated pattern matching — not human comprehension. Can fail on novel problems.
  3. Coral card: "No memory between chats"
     Text: Each new conversation starts from zero. Within a chat it remembers all (context window).
  Source: Original diagram — CC0, free to use in course
-->

**It does not search the internet by default.** An LLM answers from what it learned during training, not from a live search. This is why it can *hallucinate* — confidently state something false. Always verify important factual claims independently.

*Exception: ChatGPT with browsing enabled, Perplexity, and Gemini with live search can fetch real-time information. But the base model cannot.*

**It does not understand in the human sense.** The model does sophisticated pattern matching. This matters less than you might think in practice — outputs are often indistinguishable from genuine understanding — but it explains why AI can fail in surprising ways on genuinely novel problems.

**It has no memory between conversations.** Each new chat starts fresh. Within a conversation it remembers everything (the context window). Close the tab — it is back to zero.

---

## Why Indian IT professionals need to understand this NOW

AI/ML hiring on Naukri grew 45% across FY26 — the fastest-growing job category in Indian tech, while overall IT hiring remained flat. Naukri currently lists over 77,000 active AI job vacancies, and that number keeps climbing.

<!-- VISUAL: india_ai_hiring_chart (Chart.js bar chart) -->
<!--
  Metric summary cards (4 across):
  - AI/ML hiring growth FY26: +45%
  - Overall IT sector growth: Flat
  - Active AI vacancies on Naukri: 77,000+
  - AI salary premium: +53%

  Bar chart (grouped, 4 time periods):
  X-axis: Q1 FY26 | Feb 2026 (Indian MNCs) | Mar 2026 | Full year FY26
  Teal bars: AI/ML YoY growth: 38%, 82%, 37%, 45%
  Gray bars: Overall IT YoY growth: 8%, 12%, 9%, 8%
  
  Sources: Naukri JobSpeak March 2026, Naukri AI Jobs Report 2025, CBRE India Dec 2025
-->

But here is what many people miss — the majority of those roles are not asking for people to *build* AI. They are asking for people who can *work with* AI effectively.

Infosys alone is running over 4,600 active AI projects, has generated over 28 million lines of code using AI tools, and built more than 500 AI agents — deployed with 90% of its 200 largest clients. TCS, Wipro, and HCL are following the same path.

Developers who can write effective prompts, use AI coding tools, and understand what AI can and cannot do are being fast-tracked. Those who cannot are being left behind — regardless of years of experience.

> **CC-licensed image suggestion:** For a visual of Indian IT professionals in a modern workspace:  
> Search Unsplash (unsplash.com/license — free for commercial use, no attribution required):  
> Query: "software developer India office"  
> Or use Wikimedia Commons: search "information technology India"

---

## The three things to remember

If you take nothing else from this module, take these three points:

1. **LLMs predict the next word** — at massive scale, across massive training data, this produces remarkably capable outputs.

2. **They can hallucinate** — because they are pattern-matching, not fact-checking. Always verify important claims.

3. **Context is everything** — the more relevant context you give the model in your prompt, the better its output. This is the entire foundation of prompt engineering, which you will learn in Unit 2.

---

## Assignment 1.1

**Identify 5 GenAI tools you already use (or have access to)**

No technical work required — this is a reflection exercise.

1. List 5 AI tools you have used or have access to. Examples: ChatGPT, GitHub Copilot, Gemini in Google Workspace, Claude, Notion AI, Grammarly, Bing Chat.

2. For each tool, write two sentences:
   - What task you used it for (or what task it is designed for)
   - One observation about output quality — what it did well or where it fell short

3. Save your list. You will revisit it at the end of the course to see how your perspective has changed.

There are no wrong answers. The goal is awareness — knowing what AI tools are already in your environment is the first step to using them strategically.

---

## What is coming next

In Module 1.2, you will compare the three tools most Indian IT professionals are choosing between — **ChatGPT, Claude, and Gemini** — and learn which is best suited for different types of work.

→ [Continue to Module 1.2: ChatGPT vs Claude vs Gemini](/courses/genai-it/unit1/module-1-2-chatgpt-vs-claude-vs-gemini/)

---

## Further reading on the blog

- [How AI is Affecting Indian IT Jobs in 2026](/posts/ai-impact-indian-it-jobs/) — chandrashaker.in  
- [AI-Resistant Skills: What to Learn to Stay Relevant](/posts/ai-resistant-skills-india/) — chandrashaker.in

---

*← [Back to Unit 1 Overview](/courses/genai-it/unit1/) | [Course Home](/courses/genai-it/)*

---

### Image credits and licences (for course records)

| Visual | Type | Licence | Attribution required |
|---|---|---|---|
| Discriminative vs Generative diagram | Original SVG | CC0 | No |
| LLM next-token prediction diagram | Original SVG | CC0 | No |
| 5-step conversation flow diagram | Original SVG | CC0 | No |
| Misconceptions panel | Original SVG | CC0 | No |
| India hiring chart | Original Chart.js | CC0 (data from Naukri) | Cite Naukri as data source |
| LLM timeline (optional, Wikimedia) | Wikimedia Commons | CC BY-SA 4.0 | Yes — "Source: Wikimedia Commons, CC BY-SA 4.0" |
| Office photo (optional, Unsplash) | Unsplash license | Free commercial use | No (but credit appreciated) |
