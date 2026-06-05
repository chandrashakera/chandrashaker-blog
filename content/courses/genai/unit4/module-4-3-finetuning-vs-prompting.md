---
title: "Module 4.3: Fine-Tuning vs Prompting — When to Use Which"
description: "Understand when prompting is enough, when RAG is the answer, and when fine-tuning is actually necessary — a practical decision framework for Indian IT students and professionals."
weight: 3
sidebar: false
mainroad_aside: false
tags: ["fine-tuning", "prompt-engineering", "rag", "lora", "india", "generative-ai", "advanced"]
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
/* ── Module header ───────────────────────────────────────────── */
.mod-header{background:#1565C0;border-radius:6px;padding:14px 18px;margin-bottom:24px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px}
.mod-header-left{display:flex;flex-direction:column;gap:4px}
.mod-breadcrumb{font-size:11px;color:rgba(255,255,255,0.75);letter-spacing:0.03em}
.mod-title-inline{font-size:15px;font-weight:600;color:#fff;margin:0}
.mod-meta{display:flex;gap:10px;flex-wrap:wrap}
.mod-meta-item{font-size:11px;color:rgba(255,255,255,0.85);background:rgba(255,255,255,0.15);padding:3px 10px;border-radius:20px}
/* ── Callout boxes ───────────────────────────────────────────── */
.mod-keypoint{background:#fff8e1;border-left:4px solid #FF8C00;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a3000;line-height:1.6}
.mod-keypoint strong{color:#FF8C00}
.mod-remember{background:#e8f0fe;border-left:4px solid #1565C0;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0}
.mod-remember-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.06em;margin-bottom:8px}
.mod-remember ol{margin:0;padding-left:18px}
.mod-remember li{font-size:14px;color:#111111;line-height:1.7;margin-bottom:4px}
/* ── Sequence ladder ─────────────────────────────────────────── */
.mod-ladder{margin:20px 0}
.mod-rung{display:flex;align-items:flex-start;gap:14px;padding:14px 16px;background:#fff;border:1px solid #e0e0e0;border-radius:8px;margin-bottom:8px;position:relative}
.mod-rung-num{width:34px;height:34px;border-radius:50%;font-size:14px;font-weight:700;color:#fff;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px}
.mod-rung-body{flex:1}
.mod-rung-title{font-size:14px;font-weight:700;color:#1a1a1a;margin:0 0 3px}
.mod-rung-desc{font-size:13px;color:#555;line-height:1.6;margin:0 0 4px}
.mod-rung-use{font-size:12px;font-style:italic;color:#888;line-height:1.5}
.mod-rung-tag{display:inline-block;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;float:right;margin-left:8px}
/* ── Comparison table ────────────────────────────────────────── */
.mod-table-wrap{overflow-x:auto;margin:20px 0}
.mod-table{width:100%;border-collapse:collapse;font-size:13px}
.mod-table th{background:#1565C0;color:#fff;padding:10px 13px;text-align:left;font-weight:600;font-size:12px}
.mod-table td{padding:10px 13px;border-bottom:1px solid #f0f0f0;color:#111111;vertical-align:top;line-height:1.5}
.mod-table tr:last-child td{border-bottom:none}
.mod-table tr:nth-child(even) td{background:#fafafa}
.mod-table td:first-child{font-weight:600;color:#1565C0;white-space:nowrap}
/* ── Decision tree ───────────────────────────────────────────── */
.mod-decision{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-decision-title{font-size:11px;font-weight:700;color:#555;letter-spacing:0.05em;margin-bottom:14px}
.mod-drow{display:flex;align-items:flex-start;gap:12px;padding:10px 0;border-bottom:1px solid #f0f0f0}
.mod-drow:last-child{border-bottom:none}
.mod-dq{font-size:13px;font-weight:600;color:#1565C0;flex:1.4;line-height:1.4}
.mod-darrow{font-size:14px;color:#bbb;flex-shrink:0;margin-top:1px}
.mod-dans{font-size:13px;color:#111111;flex:2;line-height:1.4}
/* ── Fine-tune method cards ──────────────────────────────────── */
.mod-method-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin:20px 0}
.mod-method-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-method-title{font-size:13px;font-weight:700;color:#1565C0;margin:0 0 6px}
.mod-method-text{font-size:12px;color:#444;line-height:1.6;margin:0 0 8px}
.mod-method-badge{display:inline-block;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px}
.mod-badge-green{background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7}
.mod-badge-orange{background:#fff8e1;color:#e65c00;border:1px solid #FFB300}
.mod-badge-red{background:#ffeaea;color:#c62828;border:1px solid #ef9a9a}
/* ── Indian IT context cards ─────────────────────────────────── */
.mod-india-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-india-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;border-left:3px solid #1565C0}
.mod-india-title{font-size:13px;font-weight:700;color:#1565C0;margin:0 0 6px}
.mod-india-text{font-size:13px;color:#333;line-height:1.6;margin:0}
.mod-india-verdict{font-size:11px;font-weight:700;margin-top:7px;padding:2px 8px;border-radius:20px;display:inline-block}
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
@media(max-width:520px){.mod-method-grid{grid-template-columns:1fr}.mod-india-grid{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:70%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">14 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Module 1 ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-2">Module 2 ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-3">Module 3 ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-4">Module 4 — current</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Module 5</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 4 &nbsp;›&nbsp; MODULE 3 OF 4</span>
    <h1 class="mod-title-inline">Fine-Tuning vs Prompting — When to Use Which</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 13 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Decision framework</span>
  </div>
</div>

You now understand prompting (Units 1–2), RAG (Module 4.1), and agents (Module 4.2). This module answers the question that comes up in almost every Indian IT AI project discussion: when is prompting enough, when should you use RAG, and when do you actually need to fine-tune?

This is not a deeply technical module — you do not need to run a training job to understand it. You need to understand the decision logic, the trade-offs, and the cost implications. That understanding is what separates a professional who can discuss AI architecture from one who can only use AI tools.

---

## The honest answer most teams miss

<div class="mod-keypoint">
<strong>Prompt engineering and few-shot examples solve approximately 70% of LLM performance problems. Fine-tuning is the 30% solution.</strong> Most teams reach for fine-tuning too early — they spend weeks preparing data, renting GPUs, and debugging training loops. Meanwhile, a better-crafted system prompt with few-shot examples and chain-of-thought reasoning would have solved the problem in an afternoon. The question is not "which is better?" — it is "which is appropriate for this specific problem right now?"
</div>

The right sequence in 2026 is: **Prompt → RAG → Fine-tune → Distill.** Move to the next level only when the previous level genuinely cannot solve the problem.

---

## The four-level decision ladder

<div class="mod-ladder">

<div class="mod-rung">
  <div class="mod-rung-num" style="background:#2e7d32">1</div>
  <div class="mod-rung-body">
    <div class="mod-rung-title">Prompting &amp; few-shot examples <span class="mod-rung-tag" style="background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7">Start here always</span></div>
    <div class="mod-rung-desc">Write a clear, well-structured prompt. Add role, context, format, and constraints. Add 1–3 few-shot examples if style matters. Use chain-of-thought for complex reasoning. This is fast, free, and reversible.</div>
    <div class="mod-rung-use">Use when: you need a general-purpose task done well. The model already knows how to do this type of work from training. You want to change the style, format, or depth of response.</div>
  </div>
</div>

<div class="mod-rung">
  <div class="mod-rung-num" style="background:#1565C0">2</div>
  <div class="mod-rung-body">
    <div class="mod-rung-title">RAG — retrieval augmented generation <span class="mod-rung-tag" style="background:#e3f2fd;color:#1565C0;border:1px solid #90caf9">For knowledge problems</span></div>
    <div class="mod-rung-desc">Connect the model to your documents, databases, or knowledge bases. The model retrieves relevant content at query time and answers from it. No retraining, always up to date. Covered in Module 4.1.</div>
    <div class="mod-rung-use">Use when: the model needs access to your specific data — internal policies, product details, client information, recent events — that was not in its training data.</div>
  </div>
</div>

<div class="mod-rung">
  <div class="mod-rung-num" style="background:#FF8C00">3</div>
  <div class="mod-rung-body">
    <div class="mod-rung-title">Fine-tuning <span class="mod-rung-tag" style="background:#fff8e1;color:#e65c00;border:1px solid #FFB300">For behaviour problems</span></div>
    <div class="mod-rung-desc">Retrain the model weights on your specific data to teach it a new behaviour, style, or task pattern. Expensive and time-consuming, but produces a model that reliably behaves in a specific way without needing the behaviour described in every prompt.</div>
    <div class="mod-rung-use">Use when: prompting has hit a performance ceiling, you need consistent output format or style at scale, you have 500+ high-quality training examples, or latency and cost require a smaller specialised model.</div>
  </div>
</div>

<div class="mod-rung">
  <div class="mod-rung-num" style="background:#6a1b9a">4</div>
  <div class="mod-rung-body">
    <div class="mod-rung-title">Distillation <span class="mod-rung-tag" style="background:#f3e5f5;color:#6a1b9a;border:1px solid #ce93d8">For cost / scale problems</span></div>
    <div class="mod-rung-desc">Train a smaller, cheaper model to mimic the outputs of a larger one on your specific task. The result is a model that is fast, cheap to serve, and specialised. Only relevant when you have very high query volumes and cost is a primary constraint.</div>
    <div class="mod-rung-use">Use when: your fine-tuned model is working well but API costs at scale are unsustainable. This is typically a problem for products serving millions of users, not internal enterprise tools.</div>
  </div>
</div>

</div>

---

## Prompting vs RAG vs fine-tuning — full comparison

<div class="mod-table-wrap">
<table class="mod-table">
<thead>
  <tr><th>Dimension</th><th>Prompting</th><th>RAG</th><th>Fine-tuning</th></tr>
</thead>
<tbody>
  <tr>
    <td>What it changes</td>
    <td>What the model is asked to do in each conversation</td>
    <td>What information the model has access to at query time</td>
    <td>The model's weights — permanently changes how it behaves</td>
  </tr>
  <tr>
    <td>Best for</td>
    <td>General tasks, style control, format, reasoning</td>
    <td>Factual Q&amp;A over your documents and data</td>
    <td>Consistent behaviour, custom style, domain specialisation</td>
  </tr>
  <tr>
    <td>Data required</td>
    <td>None — just a good prompt</td>
    <td>Your documents, indexed in a vector database</td>
    <td>500–50,000+ high-quality labelled examples</td>
  </tr>
  <tr>
    <td>Time to implement</td>
    <td>Minutes to hours</td>
    <td>Days to weeks (depends on data volume)</td>
    <td>Weeks to months (data prep + training + eval)</td>
  </tr>
  <tr>
    <td>Cost</td>
    <td>API call cost only — cheapest</td>
    <td>Vector DB storage + API calls — moderate</td>
    <td>GPU compute for training + ongoing inference cost — most expensive</td>
  </tr>
  <tr>
    <td>Updatable</td>
    <td>Yes — change the prompt instantly</td>
    <td>Yes — add/update documents, no retraining</td>
    <td>No — must retrain when data changes significantly</td>
  </tr>
  <tr>
    <td>Hallucination risk</td>
    <td>Highest — model answers from training memory</td>
    <td>Lower for factual queries — grounded in retrieved docs</td>
    <td>Similar to base model — fine-tuning does not eliminate hallucination</td>
  </tr>
  <tr>
    <td>Indian IT context</td>
    <td>90%+ of daily professional use cases</td>
    <td>Internal knowledge tools, banking chatbots, compliance systems</td>
    <td>Company-specific code style models, domain classifiers, specialised NLP</td>
  </tr>
</tbody>
</table>
</div>

---

## When fine-tuning is actually the right answer

Fine-tuning is for form, not facts. You use it to shape behaviour, style, structured output, and refusal patterns — not to inject knowledge that changes frequently. Here are the four situations where fine-tuning genuinely makes sense:

<div class="img-center"><svg width="680" viewBox="0 0 680 170" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Four situations where fine-tuning is the right choice: consistent output format, domain style, performance ceiling reached, or cost slash needed</title>
<rect x="0" y="0" width="680" height="170" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="340" y="22" text-anchor="middle" font-size="11" font-weight="700" fill="#555" font-family="sans-serif">FOUR SITUATIONS WHERE FINE-TUNING IS JUSTIFIED</text>
<rect x="14" y="36" width="152" height="118" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="90" y="58" text-anchor="middle" font-size="11" font-weight="700" fill="#FF8C00" font-family="sans-serif">1. Consistent format</text>
<text x="90" y="76" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">You need the same</text>
<text x="90" y="89" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">structured output every</text>
<text x="90" y="102" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">time — JSON schema,</text>
<text x="90" y="115" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">medical coding, specific</text>
<text x="90" y="128" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">report templates.</text>
<text x="90" y="146" text-anchor="middle" font-size="9" font-style="italic" fill="#888" font-family="sans-serif">Prompting is unreliable at scale</text>
<rect x="180" y="36" width="152" height="118" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="256" y="58" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">2. Domain style</text>
<text x="256" y="76" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">Your org has a specific</text>
<text x="256" y="89" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">tone, vocabulary, or</text>
<text x="256" y="102" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">domain pattern that</text>
<text x="256" y="115" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">must be consistent</text>
<text x="256" y="128" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">without long prompts.</text>
<text x="256" y="146" text-anchor="middle" font-size="9" font-style="italic" fill="#888" font-family="sans-serif">e.g. company code style guide</text>
<rect x="346" y="36" width="152" height="118" rx="7" fill="#e8f5e9" stroke="#a5d6a7" stroke-width="1"/>
<text x="422" y="58" text-anchor="middle" font-size="11" font-weight="700" fill="#2e7d32" font-family="sans-serif">3. Prompting ceiling</text>
<text x="422" y="76" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">You have genuinely</text>
<text x="422" y="89" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">exhausted prompting —</text>
<text x="422" y="102" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">CoT, few-shot, role,</text>
<text x="422" y="115" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">structured output — and</text>
<text x="422" y="128" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">performance is still low.</text>
<text x="422" y="146" text-anchor="middle" font-size="9" font-style="italic" fill="#888" font-family="sans-serif">Needs evaluation data to prove</text>
<rect x="512" y="36" width="154" height="118" rx="7" fill="#ffeaea" stroke="#ef9a9a" stroke-width="1"/>
<text x="589" y="58" text-anchor="middle" font-size="11" font-weight="700" fill="#c62828" font-family="sans-serif">4. Cost at scale</text>
<text x="589" y="76" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">Millions of queries/day</text>
<text x="589" y="89" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">make large model API</text>
<text x="589" y="102" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">costs unsustainable.</text>
<text x="589" y="115" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">A fine-tuned 7B model</text>
<text x="589" y="128" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">at 1/50th the cost.</text>
<text x="589" y="146" text-anchor="middle" font-size="9" font-style="italic" fill="#888" font-family="sans-serif">Rarely relevant at enterprise POC stage</text>
</svg></div>

---

## The three fine-tuning methods you will hear about

You do not need to run fine-tuning yourself to be in this conversation. But knowing what LoRA and QLoRA mean — and why they matter — is now expected in Indian IT AI project discussions.

<div class="mod-method-grid">
  <div class="mod-method-card">
    <div class="mod-method-title">Full fine-tuning</div>
    <div class="mod-method-text">Updates all model weights. Highest performance ceiling, but requires significant GPU memory and compute. Expensive and slow. Only large organisations with ML infrastructure run this.</div>
    <span class="mod-method-badge mod-badge-red">High cost — rarely used in Indian IT</span>
  </div>
  <div class="mod-method-card">
    <div class="mod-method-title">LoRA / QLoRA</div>
    <div class="mod-method-text">Parameter-efficient fine-tuning — only a small adapter layer is trained on top of the frozen base model. QLoRA adds quantisation (uses less memory). Gets 90% of full fine-tuning performance at 10–100x lower cost. The standard enterprise approach in 2026.</div>
    <span class="mod-method-badge mod-badge-green">Recommended — most enterprise use cases</span>
  </div>
  <div class="mod-method-card">
    <div class="mod-method-title">Instruction tuning</div>
    <div class="mod-method-text">Teaches the model to follow your specific instructions, format, or template. Used when you need the model to reliably follow a particular output schema (JSON, a specific report format) without being told in every prompt.</div>
    <span class="mod-method-badge mod-badge-orange">Good for format consistency</span>
  </div>
</div>

<div class="mod-keypoint">
<strong>The practical point:</strong> QLoRA fine-tuning on a 7B–13B parameter model gets approximately 90% of GPT-4 performance on narrow, specific tasks at approximately 1/50th the inference cost. This is the right choice for most enterprise fine-tuning use cases in Indian IT in 2026 — when fine-tuning is justified at all.
</div>

---

## Real Indian IT scenarios — which approach?

<div class="mod-india-grid">
  <div class="mod-india-card">
    <div class="mod-india-title">&#128226; HR policy chatbot at a 10,000-employee Indian company</div>
    <div class="mod-india-text">Employees ask about leave policies, salary slips, and appraisal processes. The HR policy document changes quarterly. The questions are factual and answers must be accurate and current.</div>
    <span class="mod-india-verdict" style="background:#e3f2fd;color:#1565C0;border:1px solid #90caf9">Answer: RAG — not fine-tuning. Knowledge changes frequently, documents exist, no behaviour change needed.</span>
  </div>
  <div class="mod-india-card">
    <div class="mod-india-title">&#128187; Code review tool for a company's Java style guide</div>
    <div class="mod-india-text">The company has a 50-page internal Java style guide with specific naming conventions, patterns, and anti-patterns. They want AI to flag violations consistently without a long system prompt per review.</div>
    <span class="mod-india-verdict" style="background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7">Answer: Fine-tuning (LoRA). Consistent style behaviour needed. Training data is the style guide violations + corrections.</span>
  </div>
  <div class="mod-india-card">
    <div class="mod-india-title">&#128203; Weekly project status report generator</div>
    <div class="mod-india-text">A delivery manager pastes bullet points and wants a formatted status report in the standard company template every Friday. The template is consistent but the content changes weekly.</div>
    <span class="mod-india-verdict" style="background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7">Answer: Prompting — few-shot with the template example. No fine-tuning or RAG needed. The template is a few-shot example.</span>
  </div>
  <div class="mod-india-card">
    <div class="mod-india-title">&#127963; Customer support bot for an Indian insurance company</div>
    <div class="mod-india-text">Customers ask about policy terms, claim procedures, and premium calculations. Policy documents are 200+ pages, change with regulatory updates, and have India-specific terms like IRDAI, ULIP, and NPS.</div>
    <span class="mod-india-verdict" style="background:#e3f2fd;color:#1565C0;border:1px solid #90caf9">Answer: RAG with domain prompt tuning. RAG for the policy knowledge, a specialised prompt for the Indian insurance context and terminology.</span>
  </div>
  <div class="mod-india-card">
    <div class="mod-india-title">&#128200; Sentiment classifier for 1 million daily customer reviews</div>
    <div class="mod-india-text">An e-commerce company receives a million product reviews daily in Hindi and English. They need to classify sentiment and sub-category (delivery, quality, price) at scale with low latency.</div>
    <span class="mod-india-verdict" style="background:#fff8e1;color:#e65c00;border:1px solid #FFB300">Answer: Fine-tuning + distillation. Prompting won't scale. A fine-tuned small model on labelled examples is the right architecture.</span>
  </div>
  <div class="mod-india-card">
    <div class="mod-india-title">&#127979; Study assistant for engineering students</div>
    <div class="mod-india-text">A college wants an AI assistant that answers questions about their specific curriculum, NPTEL course material, and past exam papers — updated each semester when new material is uploaded.</div>
    <span class="mod-india-verdict" style="background:#e3f2fd;color:#1565C0;border:1px solid #90caf9">Answer: RAG. Course material is the knowledge base. Updates each semester with no retraining. Fine-tuning would be expensive and stale.</span>
  </div>
</div>

---

## The decision framework — four questions to ask

<div class="mod-decision">
<div class="mod-decision-title">ASK THESE FOUR QUESTIONS IN ORDER BEFORE RECOMMENDING AN APPROACH</div>
<div class="mod-drow">
  <span class="mod-dq">Is the problem that the model doesn't have the right information?</span>
  <span class="mod-darrow">→</span>
  <span class="mod-dans"><strong>Use RAG.</strong> Give it access to your documents. No fine-tuning needed. This is the correct diagnosis for 80% of "the model doesn't know our stuff" problems.</span>
</div>
<div class="mod-drow">
  <span class="mod-dq">Is the problem that the model isn't behaving the way you want — style, format, tone, refusals?</span>
  <span class="mod-darrow">→</span>
  <span class="mod-dans"><strong>Try better prompting first.</strong> Few-shot examples with 2–3 samples of the desired output almost always solve format and style problems. If prompting genuinely cannot solve it after real effort, then consider fine-tuning.</span>
</div>
<div class="mod-drow">
  <span class="mod-dq">Have you genuinely exhausted prompting — CoT, few-shot, role, structured output, refinement?</span>
  <span class="mod-darrow">→</span>
  <span class="mod-dans"><strong>Only now consider fine-tuning.</strong> Do you have 500+ high-quality labelled examples? Do you have the time and budget for 2–4 weeks of data preparation plus training? If yes to both, fine-tuning may be appropriate.</span>
</div>
<div class="mod-drow">
  <span class="mod-dq">Is the problem that the working solution is too expensive to run at your required scale?</span>
  <span class="mod-darrow">→</span>
  <span class="mod-dans"><strong>Consider distillation.</strong> Use the large model to generate labelled outputs, then train a smaller model on those outputs. Only relevant at very high query volumes — not a typical Indian IT enterprise concern at the POC stage.</span>
</div>
</div>

---

## The hidden cost of fine-tuning most teams miss

When teams decide to fine-tune, they typically budget for compute costs. The real cost is elsewhere. The operational cost of maintaining a fine-tuned model — adapter versioning, rollback plans, retraining cadence, and base-model drift management — are recurring costs, not one-time work.

When a hosted provider updates their base model, your adapter may degrade silently. Plan quarterly revalidation. Treat training configs, seeds, and dataset snapshots as code. Budget three to five times the training cost for ongoing lifecycle ownership over the next 12 months. The real cost is not the training compute — it is the evaluation, data curation, and lifecycle ownership.

This is why the decision framework above consistently recommends exhausting prompting and RAG before committing to fine-tuning. For most Indian IT enterprise use cases in 2026, the correct answer is a well-engineered RAG system combined with carefully crafted prompts — not a fine-tuned model.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 4.3</div>
  <ol>
    <li><strong>The right sequence is Prompt → RAG → Fine-tune</strong> — prompting solves approximately 70% of problems, RAG solves most knowledge-gap problems, and fine-tuning is for the remaining cases where behaviour genuinely cannot be achieved through prompting. Moving to fine-tuning before exhausting the earlier levels wastes significant time and money.</li>
    <li><strong>Fine-tuning is for form, not facts</strong> — use it to teach consistent behaviour, style, format, and output patterns. Never use it to inject factual knowledge that changes over time. That is what RAG is for. The best 2026 architecture is hybrid: RAG for volatile knowledge, fine-tuning for stable behaviour.</li>
    <li><strong>The hidden cost is lifecycle, not training</strong> — fine-tuning creates an ongoing maintenance obligation. Adapter versioning, quarterly revalidation, and base model drift management are recurring costs. Budget three to five times the training cost for the first year of operations. This calculation alone rules out fine-tuning for most Indian IT enterprise use cases.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-43">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 4.3 — Apply the Decision Framework to a Real Use Case</h3>
  </div>
  <p>This assignment develops the architectural reasoning skill that distinguishes AI practitioners from AI tool users.</p>
  <ol>
    <li><strong>Choose a real AI use case</strong> from your domain — either the RAG use case from Assignment 4.1, the agent workflow from Assignment 4.2, or a new one. Describe it in two sentences: what the system does and who uses it.</li>
    <li><strong>Work through the four-question decision framework:</strong>
      <ul>
        <li>Is the problem a knowledge gap? → if yes, describe the RAG implementation</li>
        <li>Is it a behaviour problem? → if yes, describe what prompting approach to try first</li>
        <li>Would prompting genuinely fail here? → if yes, justify why and what training data would look like</li>
        <li>Is scale and cost the driver? → if yes, describe the query volume and economics</li>
      </ul>
    </li>
    <li><strong>State your recommendation</strong> — Prompting, RAG, Fine-tuning, or a combination — with one paragraph justifying the choice using the criteria from this module.</li>
    <li><strong>Add to your AI Learning Journal</strong> under "Module 4.3 — Architecture Decision." Together with Assignments 4.1 and 4.2, this completes your Unit 4 AI architecture portfolio — three concrete examples showing you can think at a systems level.</li>
  </ol>
  <p>Being able to recommend Prompt vs RAG vs Fine-tuning with clear justification — and explain why fine-tuning is usually not the answer — is one of the most valued skills in every AI project discussion at Indian IT companies right now.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit4/module-4-2-ai-agents-workflows/">&#8592; Module 4.2: AI Agents and Workflows</a>
  <a class="mod-nav-next" href="/courses/genai/unit4/module-4-4-nocode-ai-tools/">Module 4.4: No-Code AI Tools &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>Prompt engineering solves ~70% of LLM problems; fine-tuning is the 30% solution</td><td>ortemtech.com Enterprise LLM Fine-Tuning Guide 2026; gauraw.com Fine-Tuning LLM Guide March 2026</td></tr>
      <tr><td>Right sequence in 2026: Prompt → RAG → Fine-tune → Distill</td><td>bigdataboutique.com Fine-Tuning LLMs When RAG Isn't Enough, May 2026</td></tr>
      <tr><td>Fine-tuning is for form not facts — style, behaviour, output patterns</td><td>bigdataboutique.com May 2026; umesh-malik.com RAG vs Fine-Tuning February 2026</td></tr>
      <tr><td>Most teams reach for fine-tuning too early; better prompt would solve it in an afternoon</td><td>gauraw.com March 2026</td></tr>
      <tr><td>QLoRA gets 90% of full fine-tuning performance at 10–100x lower cost</td><td>ortemtech.com June 2026</td></tr>
      <tr><td>A fine-tuned 7B model outperforms GPT-4o on specific task at 1/50th inference cost</td><td>ortemtech.com Enterprise LLM Fine-Tuning Guide June 2026</td></tr>
      <tr><td>Budget 3–5x training cost for lifecycle ownership over 12 months; quarterly revalidation needed</td><td>bigdataboutique.com May 2026</td></tr>
      <tr><td>Best 2026 pattern: retrieval for facts, fine-tuning for style and decision behaviour</td><td>umesh-malik.com RAG vs Fine-Tuning February 2026</td></tr>
      <tr><td>For knowledge bases under 200K tokens, full-context prompting + prompt caching can beat RAG</td><td>umesh-malik.com citing Anthropic documentation, February 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
