---
title: "Module 2.4: Common Prompt Mistakes and How to Fix Them"
description: "The 10 most common prompt engineering mistakes Indian students and IT professionals make — with exact before-and-after fixes and a reusable self-check checklist."
weight: 4
sidebar: false
mainroad_aside: false
tags: ["prompt-engineering", "prompt-mistakes", "india", "generative-ai", "chatgpt", "claude", "beginners"]
---

<style>
/* ── Module progress bar ─────────────────────────────────────── */
.mod-progress-wrap{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:12px 16px;margin-bottom:20px}
.mod-progress-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;flex-wrap:wrap;gap:6px}
.mod-progress-title{font-size:12px;font-weight:700;color:#555;letter-spacing:0.04em}
.mod-progress-bg{height:6px;background:#e0e0e0;border-radius:3px;margin-bottom:10px}
.mod-progress-fill{height:6px;border-radius:3px;background:#FF8C00;transition:width 0.3s ease}
.mod-progress-units{display:flex;gap:6px;flex-wrap:wrap}
.mod-progress-unit{font-size:11px;padding:3px 10px;border-radius:20px;text-decoration:none;font-weight:500;border:1px solid}
.mod-progress-unit.done{background:#e8f5e9;color:#2e7d32;border-color:#a5d6a7}
.mod-progress-unit.current{background:#1565C0;color:#fff;border-color:#1565C0}
.mod-progress-unit.upcoming{background:#f5f5f4;color:#999;border-color:#e0e0e0}
.mod-header{background:#1565C0;border-radius:6px;padding:14px 18px;margin-bottom:24px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px}
.mod-header-left{display:flex;flex-direction:column;gap:4px}
.mod-breadcrumb{font-size:11px;color:rgba(255,255,255,0.75);letter-spacing:0.03em}
.mod-title-inline{font-size:15px;font-weight:600;color:#fff;margin:0}
.mod-meta{display:flex;gap:10px;flex-wrap:wrap}
.mod-meta-item{font-size:11px;color:rgba(255,255,255,0.85);background:rgba(255,255,255,0.15);padding:3px 10px;border-radius:20px}
.mod-keypoint{background:#fff8e1;border-left:4px solid #FF8C00;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a3000;line-height:1.6}
.mod-keypoint strong{color:#FF8C00}
.mod-remember{background:#e8f0fe;border-left:4px solid #1565C0;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0}
.mod-remember-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.06em;margin-bottom:8px}
.mod-remember ol{margin:0;padding-left:18px}
.mod-remember li{font-size:14px;color:#111111;line-height:1.7;margin-bottom:4px}
/* ── Mistake cards ───────────────────────────────────────────── */
.mod-mistake{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0;border-left:4px solid #c62828}
.mod-mistake-header{padding:12px 16px;display:flex;align-items:center;justify-content:space-between;gap:8px;background:#fafafa;border-bottom:1px solid #f0f0f0}
.mod-mistake-num{width:28px;height:28px;border-radius:6px;background:#c62828;color:#fff;font-size:13px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.mod-mistake-title{font-size:14px;font-weight:700;color:#c62828;flex:1}
.mod-mistake-tag{font-size:10px;font-weight:700;padding:3px 9px;border-radius:20px;background:#ffeaea;color:#c62828;border:1px solid #ef9a9a;white-space:nowrap}
.mod-mistake-body{padding:14px 16px}
.mod-mistake-desc{font-size:14px;color:#111111;line-height:1.7;margin:0 0 12px}
/* ── Prompt before/after ─────────────────────────────────────── */
.mod-ba-pair{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:10px 0}
.mod-ba-box{border-radius:6px;overflow:hidden;border:1px solid}
.mod-ba-label{padding:6px 12px;font-size:10px;font-weight:700;letter-spacing:0.05em}
.mod-ba-text{padding:10px 12px;font-size:12px;font-family:monospace,sans-serif;line-height:1.7;white-space:pre-wrap;word-break:break-word;color:#111111;min-height:48px}
.mod-ba-bad .mod-ba-label{background:#ffeaea;color:#c62828;border-bottom:1px solid #ef9a9a}
.mod-ba-bad{border-color:#ef9a9a}
.mod-ba-bad .mod-ba-text{background:#fff8f8}
.mod-ba-good .mod-ba-label{background:#e8f5e9;color:#2e7d32;border-bottom:1px solid #a5d6a7}
.mod-ba-good{border-color:#a5d6a7}
.mod-ba-good .mod-ba-text{background:#f5fff6}
.mod-fix-note{font-size:12px;color:#555;padding:8px 12px;background:#f9f9f9;border-top:1px solid #f0f0f0;border-radius:0 0 6px 6px;line-height:1.5}
.mod-fix-note strong{color:#2e7d32}
/* ── Checklist ───────────────────────────────────────────────── */
.mod-checklist{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0}
.mod-checklist-header{background:#1565C0;padding:12px 16px;font-size:12px;font-weight:700;letter-spacing:0.05em;color:#fff}
.mod-checklist-section{padding:4px 0}
.mod-checklist-section-title{font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;padding:10px 16px 4px}
.mod-check-item{display:flex;align-items:flex-start;gap:10px;padding:8px 16px;border-bottom:1px solid #f5f5f5}
.mod-check-item:last-child{border-bottom:none}
.mod-check-box{width:16px;height:16px;border-radius:3px;border:1.5px solid #b0bec5;flex-shrink:0;margin-top:2px;background:#fff}
.mod-check-text{font-size:13px;color:#111111;line-height:1.5;flex:1}
.mod-check-text em{font-size:11px;color:#888;font-style:normal;display:block;margin-top:2px}
/* ── Diagnosis flowchart ─────────────────────────────────────── */
.mod-diag{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-diag-title{font-size:11px;font-weight:700;color:#555;letter-spacing:0.05em;margin-bottom:12px}
.mod-diag-row{display:flex;align-items:flex-start;gap:12px;padding:9px 0;border-bottom:1px solid #f0f0f0}
.mod-diag-row:last-child{border-bottom:none}
.mod-diag-symptom{font-size:13px;font-weight:600;color:#c62828;flex:1.2;line-height:1.4}
.mod-diag-arrow{font-size:14px;color:#999;flex-shrink:0;margin-top:1px}
.mod-diag-fix{font-size:13px;color:#111111;flex:2;line-height:1.4}
/* ── Unit 2 summary ──────────────────────────────────────────── */
.mod-unit-summary{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin:20px 0}
.mod-unit-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-unit-card-num{font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:4px}
.mod-unit-card-title{font-size:14px;font-weight:700;color:#1565C0;margin:0 0 6px}
.mod-unit-card-summary{font-size:13px;color:#444;line-height:1.6;margin:0}
/* ── Assignment, nav, blog, credits ─────────────────────────── */
.mod-assignment{background:#fff8e1;border:1px solid #FFB300;border-radius:6px;padding:16px 18px;margin:28px 0}
.mod-assignment-header{display:flex;align-items:center;gap:8px;margin-bottom:10px}
.mod-assignment-icon{font-size:16px;color:#FF8C00}
.mod-assignment-title{font-size:14px;font-weight:700;color:#5d4037;margin:0}
.mod-assignment p,.mod-assignment li{font-size:14px;color:#4a3000;line-height:1.7}
.mod-assignment ol,.mod-assignment ul{padding-left:20px;margin:8px 0}
.mod-nav{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;margin-top:32px;padding-top:18px;border-top:1px solid #e0e0e0}
.mod-nav-back{font-size:13px;color:#1565C0;text-decoration:none}
.mod-nav-back:hover{color:#0d47a1;text-decoration:underline}
.mod-nav-next{display:inline-flex;align-items:center;gap:6px;font-size:13px;font-weight:600;padding:9px 18px;border-radius:4px;background:#FF8C00;color:#fff !important;text-decoration:none}
.mod-nav-next:hover{background:#e65c00;color:#fff !important;text-decoration:none}
.mod-blog-links{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:6px;padding:14px 18px;margin-top:20px}
.mod-blog-title{font-size:11px;font-weight:700;color:#888;letter-spacing:0.06em;margin-bottom:8px}
.mod-blog-links a{display:block;font-size:13px;color:#1565C0;text-decoration:none;padding:3px 0;border-bottom:1px solid #f0f0f0}
.mod-blog-links a:last-child{border-bottom:none}
.mod-blog-links a:hover{color:#FF8C00;text-decoration:underline}
/* ── Body text readability ───────────────────────────────────── */
.mod-wrap p,.mod-wrap li,.mod-wrap td{font-size:16px !important;color:#111111 !important;line-height:1.85 !important;font-weight:450}
.mod-wrap p{margin-bottom:1.1em}
.mod-wrap h2{font-size:20px;color:#111111;margin-top:32px;margin-bottom:12px}
.mod-wrap h3{font-size:17px;color:#111111;margin-top:24px;margin-bottom:8px}
.mod-wrap strong{color:#111111;font-weight:600}
.mod-wrap em{color:#333}
.mod-wrap code{font-size:14px;background:#f0f0f0;padding:2px 6px;border-radius:3px;color:#c62828}
@media(max-width:600px){.mod-wrap p,.mod-wrap li,.mod-wrap td{font-size:16px !important;line-height:1.9 !important}}
.mod-credits{font-size:12px;color:#888;margin-top:32px;padding-top:12px;border-top:1px solid #e0e0e0}
.mod-credits summary{cursor:pointer;font-size:12px;color:#aaa;list-style:none}
.mod-credits summary:hover{color:#888}
.img-center{display:flex;justify-content:center;margin:20px 0}
.img-center svg{max-width:100%;height:auto}
.img-center>div{max-width:680px;width:100%}
@media(max-width:520px){.mod-ba-pair,.mod-unit-summary{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:35%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">7 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Understanding GenAI ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-2">Prompt Engineering</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-3">GenAI for Your Job</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-4">Advanced Techniques</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Career & India</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 2 &nbsp;›&nbsp; MODULE 4 OF 4</span>
    <h1 class="mod-title-inline">Common Prompt Mistakes and How to Fix Them</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Unit 2 Finale</span>
  </div>
</div>

This is the final module of Unit 2 — and the most practical one. You now have three modules of prompt engineering theory behind you. This module is about what goes wrong when you apply it, and how to fix it fast.

Every prompt that fails does so for a diagnosable reason. Once you learn to recognise the patterns, you will spend less time rewriting prompts from scratch and more time refining them precisely. The 10 mistakes in this module account for the vast majority of poor AI outputs that Indian students and IT professionals experience.

---

<div class="mod-keypoint">
<strong>The core principle of this module:</strong> A bad output is almost never the AI's fault. It is a specification problem — something was missing, ambiguous, or contradictory in the prompt. Your job is to diagnose which component failed and fix that specific component.
</div>

---

## Mistake 1 — Too vague, no task verb

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">1</div>
  <div class="mod-mistake-title">No task verb — the model has to guess what you want</div>
  <span class="mod-mistake-tag">Most common</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">The most frequent mistake: stating a topic instead of a task. The model does not know if you want a summary, a tutorial, a comparison, a list, an essay, or code. It guesses — and guesses wrong about half the time.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ NO TASK VERB</div><div class="mod-ba-text">machine learning in Python</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ CLEAR TASK VERB</div><div class="mod-ba-text">Write a beginner-friendly tutorial on training a linear regression model in Python using scikit-learn. Include code with comments.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> Start every prompt with an action verb — write, explain, compare, list, debug, summarise, translate, review, generate, analyse. One verb, one task.</div>
</div>
</div>

---

## Mistake 2 — No audience specified

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">2</div>
  <div class="mod-mistake-title">No audience — the model defaults to a generic educated adult</div>
  <span class="mod-mistake-tag">Very common</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">Without an audience, the model picks a default — usually a vague "educated adult." For students, this means explanations that are too advanced. For non-technical managers, too technical. Specifying the audience is the single fastest way to improve output quality.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ NO AUDIENCE</div><div class="mod-ba-text">Explain recursion in Python.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ AUDIENCE SPECIFIED</div><div class="mod-ba-text">Explain recursion in Python to a 2nd-year BTech CSE student who understands loops and functions but has never written a recursive function. Use a simple real-world analogy first, then a code example.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> Add "for a [role + level]" to every explanation or writing task. "For a final-year ECE student", "for a non-technical HR manager", "for a junior developer joining my team."</div>
</div>
</div>

---

## Mistake 3 — Missing context

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">3</div>
  <div class="mod-mistake-title">No context — the model invents details you did not want</div>
  <span class="mod-mistake-tag">Very common</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">The most common assumption mistake: the model does not know who you are, what your project is, what constraints you have, or what has already been tried. Without context, it fills in the gaps — and fills them with generic content that does not fit your situation.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ NO CONTEXT</div><div class="mod-ba-text">Write an email about the project delay.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ CONTEXT PROVIDED</div><div class="mod-ba-text">Write an email to my project manager at TCS.

Context: The backend API integration is delayed by 3 days because the third-party vendor has not shared their documentation despite two reminders. The original deadline was Friday. The delay affects only the payment module, not the entire project.

Tone: Professional and factual. Do not over-apologise. Propose a revised timeline.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> Before writing a prompt for any professional task, ask yourself: "What would I tell a new colleague before asking them to do this?" Paste that into your prompt as context.</div>
</div>
</div>

---

## Mistake 4 — No format specified

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">4</div>
  <div class="mod-mistake-title">No format — the model picks one you did not want</div>
  <span class="mod-mistake-tag">Common</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">Without a format instruction, the model defaults to its training average — usually long paragraphs with bold headings. If you wanted a table, bullet points, or a short paragraph, you will have to ask again. Specifying format upfront saves an entire follow-up prompt.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ NO FORMAT</div><div class="mod-ba-text">Compare Zerodha and Upstox for a beginner investor.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ FORMAT SPECIFIED</div><div class="mod-ba-text">Compare Zerodha and Upstox for a beginner investor in India.

Format: A table with these columns — Feature | Zerodha | Upstox.
Rows: Account opening fee, Brokerage, App usability, Research tools, Customer support.
After the table, add 2 sentences on which is better for a first-time investor and why.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> Always specify format for outputs you will use directly — tables, bullet lists, numbered steps, code blocks, JSON, plain paragraphs, word count. If you do not specify, you are choosing "surprise me."</div>
</div>
</div>

---

## Mistake 5 — Multiple tasks in one prompt

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">5</div>
  <div class="mod-mistake-title">Multi-task prompt — the model rushes all tasks and does none well</div>
  <span class="mod-mistake-tag">Common</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">Packing multiple unrelated tasks into one prompt forces the model to switch contexts repeatedly. Each task gets a fraction of the attention it deserves. The output is broad and shallow when you needed deep and specific.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ MULTIPLE TASKS</div><div class="mod-ba-text">Explain neural networks, write me a Python implementation, list the top 5 applications in India, and suggest how I can learn this in 30 days.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ ONE TASK PER PROMPT</div><div class="mod-ba-text">Prompt 1: Explain neural networks in plain language for a 3rd-year ECE student. Use an analogy. Under 200 words.

[After reading the answer:]
Prompt 2: Show me a minimal Python implementation of a feedforward neural network using NumPy only. No frameworks.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> One task per prompt. Use the same conversation thread — each response builds on the last. Sequential prompts in one conversation produce far better results than one mega-prompt.</div>
</div>
</div>

---

## Mistake 6 — Accepting the first output

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">6</div>
  <div class="mod-mistake-title">Accepting the first output — leaving 30–40% quality on the table</div>
  <span class="mod-mistake-tag">Very common</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">The first output is a starting point, not a final deliverable. Most AI outputs need one or two refinement passes to reach high quality. Accepting first outputs and blaming the tool is the most common mistake experienced users make.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ ACCEPTING FIRST OUTPUT</div><div class="mod-ba-text">[reads the output, copies it, submits it]

Result: generic, AI-sounding, not quite right.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ REFINEMENT PROMPTS</div><div class="mod-ba-text">Follow-up 1: "Make it more concise — cut to under 150 words."

Follow-up 2: "Replace the generic opening line with something specific to Indian IT."

Follow-up 3: "The tone is too formal. Rewrite the second paragraph to sound like a person, not a press release."</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> After every first output, ask yourself: what is one specific thing that could be better? Write one targeted follow-up prompt. Two iterations of this produces output that is noticeably better than the first draft.</div>
</div>
</div>

---

## Mistake 7 — Not separating generation from verification

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">7</div>
  <div class="mod-mistake-title">Asking for a perfect answer in one pass — missing silent errors</div>
  <span class="mod-mistake-tag">Common in professional use</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">Models make silent mistakes — missed constraints, broken logic, unsupported claims, incorrect code — that are not flagged as errors. The output looks correct but is not. The fix is a two-pass approach: generate first, verify separately.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ ONE-PASS PROMPT</div><div class="mod-ba-text">Write a Python function that reads a CSV file and returns the top 5 rows by sales value.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ TWO-PASS PROMPT</div><div class="mod-ba-text">Pass 1: Write a Python function that reads a CSV file and returns the top 5 rows by sales value. The CSV has columns: date, product, region, sales.

Pass 2 (new prompt): Review the code you just wrote. Check for: edge cases (empty CSV, missing column), error handling, and whether the output is a DataFrame or a list. Flag any issues.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> For any important output — code, analysis, a document you will send to someone — use a second prompt to review and verify. Ask the model to check its own work against specific criteria. It catches its own mistakes surprisingly well when asked explicitly.</div>
</div>
</div>

---

## Mistake 8 — Wrong technique for the task

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">8</div>
  <div class="mod-mistake-title">Using the wrong prompting technique for the task type</div>
  <span class="mod-mistake-tag">Intermediate mistake</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">After learning techniques in Unit 2, a common mistake is over-applying them — adding few-shot examples when zero-shot is enough, or skipping chain-of-thought on a task that clearly needs step-by-step reasoning. Also: applying explicit CoT reasoning prompts to newer reasoning models that have it built in — this can actually interfere with their reasoning process.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ WRONG TECHNIQUE</div><div class="mod-ba-text">Using few-shot with 3 examples to ask: "What is the capital of Maharashtra?"

Or: Adding "think step by step" to a reasoning model (o1, Gemini Thinking) — these models already reason internally; the instruction is redundant or disruptive.</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ RIGHT TECHNIQUE</div><div class="mod-ba-text">Simple factual question → zero-shot. No examples needed.

Complex analysis or multi-step problem → CoT on standard models (ChatGPT, Claude Sonnet, Gemini Pro).

Style-sensitive output → few-shot. Provide 1 example.

Reasoning models (o1, Gemini Thinking) → direct instructions. Skip explicit CoT triggers.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> Match technique to task. Zero-shot first, always. Add few-shot only for style/format tasks. Add CoT only for multi-step reasoning on standard models. The simpler the better.</div>
</div>
</div>

---

## Mistake 9 — Generic domain language

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">9</div>
  <div class="mod-mistake-title">Not including your domain — getting generic output for a specific field</div>
  <span class="mod-mistake-tag">Common in professional use</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">A prompt about "system performance" without specifying whether you mean database performance, network performance, or microcontroller performance will get a generic answer that may not apply to your field. Domain-specific vocabulary in your prompt produces domain-specific output.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ NO DOMAIN</div><div class="mod-ba-text">How do I improve system performance?</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ DOMAIN SPECIFIED</div><div class="mod-ba-text">How do I improve query performance in a Django REST API backed by PostgreSQL, handling 50,000 requests per day? Focus on database indexing and query optimisation. We are on AWS RDS.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> Include your specific technology stack, industry, or subject area in every technical prompt. The more specific your domain language, the more precise the output. "Indian retail banking", "embedded systems on ARM Cortex-M4", "BTech EC curriculum" — specificity beats generality every time.</div>
</div>
</div>

---

## Mistake 10 — Outdated context in long conversations

<div class="mod-mistake">
<div class="mod-mistake-header">
  <div class="mod-mistake-num">10</div>
  <div class="mod-mistake-title">Losing context in long conversations — the model drifts</div>
  <span class="mod-mistake-tag">Common in extended sessions</span>
</div>
<div class="mod-mistake-body">
  <p class="mod-mistake-desc">In a long conversation, the model can gradually lose track of your original constraints, role, or goal — especially when the context window fills up and older instructions get compressed. You notice this when the model starts contradicting earlier instructions or reverting to generic style.</p>
  <div class="mod-ba-pair">
    <div class="mod-ba-box mod-ba-bad"><div class="mod-ba-label">✗ CONTEXT DRIFT</div><div class="mod-ba-text">[After 15 exchanges, the model has forgotten it was supposed to be a strict interviewer and starts giving away answers, or has forgotten the word limit it was given 10 messages ago]</div></div>
    <div class="mod-ba-box mod-ba-good"><div class="mod-ba-label">✓ CONTEXT RESET</div><div class="mod-ba-text">Quick reminder of our constraints: You are a strict technical interviewer. Do not give away answers. Maximum 3 sentences per response. We are at question 4 of 10.

Continue from where we left off.</div></div>
  </div>
  <div class="mod-fix-note"><strong>Fix:</strong> For tasks spanning more than 8–10 exchanges, periodically restate the key constraints in a brief "reminder" prompt. Also: start a fresh conversation for a genuinely new task rather than continuing an old one — stale context from previous tasks can corrupt new outputs.</div>
</div>
</div>

---

## Quick diagnosis guide — what symptom means what

<div class="mod-diag">
<div class="mod-diag-title">IF THE OUTPUT IS... → THE MISSING COMPONENT IS...</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Too generic, could apply to anyone</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>context</strong> (who you are, what this is for) and <strong>audience</strong></span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Wrong format (paragraphs when you wanted a table, or vice versa)</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>format specification</strong> — add it explicitly</span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Too long, too detailed, goes off on tangents</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>constraints</strong> — add word count, "be concise", or scope limits</span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Too shallow, not specific enough to your situation</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>domain language</strong> and <strong>context</strong> — be more specific about your tech stack, industry, and goal</span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Wrong tone (too formal, too casual, too technical)</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>role</strong> and <strong>audience</strong> specification — add both</span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Logically wrong or inconsistent on a complex problem</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>chain-of-thought</strong> — add "think step by step" or numbered reasoning steps</span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Correct but feels AI-sounding, not your style</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing <strong>few-shot examples</strong> of your preferred style — add 1–2 examples</span>
</div>
<div class="mod-diag-row">
  <span class="mod-diag-symptom">Addresses the wrong task entirely</span>
  <span class="mod-diag-arrow">→</span>
  <span class="mod-diag-fix">Missing clear <strong>task verb</strong> — rewrite the first sentence with a specific action verb</span>
</div>
</div>

---

## The pre-submit prompt checklist

Print this. Stick it next to your monitor. Use it for the next two weeks until it becomes instinctive.

<div class="mod-checklist">
<div class="mod-checklist-header">PROMPT SELF-CHECK — RUN THIS BEFORE HITTING SEND</div>

<div class="mod-checklist-section">
<div class="mod-checklist-section-title">FOUNDATION</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Does my prompt start with a clear action verb?<em>write / explain / compare / list / debug / summarise / review / generate</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Have I specified who will read or use this output?<em>"for a 3rd-year BTech student" / "for my project manager at Infosys"</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Have I provided enough context for this specific situation?<em>background, constraints, what has already been tried, what the output is for</em></div></div>
</div>

<div class="mod-checklist-section">
<div class="mod-checklist-section-title">OUTPUT CONTROL</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Have I specified the output format?<em>table / bullet list / code block / numbered steps / plain paragraphs / word count</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Have I added constraints on what NOT to include?<em>word limits / topics to exclude / tools to avoid / tone restrictions</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Is this one task, or have I bundled multiple tasks?<em>if multiple → split into sequential prompts</em></div></div>
</div>

<div class="mod-checklist-section">
<div class="mod-checklist-section-title">TECHNIQUE</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Does the style/format matter enough to add a few-shot example?<em>if yes → provide 1 example before the task</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Does this involve multi-step reasoning or analysis?<em>if yes → add "think step by step" or numbered reasoning steps</em></div></div>
</div>

<div class="mod-checklist-section">
<div class="mod-checklist-section-title">AFTER THE OUTPUT</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Have I verified every specific fact, citation, and number independently?<em>especially for professional work — do not skip this</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Is there one specific thing I can improve with a follow-up prompt?<em>conciseness / tone / a specific section / missing detail</em></div></div>
</div>
</div>

---

## Unit 2 — What you have learned

This is the last module of Unit 2. Here is a quick summary of what you now know:

<div class="mod-unit-summary">
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 2.1</div>
    <div class="mod-unit-card-title">Anatomy of a Good Prompt</div>
    <div class="mod-unit-card-summary">Six components: role, task, context, format, examples, constraints. A prompt is a specification. Structure beats length.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 2.2</div>
    <div class="mod-unit-card-title">Zero-Shot, Few-Shot, CoT</div>
    <div class="mod-unit-card-summary">Start with zero-shot. Add few-shot for style. Add CoT for multi-step reasoning. Combine all three for complex tasks.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 2.3</div>
    <div class="mod-unit-card-title">Role Prompting and Personas</div>
    <div class="mod-unit-card-summary">Role changes style and framing, not knowledge. Strong roles have 4 elements. Audience specification is as powerful as the role itself.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 2.4</div>
    <div class="mod-unit-card-title">Common Mistakes and Fixes</div>
    <div class="mod-unit-card-summary">10 diagnosable patterns. Bad output = missing specification. Use the pre-submit checklist until the habits are automatic.</div>
  </div>
</div>

Unit 3 is where all of this becomes practical for your actual job. You will apply these techniques to real developer, analyst, and manager workflows — with specific examples from Indian IT contexts.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 2.4</div>
  <ol>
    <li><strong>Bad output is a specification problem, not an AI problem</strong> — every poor output has a diagnosable missing component. Use the symptom-to-fix diagnosis guide to identify it and the pre-submit checklist to prevent it.</li>
    <li><strong>First outputs are starting points</strong> — one targeted follow-up prompt improves output quality by 30–40%. Accepting first outputs is the most common mistake experienced users make.</li>
    <li><strong>Use a two-pass approach for anything important</strong> — generate first, then use a separate prompt to verify. Ask the model to check its own output against specific criteria. It catches its own mistakes well when asked explicitly.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-24">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 2.4 — Rewrite 3 Weak Prompts Using the Full Unit 2 Toolkit</h3>
  </div>
  <p>This is the Unit 2 capstone assignment. It applies everything from all four modules.</p>
  <ol>
    <li><strong>Find 3 prompts you have written in the past</strong> that gave you a disappointing output — or write 3 new weak prompts from scratch. Use real tasks you actually need to complete.</li>
    <li><strong>Diagnose each prompt</strong> using the symptom-to-fix guide in this module. Identify exactly which component was missing or wrong.</li>
    <li><strong>Rewrite each prompt</strong> applying the full Unit 2 toolkit:
      <ul>
        <li>Six components from Module 2.1 — role, task, context, format, examples, constraints</li>
        <li>Correct technique from Module 2.2 — zero-shot, few-shot, or CoT as appropriate</li>
        <li>Role and audience from Module 2.3 if relevant</li>
      </ul>
    </li>
    <li><strong>Test each rewritten prompt</strong> and note the output quality difference.</li>
    <li><strong>Add these to your AI Learning Journal</strong> under "Prompt Rewrites — Unit 2" with a one-line note on what the most impactful change was for each.</li>
  </ol>
  <p>When you complete this assignment, you have finished Unit 2. You now have the core prompt engineering skills needed for Unit 3 — where you will apply these techniques directly to developer, analyst, and manager workflows in Indian IT contexts.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit2/module-2-3-role-prompting-personas/">&#8592; Module 2.3: Role Prompting and Personas</a>
  <a class="mod-nav-next" href="/courses/genai/unit3/module-3-1-genai-for-developers/">Unit 3: GenAI for Your Job &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>Goldilocks principle — too vague vs too specific in prompts</td><td>Reintech.io Common Prompt Engineering Mistakes, February 2026</td></tr>
      <tr><td>Two-pass approach: generate then verify; reflection pattern</td><td>Medium — Prompt Engineering Basics 2026, January 2026</td></tr>
      <tr><td>Do not use explicit CoT triggers with reasoning models (o1, Gemini Thinking) — can interfere</td><td>ODSC Medium — Beyond Prompt and Pray, April 2025; Thomas Wiegold Blog February 2026</td></tr>
      <tr><td>Domain expertise + prompt engineering is more valuable than generic prompting</td><td>ODSC Medium — Beyond Prompt and Pray, April 2025</td></tr>
      <tr><td>One strong few-shot example beats three mediocre ones</td><td>Medium — Prompt Engineering Basics 2026, January 2026</td></tr>
      <tr><td>Structure beats length — prompt engineering in 2026 is writing clearer specs</td><td>promptbuilder.cc Prompt Engineering Best Practices 2026</td></tr>
      <tr><td>Most common mistake is assuming the AI has context it does not have</td><td>Treyworks Common Prompt Engineering Mistakes 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
