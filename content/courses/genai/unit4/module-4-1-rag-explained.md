---
title: "Module 4.1: RAG — Retrieval Augmented Generation Explained Simply"
description: "Understand how RAG works, why it matters for Indian IT professionals, and where it is being deployed in enterprise AI — explained without jargon for students and freshers."
weight: 1
sidebar: false
mainroad_aside: false
tags: ["rag", "retrieval-augmented-generation", "enterprise-ai", "india", "generative-ai", "advanced"]
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
/* ── Stat grid ───────────────────────────────────────────────── */
.mod-stat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:20px 0}
.mod-stat-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;text-align:center}
.mod-stat-card-num{font-size:24px;font-weight:700;color:#1565C0;margin-bottom:4px}
.mod-stat-card-label{font-size:12px;color:#666;line-height:1.4}
/* ── Analogy box ─────────────────────────────────────────────── */
.mod-analogy{background:#f5f8ff;border:1px solid #90caf9;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-analogy-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.05em;margin-bottom:10px}
.mod-analogy-text{font-size:14px;color:#333;line-height:1.75;margin:0}
/* ── Step flow ───────────────────────────────────────────────── */
.mod-steps{margin:20px 0}
.mod-step{display:flex;align-items:flex-start;gap:14px;padding:14px 0;border-bottom:1px solid #f0f0f0}
.mod-step:last-child{border-bottom:none}
.mod-step-num{width:32px;height:32px;border-radius:50%;background:#1565C0;color:#fff;font-size:13px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px}
.mod-step-body{flex:1}
.mod-step-title{font-size:14px;font-weight:700;color:#1565C0;margin:0 0 4px}
.mod-step-text{font-size:13px;color:#333;line-height:1.6;margin:0}
.mod-step-example{font-size:12px;font-family:monospace,sans-serif;background:#f5f5f4;border-radius:4px;padding:6px 10px;color:#555;margin-top:6px;line-height:1.5;border-left:3px solid #1565C0}
/* ── Comparison grid ─────────────────────────────────────────── */
.mod-compare{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-compare-card{border-radius:8px;padding:16px;border:1px solid}
.mod-compare-card h3{font-size:14px;font-weight:700;margin:0 0 8px}
.mod-compare-list{margin:0;padding-left:16px}
.mod-compare-list li{font-size:13px;line-height:1.65;margin-bottom:4px;color:#333}
/* ── Use case cards ──────────────────────────────────────────── */
.mod-usecase-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-uc-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-uc-card-header{display:flex;align-items:center;gap:8px;margin-bottom:8px}
.mod-uc-icon{font-size:16px;flex-shrink:0}
.mod-uc-title{font-size:13px;font-weight:700;color:#1565C0;margin:0}
.mod-uc-text{font-size:13px;color:#333;line-height:1.6;margin:0}
.mod-uc-example{font-size:12px;color:#666;margin-top:6px;line-height:1.5;font-style:italic}
/* ── Interview table ─────────────────────────────────────────── */
.mod-table-wrap{overflow-x:auto;margin:20px 0}
.mod-table{width:100%;border-collapse:collapse;font-size:13px}
.mod-table th{background:#1565C0;color:#fff;padding:10px 13px;text-align:left;font-weight:600;font-size:12px}
.mod-table td{padding:10px 13px;border-bottom:1px solid #f0f0f0;color:#111111;vertical-align:top;line-height:1.5}
.mod-table tr:last-child td{border-bottom:none}
.mod-table tr:nth-child(even) td{background:#fafafa}
.mod-table td:first-child{font-weight:600;color:#1565C0}
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
@media(max-width:520px){.mod-stat-grid{grid-template-columns:1fr 1fr}.mod-compare{grid-template-columns:1fr}.mod-usecase-grid{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:60%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">12 of 20 modules complete</div>
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
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 4 &nbsp;›&nbsp; MODULE 1 OF 4</span>
    <h1 class="mod-title-inline">RAG — Retrieval Augmented Generation Explained Simply</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">No coding required</span>
  </div>
</div>

Welcome to Unit 4. In Units 1–3 you built prompt engineering skills and applied them to real work. Unit 4 goes deeper into how enterprise AI actually works — the architectures and techniques that power the AI systems being built at TCS, Infosys, Wipro, and HCL right now.

This module covers RAG — the most important AI concept in enterprise deployments in 2025–2026. You do not need to build a RAG system to understand this module. You need to understand what it is, why companies use it, and how to talk about it intelligently — which is what every placement interview at an AI-forward Indian IT company will test you on.

---

## Why RAG matters right now

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">$40B</div>
    <div class="mod-stat-card-label">RAG market projected by 2035, growing from $1.96B in 2025 — Grand View Research</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">330K+</div>
    <div class="mod-stat-card-label">employees at Infosys, TCS, and Wipro now using Microsoft 365 Copilot — a RAG-powered tool — as of June 2026</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">85%</div>
    <div class="mod-stat-card-label">of enterprises projected to adopt hybrid RAG systems combining vector and graph databases by 2026</div>
  </div>
</div>

RAG is an AI architecture that combines retrieval-based methods with generative models to produce more relevant and accurate outputs. Instead of relying solely on the pre-trained knowledge stored in a large language model, RAG enables the model to fetch relevant documents or data from an external knowledge base in real-time. This one idea — giving the AI access to *your* data, not just its training data — is what makes enterprise AI actually useful.

---

## The problem RAG solves

You already know from Module 1.1 that LLMs have a knowledge cutoff — they only know what was in their training data. This creates a fundamental problem for enterprise use:

<div class="mod-compare">
  <div class="mod-compare-card" style="background:#ffeaea;border-color:#ef9a9a">
    <h3 style="color:#c62828">Without RAG — what goes wrong</h3>
    <ul class="mod-compare-list">
      <li>Ask about your company's internal HR policy → model guesses or hallucinates</li>
      <li>Ask about a client project → model has no knowledge of it</li>
      <li>Ask about last week's product release notes → training data is months old</li>
      <li>Ask about your bank's specific loan scheme → model describes generic loans</li>
      <li>Ask about your codebase's architecture → model cannot access your repository</li>
    </ul>
  </div>
  <div class="mod-compare-card" style="background:#e8f5e9;border-color:#a5d6a7">
    <h3 style="color:#2e7d32">With RAG — what becomes possible</h3>
    <ul class="mod-compare-list">
      <li>Ask about your HR policy → model retrieves the actual document and answers from it</li>
      <li>Ask about a client project → model retrieves the project wiki and summarises accurately</li>
      <li>Ask about release notes → model retrieves the latest file and answers specifically</li>
      <li>Ask about your loan scheme → model retrieves your product manual and explains it correctly</li>
      <li>Ask about your codebase → model retrieves relevant code files and explains them</li>
    </ul>
  </div>
</div>

<div class="mod-keypoint">
<strong>The core insight:</strong> A standard LLM knows what the world knew up to its training cutoff. A RAG system knows what the world knew up to its training cutoff <em>plus</em> whatever documents you give it access to. That addition — your company's documents, your client's data, your product manuals — is what makes AI genuinely useful for enterprise work.
</div>

---

## How RAG works — the five steps

<div class="mod-analogy">
<div class="mod-analogy-title">ANALOGY — THE OPEN-BOOK EXAM</div>
<div class="mod-analogy-text">Think of a standard LLM as a closed-book exam — the model answers from memory only, and if the answer was not in what it studied, it may guess (hallucinate). RAG is an open-book exam — before answering, the model is allowed to look up the most relevant pages in your textbook. It still needs intelligence to interpret and synthesise what it finds, but it is no longer limited to what it memorised. The textbook is your company's data.</div>
</div>

<div class="mod-steps">

<div class="mod-step">
  <div class="mod-step-num">1</div>
  <div class="mod-step-body">
    <div class="mod-step-title">User asks a question</div>
    <div class="mod-step-text">A user types a query — this could be through a chatbot interface, a search box, or an internal tool. The query is captured and passed to the RAG system.</div>
    <div class="mod-step-example">User: "What is the leave encashment policy for Infosys employees in Bengaluru?"</div>
  </div>
</div>

<div class="mod-step">
  <div class="mod-step-num">2</div>
  <div class="mod-step-body">
    <div class="mod-step-title">Query is converted to a vector (embedding)</div>
    <div class="mod-step-text">The query is passed through an embedding model that converts it into a numerical representation — a vector — that captures the semantic meaning of the question. Similar concepts will have similar vectors even if the exact words differ.</div>
    <div class="mod-step-example">"Leave encashment policy Bengaluru" → [0.82, -0.14, 0.67, ...] (a list of numbers representing the meaning)</div>
  </div>
</div>

<div class="mod-step">
  <div class="mod-step-num">3</div>
  <div class="mod-step-body">
    <div class="mod-step-title">Vector database is searched for similar content</div>
    <div class="mod-step-text">The system searches a vector database — which contains your company's documents, also converted to vectors — to find the most semantically similar chunks of text. This is not a keyword search; it finds conceptually related content even if the words are different.</div>
    <div class="mod-step-example">Retrieves: HR Policy Manual Section 7.3 (Leave Encashment), Circular 2025-HR-42 (Bengaluru Specific Rules), FAQ_Leave_Policy.pdf pages 12–14</div>
  </div>
</div>

<div class="mod-step">
  <div class="mod-step-num">4</div>
  <div class="mod-step-body">
    <div class="mod-step-title">Retrieved content is added to the prompt</div>
    <div class="mod-step-text">The retrieved document chunks are added to the LLM's context window alongside the original question. This is the "augmented" part — the prompt now contains both the question and the relevant source material.</div>
    <div class="mod-step-example">Prompt to LLM: "Answer this question using only the provided documents: [Question] [HR Policy Section 7.3] [Circular 2025-HR-42] [FAQ pages 12-14]"</div>
  </div>
</div>

<div class="mod-step">
  <div class="mod-step-num">5</div>
  <div class="mod-step-body">
    <div class="mod-step-title">LLM generates a grounded answer</div>
    <div class="mod-step-text">The LLM reads both the question and the retrieved documents and generates an answer grounded in the actual source material — not from its training data. Many systems also include citations so the user can verify the source.</div>
    <div class="mod-step-example">Response: "According to HR Policy Section 7.3 and Circular 2025-HR-42, Infosys employees in Bengaluru can encash up to 30 days of earned leave per year at their basic salary rate, subject to a minimum balance of 15 days..."</div>
  </div>
</div>

</div>

---

## RAG in action — visual flow

<div class="img-center"><svg width="680" viewBox="0 0 680 180" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>RAG five-step flow: User query converted to vector, searched in vector database, retrieved chunks added to prompt, LLM generates grounded answer</title>
<defs><marker id="r1" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<rect x="0" y="0" width="680" height="180" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="340" y="20" text-anchor="middle" font-size="11" font-weight="700" fill="#555" font-family="sans-serif">HOW RAG WORKS — FIVE STEPS</text>
<!-- Step 1: User -->
<rect x="12" y="36" width="100" height="56" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="62" y="58" text-anchor="middle" font-size="10" font-weight="700" fill="#1565C0" font-family="sans-serif">1. User</text>
<text x="62" y="73" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">asks a</text>
<text x="62" y="86" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">question</text>
<line x1="112" y1="64" x2="128" y2="64" stroke="#1565C0" stroke-width="1.5" marker-end="url(#r1)"/>
<!-- Step 2: Embed -->
<rect x="128" y="36" width="108" height="56" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="182" y="58" text-anchor="middle" font-size="10" font-weight="700" fill="#1565C0" font-family="sans-serif">2. Embed</text>
<text x="182" y="73" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">query → vector</text>
<text x="182" y="86" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">[0.82, -0.14...]</text>
<line x1="236" y1="64" x2="252" y2="64" stroke="#1565C0" stroke-width="1.5" marker-end="url(#r1)"/>
<!-- Step 3: Retrieve -->
<rect x="252" y="28" width="108" height="72" rx="7" fill="#1565C0" stroke="#0d47a1" stroke-width="1"/>
<text x="306" y="52" text-anchor="middle" font-size="10" font-weight="700" fill="#fff" font-family="sans-serif">3. Retrieve</text>
<text x="306" y="67" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">search vector</text>
<text x="306" y="80" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">database</text>
<text x="306" y="92" text-anchor="middle" font-size="9" fill="rgba(255,255,255,0.75)" font-family="sans-serif">top-k chunks</text>
<!-- Vector DB below step 3 -->
<rect x="262" y="116" width="88" height="40" rx="5" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="306" y="132" text-anchor="middle" font-size="9" font-weight="700" fill="#FF8C00" font-family="sans-serif">Vector DB</text>
<text x="306" y="147" text-anchor="middle" font-size="9" fill="#888" font-family="sans-serif">Company docs</text>
<line x1="306" y1="116" x2="306" y2="100" stroke="#FF8C00" stroke-width="1.5" stroke-dasharray="3 2" marker-end="url(#r1)"/>
<line x1="360" y1="64" x2="376" y2="64" stroke="#1565C0" stroke-width="1.5" marker-end="url(#r1)"/>
<!-- Step 4: Augment -->
<rect x="376" y="36" width="108" height="56" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="430" y="58" text-anchor="middle" font-size="10" font-weight="700" fill="#FF8C00" font-family="sans-serif">4. Augment</text>
<text x="430" y="73" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">question +</text>
<text x="430" y="86" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">retrieved docs</text>
<line x1="484" y1="64" x2="500" y2="64" stroke="#1565C0" stroke-width="1.5" marker-end="url(#r1)"/>
<!-- Step 5: Generate -->
<rect x="500" y="36" width="168" height="56" rx="7" fill="#e8f5e9" stroke="#a5d6a7" stroke-width="1"/>
<text x="584" y="55" text-anchor="middle" font-size="10" font-weight="700" fill="#2e7d32" font-family="sans-serif">5. Generate</text>
<text x="584" y="70" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">LLM answers from</text>
<text x="584" y="83" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">retrieved content</text>
<text x="340" y="168" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Result: grounded answer with citations — not a hallucination from training memory</text>
</svg></div>

---

## RAG vs fine-tuning — what is the difference?

This is one of the most common interview questions in Indian IT AI roles. Both approaches customise an LLM for specific use, but they work very differently.

<div class="mod-table-wrap">
<table class="mod-table">
<thead><tr><th>Dimension</th><th>RAG</th><th>Fine-tuning</th></tr></thead>
<tbody>
  <tr>
    <td>How it works</td>
    <td>Retrieves relevant documents at query time and adds them to the context</td>
    <td>Retrains the model weights on your specific data — changes the model permanently</td>
  </tr>
  <tr>
    <td>When data updates</td>
    <td>Update the document store — no model retraining needed. Changes take effect immediately</td>
    <td>Must retrain the model — expensive, slow, and requires ML expertise</td>
  </tr>
  <tr>
    <td>Best for</td>
    <td>Factual Q&A over documents, internal knowledge bases, current information</td>
    <td>Teaching a specific style, format, or task pattern the model must perform consistently</td>
  </tr>
  <tr>
    <td>Cost</td>
    <td>Lower — vector database + API calls</td>
    <td>Higher — GPU compute for training, ongoing maintenance</td>
  </tr>
  <tr>
    <td>Hallucination risk</td>
    <td>Lower for factual queries — answer grounded in retrieved documents</td>
    <td>Similar to base model — model may still confabulate if trained data was incomplete</td>
  </tr>
  <tr>
    <td>Indian IT context</td>
    <td>Used by Infosys Topaz, TCS AI platforms, internal knowledge tools at most major firms</td>
    <td>Used for specialised models: code completion tuned to company style guides, domain-specific classifiers</td>
  </tr>
</tbody>
</table>
</div>

<div class="mod-keypoint">
<strong>The one-sentence answer for interviews:</strong> RAG gives the model access to external documents at query time — no retraining needed, always up to date. Fine-tuning changes the model's weights to teach it a new behaviour permanently — powerful but expensive. For most enterprise document Q&A use cases, RAG is the right choice.
</div>

---

## Where RAG is being used in Indian IT right now

<div class="mod-usecase-grid">
  <div class="mod-uc-card">
    <div class="mod-uc-card-header">
      <span class="mod-uc-icon">&#127970;</span>
      <div class="mod-uc-title">Internal knowledge bases</div>
    </div>
    <div class="mod-uc-text">Employees ask questions about HR policies, project documentation, SOPs, and compliance rules in natural language. The RAG system retrieves the relevant document and answers accurately.</div>
    <div class="mod-uc-example">TCS, Infosys, Wipro — internal HR and policy chatbots. Infosys uses this within its Topaz platform across 200+ client deployments.</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-card-header">
      <span class="mod-uc-icon">&#127963;</span>
      <div class="mod-uc-title">Customer support and banking</div>
    </div>
    <div class="mod-uc-text">Indian banks and fintechs use RAG to power customer service chatbots that answer questions about products, interest rates, and eligibility using the bank's actual product documentation — not generic LLM knowledge.</div>
    <div class="mod-uc-example">HDFC, ICICI, SBI digital assistants. The system retrieves from the latest product circular, not training data from months ago.</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-card-header">
      <span class="mod-uc-icon">&#128188;</span>
      <div class="mod-uc-title">Legal and compliance</div>
    </div>
    <div class="mod-uc-text">Legal teams query contract repositories, regulatory documents, and compliance frameworks in natural language. RAG retrieves the specific clause or regulation and generates a grounded summary.</div>
    <div class="mod-uc-example">Used at Indian law firms, SEBI-regulated entities, and IT companies managing client contract libraries. 92% accuracy in legal document analysis reported using Knowledge Graph RAG.</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-card-header">
      <span class="mod-uc-icon">&#128200;</span>
      <div class="mod-uc-title">Code and technical documentation</div>
    </div>
    <div class="mod-uc-text">Developers query internal codebases, API documentation, and architecture wikis. The RAG system retrieves relevant code files or documentation pages before the LLM generates an explanation or recommendation.</div>
    <div class="mod-uc-example">GitHub Copilot Enterprise, Cursor IDE, and internal developer tools at Indian IT companies use RAG over private code repositories.</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-card-header">
      <span class="mod-uc-icon">&#127891;</span>
      <div class="mod-uc-title">Education and training</div>
    </div>
    <div class="mod-uc-text">University systems and corporate LMS platforms use RAG to answer student and employee questions from course material, policy documents, and knowledge bases — updated in real time as new material is added.</div>
    <div class="mod-uc-example">Indian ed-tech companies (Byju's, Unacademy), corporate training platforms at TCS iON. Course content is added to the document store — no model retraining needed.</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-card-header">
      <span class="mod-uc-icon">&#9874;</span>
      <div class="mod-uc-title">Manufacturing and operations</div>
    </div>
    <div class="mod-uc-text">Maintenance engineers query equipment manuals, failure history, and SOP libraries. The RAG system retrieves the relevant section of a 500-page technical manual and answers a specific question about a machine fault.</div>
    <div class="mod-uc-example">Infosys Engineering Services clients in auto and aerospace manufacturing. Replaces manual search through technical documentation that used to take hours.</div>
  </div>
</div>

---

## What RAG cannot do — knowing the limits

<div class="mod-compare">
  <div class="mod-compare-card" style="background:#e8f5e9;border-color:#a5d6a7">
    <h3 style="color:#2e7d32">RAG is excellent for</h3>
    <ul class="mod-compare-list">
      <li>Answering factual questions from documents</li>
      <li>Keeping answers up to date without retraining</li>
      <li>Citing sources so users can verify answers</li>
      <li>Internal knowledge Q&amp;A at any scale</li>
      <li>Reducing hallucination on domain-specific queries</li>
    </ul>
  </div>
  <div class="mod-compare-card" style="background:#ffeaea;border-color:#ef9a9a">
    <h3 style="color:#c62828">RAG cannot</h3>
    <ul class="mod-compare-list">
      <li>Answer questions not covered in the document store</li>
      <li>Reason across documents if the connections are implicit</li>
      <li>Guarantee accuracy — retrieval quality determines answer quality</li>
      <li>Replace fine-tuning when behavioural change is needed</li>
      <li>Work well with very poorly structured or noisy documents</li>
    </ul>
  </div>
</div>

The most important insight from enterprise RAG deployments in 2025 and 2026 is straightforward: RAG is only as good as the quality and reliability of the underlying knowledge source. Garbage documents in, garbage answers out — regardless of how sophisticated the retrieval system is.

---

## RAG in 2026 — what has evolved

By 2026, Agentic RAG is the baseline for any serious AI application — trading a small amount of latency and token cost for a massive increase in reliability. Three developments matter for your career awareness:

**Agentic RAG** — the system does not just retrieve once; an AI agent decides what to search for, evaluates what it finds, and may search again with a refined query. This produces better answers on complex questions but takes longer.

**GraphRAG** — instead of retrieving text chunks, the system retrieves a knowledge graph — entities, relationships, and connections. Better for questions that require reasoning across multiple related pieces of information. Microsoft has open-sourced a GraphRAG framework actively used by Indian IT companies.

**Hybrid RAG** — combines keyword search (traditional) with semantic search (vector). More robust than either alone for enterprise datasets where exact terms (product codes, regulation numbers) matter alongside meaning.

For a fresher or junior professional, you do not need to build any of these. You need to recognise the terms, understand what problem each solves, and be able to discuss them intelligently when they come up in a project context or interview.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 4.1</div>
  <ol>
    <li><strong>RAG = LLM + your documents, at query time</strong> — the model retrieves relevant content from your knowledge base before answering. This gives it access to current, domain-specific information without retraining. It is why enterprise AI chatbots can answer accurately about internal policies, product details, and recent documents.</li>
    <li><strong>RAG vs fine-tuning: retrieval vs retraining</strong> — RAG is the right choice when you need accurate, updatable factual Q&amp;A over documents. Fine-tuning is the right choice when you need the model to consistently behave in a specific way. For most Indian IT enterprise use cases in 2026, RAG is deployed far more often than fine-tuning.</li>
    <li><strong>Answer quality depends on document quality</strong> — a RAG system is only as reliable as the knowledge base it retrieves from. Poorly organised, outdated, or inaccurate source documents produce poor answers even with the best retrieval system. In any RAG project, data quality is the most important non-technical factor.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-41">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 4.1 — Identify a RAG Use Case in Your Domain</h3>
  </div>
  <p>This assignment develops your ability to apply RAG thinking to real situations — the skill interviewers test when asking about AI architecture.</p>
  <ol>
    <li><strong>Identify one RAG opportunity</strong> in a domain you know well — your college, your target industry, or a company you have researched. Ask yourself: "What questions do people repeatedly ask that could be answered from a set of documents?" Good candidates: student handbook Q&amp;A, technical documentation search, policy lookup, product catalogue questions.</li>
    <li><strong>Describe the system in five parts:</strong>
      <ul>
        <li><strong>The document store:</strong> What documents would you put in it? (Be specific — not "company documents" but "the 2026 HR policy manual, leave circulars, and the FAQ document")</li>
        <li><strong>The user:</strong> Who asks questions, and what kind of questions do they ask?</li>
        <li><strong>A sample query:</strong> Write one realistic question a user would ask</li>
        <li><strong>Expected retrieval:</strong> Which specific document or section should the system retrieve?</li>
        <li><strong>The benefit:</strong> What does this replace or improve compared to the current situation?</li>
      </ul>
    </li>
    <li><strong>Add to your AI Learning Journal</strong> under "Module 4.1 — RAG Use Case." This becomes part of your Company AI Research document from Assignment 1.3 — concrete evidence that you can think in AI architecture terms, not just tool terms.</li>
  </ol>
  <p>The ability to identify a RAG opportunity in a domain, describe the components clearly, and explain the benefit is exactly what TCS, Infosys, and Wipro look for when hiring for AI delivery roles. This assignment is interview preparation, not just coursework.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit3/module-3-4-prompt-library/">&#8592; Module 3.4: Your Prompt Library</a>
  <a class="mod-nav-next" href="/courses/genai/unit4/module-4-2-ai-agents-workflows/">Module 4.2: AI Agents and Workflows &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>RAG market growing from $1.96B in 2025 to $40.34B by 2035</td><td>Grand View Research, cited in moontechnolabs.com RAG Use Cases May 2025</td></tr>
      <tr><td>Infosys, TCS, and Wipro collectively deployed Microsoft 365 Copilot to 330,000+ employees by June 2026</td><td>windowsnews.ai, June 3 2026 — confirmed by Microsoft</td></tr>
      <tr><td>85% of enterprises projected to adopt hybrid RAG systems by 2026</td><td>newline.co / Neo4j research, January 2026</td></tr>
      <tr><td>RAG is an architecture combining retrieval with generation for more relevant outputs</td><td>IBM Think / ksolves.com February 2026</td></tr>
      <tr><td>RAG only as good as the quality of the underlying knowledge source</td><td>atlan.com — What Is RAG? How Retrieval-Augmented Generation Works in 2026, April 2026</td></tr>
      <tr><td>Agentic RAG is the baseline for serious AI applications in 2026</td><td>Medium / Reliable Data Engineering, January 2026</td></tr>
      <tr><td>92% accuracy in legal document analysis using Knowledge Graph RAG</td><td>newline.co / webAI research, January 2026</td></tr>
      <tr><td>RAG has evolved from simple retriever-generator pipeline to sophisticated enterprise architecture</td><td>techment.com RAG in 2026, May 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
