---
title: "Module 1.1: What is Generative AI — LLMs Explained Simply"
description: "Understand how LLMs and Generative AI actually work — explained in plain language for Indian students and freshers. No maths, no jargon."
weight: 1
sidebar: false
tags: ["generative-ai", "llm", "beginners", "india", "prompt-engineering"]
---

<style>
/* ── Module header bar ───────────────────────────────────────── */
.mod-header{background:#1565C0;border-radius:6px;padding:14px 18px;margin-bottom:24px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px}
.mod-header-left{display:flex;flex-direction:column;gap:4px}
.mod-breadcrumb{font-size:11px;color:rgba(255,255,255,0.75);letter-spacing:0.03em}
.mod-title-inline{font-size:15px;font-weight:600;color:#fff;margin:0}
.mod-meta{display:flex;gap:10px;flex-wrap:wrap}
.mod-meta-item{font-size:11px;color:rgba(255,255,255,0.85);background:rgba(255,255,255,0.15);padding:3px 10px;border-radius:20px}
/* ── Section callout boxes ───────────────────────────────────── */
.mod-keypoint{background:#fff8e1;border-left:4px solid #FF8C00;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a3000;line-height:1.6}
.mod-keypoint strong{color:#FF8C00}
.mod-remember{background:#e8f0fe;border-left:4px solid #1565C0;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0}
.mod-remember-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.06em;margin-bottom:8px}
.mod-remember ol{margin:0;padding-left:18px}
.mod-remember li{font-size:14px;color:#1a1a1a;line-height:1.7;margin-bottom:4px}
/* ── Assignment box ──────────────────────────────────────────── */
.mod-assignment{background:#fff8e1;border:1px solid #FFB300;border-radius:6px;padding:16px 18px;margin:28px 0}
.mod-assignment-header{display:flex;align-items:center;gap:8px;margin-bottom:10px}
.mod-assignment-icon{font-size:16px;color:#FF8C00}
.mod-assignment-title{font-size:14px;font-weight:700;color:#5d4037;margin:0}
.mod-assignment p,.mod-assignment li{font-size:14px;color:#4a3000;line-height:1.7}
.mod-assignment ol{padding-left:20px;margin:8px 0}
/* ── Navigation footer ───────────────────────────────────────── */
.mod-nav{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;margin-top:32px;padding-top:18px;border-top:1px solid #e0e0e0}
.mod-nav-back{font-size:13px;color:#1565C0;text-decoration:none;display:flex;align-items:center;gap:5px}
.mod-nav-back:hover{color:#0d47a1;text-decoration:underline}
.mod-nav-next{display:inline-flex;align-items:center;gap:6px;font-size:13px;font-weight:600;padding:9px 18px;border-radius:4px;background:#FF8C00;color:#fff !important;text-decoration:none}
.mod-nav-next:hover{background:#e65c00;color:#fff !important;text-decoration:none}
/* ── Blog links footer ───────────────────────────────────────── */
.mod-blog-links{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:6px;padding:14px 18px;margin-top:20px}
.mod-blog-title{font-size:11px;font-weight:700;color:#888;letter-spacing:0.06em;margin-bottom:8px}
.mod-blog-links a{display:block;font-size:13px;color:#1565C0;text-decoration:none;padding:3px 0;border-bottom:1px solid #f0f0f0}
.mod-blog-links a:last-child{border-bottom:none}
.mod-blog-links a:hover{color:#FF8C00;text-decoration:underline}
/* ── Body text readability ───────────────────────────────────── */
.mod-wrap p,.mod-wrap li,.mod-wrap td{font-size:15px;color:#222;line-height:1.8}
.mod-wrap h2{font-size:20px;color:#111;margin-top:32px;margin-bottom:12px}
.mod-wrap h3{font-size:17px;color:#111;margin-top:24px;margin-bottom:8px}
.mod-wrap strong{color:#111;font-weight:600}
.mod-wrap em{color:#333}
.mod-wrap code{font-size:14px;background:#f0f0f0;padding:2px 6px;border-radius:3px;color:#c62828}
/* ── Image credit table ──────────────────────────────────────── */
.mod-credits{font-size:12px;color:#888;margin-top:32px;padding-top:12px;border-top:1px solid #e0e0e0}
.mod-credits summary{cursor:pointer;font-size:12px;color:#aaa;list-style:none}
.mod-credits summary:hover{color:#888}
/* ── Centre-align all diagrams ───────────────────────────────── */
.img-center{display:flex;justify-content:center;margin:20px 0}
.img-center svg{max-width:100%;height:auto}
.img-center>div{max-width:680px;width:100%}
</style>

<div class="mod-wrap">
<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 1 &nbsp;›&nbsp; MODULE 1 OF 4</span>
    <h1 class="mod-title-inline">What is Generative AI — LLMs Explained Simply</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 12 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">No prerequisites</span>
  </div>
</div>

You have probably used ChatGPT, Copilot, or Gemini by now — maybe to draft an email, explain a bug, or summarise a document. But do you know what is actually happening when you type a message and the AI responds?

This module explains what Generative AI is, how Large Language Models work, and why this matters for your career in Indian IT — all without a single equation.

---

## What does "Generative AI" actually mean?

Let us start with the two words separately.

**AI (Artificial Intelligence)** is a broad term for software that can perform tasks that normally require human thinking — recognising images, translating languages, making decisions.

**Generative** means it creates new content. Earlier AI systems were mostly *discriminative* — they classified or predicted things. A spam filter decides: is this email spam or not spam? A recommendation engine decides: which movie should I suggest?

Generative AI is different. It *produces* something new — a paragraph of text, a line of code, an image, a piece of music — that did not exist before.

<div class="img-center"><svg width="680" viewBox="0 0 680 260" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Discriminative AI versus Generative AI</title>
<defs><marker id="a1" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker>
<marker id="a2" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<!-- Left panel: Discriminative -->
<rect x="10" y="10" width="310" height="240" rx="10" fill="#f5f5f4" stroke="#d3d1c7" stroke-width="1"/>
<rect x="10" y="10" width="310" height="44" rx="10" fill="#455a64"/>
<rect x="10" y="44" width="310" height="10" fill="#455a64"/>
<text x="165" y="37" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" font-family="sans-serif">Discriminative AI</text>
<text x="165" y="72" text-anchor="middle" font-size="11" fill="#666" font-family="sans-serif">classifies or decides</text>
<!-- Input box -->
<rect x="30" y="90" width="100" height="44" rx="6" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="80" y="107" text-anchor="middle" font-size="11" font-weight="600" fill="#1565C0" font-family="sans-serif">Input</text>
<text x="80" y="124" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">an email</text>
<!-- Arrow -->
<line x1="130" y1="112" x2="158" y2="112" stroke="#1565C0" stroke-width="1.5" marker-end="url(#a1)"/>
<!-- Output box -->
<rect x="158" y="90" width="142" height="44" rx="6" fill="#eceff1" stroke="#b0bec5" stroke-width="1"/>
<text x="229" y="107" text-anchor="middle" font-size="11" font-weight="600" fill="#37474f" font-family="sans-serif">Output</text>
<text x="229" y="124" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Spam / Not spam</text>
<!-- Examples -->
<rect x="30" y="158" width="270" height="68" rx="6" fill="#eceff1" stroke="#cfd8dc" stroke-width="1"/>
<text x="165" y="176" text-anchor="middle" font-size="10" font-weight="700" fill="#546e7a" font-family="sans-serif">EXAMPLES</text>
<text x="165" y="194" text-anchor="middle" font-size="11" fill="#555" font-family="sans-serif">Spam filters · Image classifiers</text>
<text x="165" y="211" text-anchor="middle" font-size="11" fill="#555" font-family="sans-serif">Recommendation engines</text>
<!-- Right panel: Generative -->
<rect x="360" y="10" width="310" height="240" rx="10" fill="#f5f5f4" stroke="#d3d1c7" stroke-width="1"/>
<rect x="360" y="10" width="310" height="44" rx="10" fill="#1565C0"/>
<rect x="360" y="44" width="310" height="10" fill="#1565C0"/>
<text x="515" y="37" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" font-family="sans-serif">Generative AI</text>
<text x="515" y="72" text-anchor="middle" font-size="11" fill="#666" font-family="sans-serif">creates new content</text>
<!-- Input box -->
<rect x="380" y="90" width="100" height="44" rx="6" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="430" y="107" text-anchor="middle" font-size="11" font-weight="600" fill="#1565C0" font-family="sans-serif">Input</text>
<text x="430" y="124" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">a prompt</text>
<!-- Arrow -->
<line x1="480" y1="112" x2="508" y2="112" stroke="#1565C0" stroke-width="1.5" marker-end="url(#a2)"/>
<!-- Output box -->
<rect x="508" y="90" width="142" height="44" rx="6" fill="#e8f0fe" stroke="#90caf9" stroke-width="1"/>
<text x="579" y="107" text-anchor="middle" font-size="11" font-weight="600" fill="#1565C0" font-family="sans-serif">Output</text>
<text x="579" y="124" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">New text / code / image</text>
<!-- Examples -->
<rect x="380" y="158" width="270" height="68" rx="6" fill="#e8f0fe" stroke="#90caf9" stroke-width="1"/>
<text x="515" y="176" text-anchor="middle" font-size="10" font-weight="700" fill="#1565C0" font-family="sans-serif">EXAMPLES</text>
<text x="515" y="194" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">ChatGPT · Claude · Gemini</text>
<text x="515" y="211" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">DALL-E · GitHub Copilot</text>
</svg></div>

The most powerful form of Generative AI today is built on **Large Language Models (LLMs)**.

---

## What is a Large Language Model?

An LLM is a type of AI trained on an enormous amount of text — books, websites, research papers, code repositories, forum posts, and more. The training data for GPT-3 is estimated to include over 300 billion words.

During training, the model learns one thing at a deep level:

<div class="mod-keypoint">
<strong>Core idea:</strong> Given a sequence of words, what word is most likely to come next?
</div>

That sounds simple. But when you do this billions of times, across hundreds of billions of examples, the model ends up learning something profound — it learns the patterns of human knowledge itself.

It learns that after "The capital of India is", the word "New" followed by "Delhi" is overwhelmingly likely. It learns that after `def calculate_tax(income):`, a line of Python code is expected, not a recipe. It learns the tone of a formal email versus a WhatsApp message.

None of this was explicitly programmed. It emerged from pattern learning at massive scale.

<div class="img-center"><svg width="680" viewBox="0 0 680 300" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>How an LLM predicts the next token — probability distribution</title>
<defs><marker id="b1" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<!-- Input box -->
<rect x="10" y="108" width="190" height="60" rx="8" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="105" y="132" text-anchor="middle" font-size="12" font-weight="600" fill="#1565C0" font-family="sans-serif">"The capital of</text>
<text x="105" y="152" text-anchor="middle" font-size="12" font-weight="600" fill="#1565C0" font-family="sans-serif">India is ___"</text>
<!-- Arrow -->
<line x1="200" y1="138" x2="228" y2="138" stroke="#1565C0" stroke-width="1.5" marker-end="url(#b1)"/>
<!-- LLM box -->
<rect x="228" y="100" width="144" height="76" rx="8" fill="#1565C0" stroke="#0d47a1" stroke-width="1"/>
<text x="300" y="132" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" font-family="sans-serif">LLM</text>
<text x="300" y="152" text-anchor="middle" font-size="11" fill="rgba(255,255,255,0.85)" font-family="sans-serif">175B+ parameters</text>
<!-- Arrow -->
<line x1="372" y1="138" x2="400" y2="138" stroke="#1565C0" stroke-width="1.5" marker-end="url(#b1)"/>
<!-- Chart label -->
<text x="404" y="58" font-size="11" font-weight="700" fill="#555" font-family="sans-serif">Probability of each possible next word:</text>
<!-- Bar 1: New Delhi 94% -->
<rect x="404" y="70" width="256" height="36" rx="5" fill="#1565C0"/>
<text x="418" y="91" font-size="12" font-weight="600" fill="#fff" font-family="sans-serif">New Delhi</text>
<text x="652" y="91" text-anchor="end" font-size="12" font-weight="700" fill="#fff" font-family="sans-serif">94%</text>
<!-- Bar 2: Mumbai 3% -->
<rect x="404" y="116" width="180" height="32" rx="5" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="418" y="136" font-size="11" fill="#333" font-family="sans-serif">Mumbai</text>
<text x="576" y="136" text-anchor="end" font-size="11" font-weight="600" fill="#1565C0" font-family="sans-serif">3%</text>
<!-- Bar 3: Kolkata 2% -->
<rect x="404" y="158" width="160" height="32" rx="5" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="418" y="178" font-size="11" fill="#333" font-family="sans-serif">Kolkata</text>
<text x="556" y="178" text-anchor="end" font-size="11" font-weight="600" fill="#1565C0" font-family="sans-serif">2%</text>
<!-- Bar 4: Other 1% -->
<rect x="404" y="200" width="140" height="32" rx="5" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="418" y="220" font-size="11" fill="#333" font-family="sans-serif">Other</text>
<text x="536" y="220" text-anchor="end" font-size="11" font-weight="600" fill="#1565C0" font-family="sans-serif">1%</text>
<!-- Caption -->
<text x="340" y="264" text-anchor="middle" font-size="11" fill="#777" font-family="sans-serif">This happens for every single token in the response —</text>
<text x="340" y="280" text-anchor="middle" font-size="11" fill="#777" font-family="sans-serif">hundreds of times per reply.</text>
</svg></div>

---

## The "Large" in Large Language Model

GPT-3 — the model behind early ChatGPT — has **175 billion parameters**. Each parameter is a numerical value tuned during training to capture patterns in language. Think of each parameter as a tiny dial. Training adjusts all 175 billion dials simultaneously — billions of times — until the model becomes very good at predicting what comes next.

**Why does size matter?**  
Larger models develop what researchers call *emergent abilities* — capabilities that smaller models simply do not have. The ability to reason through multi-step problems, write working code, explain complex concepts — these appeared at scale, not by design.

Importantly, the industry has also learned that *efficiency matters as much as size*. More recent models are not necessarily bigger — they are smarter about how they use their parameters. The exact architecture of GPT-4, Claude, and Gemini is not publicly disclosed, but the trend is clear: better results with leaner, more efficient designs.

<div class="img-center"><svg width="680" viewBox="0 0 640 160" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>LLM scale growth from GPT-2 in 2019 to the efficient era from 2024</title>
<defs><marker id="tl" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#ccc" stroke-width="1.5"/></marker></defs>
<rect x="0" y="0" width="640" height="160" rx="6" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="320" y="22" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">LLM SCALE GROWTH — bubble size = relative parameters</text>
<!-- Timeline axis at y=90 giving room above for labels and below for sublabels -->
<line x1="40" y1="90" x2="608" y2="90" stroke="#ccc" stroke-width="1.5"/>
<line x1="600" y1="90" x2="614" y2="90" stroke="#ccc" stroke-width="1.5" marker-end="url(#tl)"/>
<!-- GPT-2: r=5, label above, sublabel below -->
<text x="80"  y="44" text-anchor="middle" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">GPT-2</text>
<circle cx="80"  cy="90" r="5"  fill="#FF8C00"/>
<text x="80"  y="114" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">1.5B · 2019</text>
<!-- GPT-3: r=9 -->
<text x="190" y="38" text-anchor="middle" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">GPT-3</text>
<circle cx="190" cy="90" r="9"  fill="#FF8C00"/>
<text x="190" y="114" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">175B · 2020</text>
<!-- PaLM: r=13 — label y adjusted to clear bubble top (90-13=77, so label at y=60) -->
<text x="310" y="54" text-anchor="middle" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">PaLM</text>
<circle cx="310" cy="90" r="13" fill="#1565C0"/>
<text x="310" y="118" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">540B · 2022</text>
<!-- GPT-4: r=17 — label y must clear bubble top (90-17=73, label at y=50) -->
<text x="430" y="46" text-anchor="middle" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">GPT-4</text>
<circle cx="430" cy="90" r="17" fill="#1565C0"/>
<text x="430" y="122" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">~1T+ · 2023</text>
<!-- Efficient era: r=11 -->
<text x="555" y="50" text-anchor="middle" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">Efficient era</text>
<circle cx="555" cy="90" r="11" fill="#0d47a1"/>
<text x="555" y="116" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Smaller + smarter · 2024–</text>
</svg></div>

---

## How does a conversation with ChatGPT actually work?

When you type a message, the model does not "think" the way you do. It runs through the same five mechanical steps — hundreds of times — to build your response one word at a time.

<div class="img-center"><svg width="680" viewBox="0 0 680 160" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>5-step process ChatGPT uses to generate a response</title>
<defs><marker id="c1" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<!-- Step 1 -->
<rect x="10" y="20" width="112" height="72" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="66" y="46" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">1. Tokenise</text>
<text x="66" y="63" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">split text into</text>
<text x="66" y="79" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">chunks</text>
<line x1="122" y1="56" x2="138" y2="56" stroke="#1565C0" stroke-width="1.5" marker-end="url(#c1)"/>
<!-- Step 2 -->
<rect x="138" y="20" width="112" height="72" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="194" y="46" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">2. Context</text>
<text x="194" y="63" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">load the full</text>
<text x="194" y="79" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">conversation</text>
<line x1="250" y1="56" x2="266" y2="56" stroke="#1565C0" stroke-width="1.5" marker-end="url(#c1)"/>
<!-- Step 3 -->
<rect x="266" y="20" width="120" height="72" rx="7" fill="#1565C0" stroke="#0d47a1" stroke-width="1"/>
<text x="326" y="46" text-anchor="middle" font-size="11" font-weight="700" fill="#fff" font-family="sans-serif">3. Probabilities</text>
<text x="326" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">score all possible</text>
<text x="326" y="79" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">tokens</text>
<line x1="386" y1="56" x2="402" y2="56" stroke="#1565C0" stroke-width="1.5" marker-end="url(#c1)"/>
<!-- Step 4 -->
<rect x="402" y="20" width="112" height="72" rx="7" fill="#1565C0" stroke="#0d47a1" stroke-width="1"/>
<text x="458" y="46" text-anchor="middle" font-size="11" font-weight="700" fill="#fff" font-family="sans-serif">4. Sample</text>
<text x="458" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">pick from</text>
<text x="458" y="79" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">top options</text>
<line x1="514" y1="56" x2="530" y2="56" stroke="#1565C0" stroke-width="1.5" marker-end="url(#c1)"/>
<!-- Step 5 -->
<rect x="530" y="20" width="140" height="72" rx="7" fill="#FF8C00" stroke="#e65c00" stroke-width="1"/>
<text x="600" y="46" text-anchor="middle" font-size="11" font-weight="700" fill="#fff" font-family="sans-serif">5. Repeat</text>
<text x="600" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">until response</text>
<text x="600" y="79" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">is complete</text>
<!-- Loop arrow from step 5 back to step 3 -->
<path d="M600 92 L600 120 L326 120 L326 92" fill="none" stroke="#999" stroke-width="1" stroke-dasharray="4 3" marker-end="url(#c1)"/>
<text x="463" y="140" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">loops back to step 3 for every new token</text>
</svg></div>

**Step 1 — Tokenisation:** Your text is broken into tokens (chunks of text — roughly words or parts of words). "Generative AI" becomes two tokens. "Chandrashaker" might become three or four.

**Step 2 — Context window:** The model reads all the tokens in your conversation as one long sequence. Modern models like GPT-4 support up to 128,000 tokens — enough for a full novel.

**Step 3 — Probability calculation:** For every possible next token (~50,000 options), the model assigns a probability score.

**Step 4 — Sampling:** Rather than always picking the top-probability token (which would feel robotic and repetitive), the model samples from the top options — introducing natural variation. This is why the same question asked twice gives slightly different answers.

**Step 5 — Repeat:** Steps 3 and 4 repeat for every token in the response until the model decides to stop. A 200-word reply involves hundreds of these cycles.

This is why responses stream word by word — the model is generating your reply one token at a time, in real time.

---

## What Generative AI is NOT

Three misconceptions cause the most problems — either leading to over-trust or unnecessary dismissal of AI tools.

<div class="img-center"><svg width="680" viewBox="0 0 680 230" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Three common misconceptions about Generative AI</title>
<!-- Card 1: No internet -->
<rect x="10" y="10" width="206" height="210" rx="8" fill="#fff3f3" stroke="#ef9a9a" stroke-width="1"/>
<rect x="10" y="10" width="206" height="44" rx="8" fill="#c62828"/>
<rect x="10" y="42" width="206" height="12" fill="#c62828"/>
<text x="113" y="36" text-anchor="middle" font-size="12" font-weight="700" fill="#fff" font-family="sans-serif">No internet (by default)</text>
<line x1="28" y1="66" x2="198" y2="66" stroke="#ef9a9a" stroke-width="0.5"/>
<text x="113" y="86"  text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Answers from training</text>
<text x="113" y="103" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">data, not live search.</text>
<text x="113" y="122" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">This is why it can</text>
<text x="113" y="139" text-anchor="middle" font-size="11" fill="#c62828" font-weight="600" font-family="sans-serif">hallucinate</text>
<text x="113" y="156" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">— state false facts</text>
<text x="113" y="173" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">confidently.</text>
<text x="113" y="196" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Exception: ChatGPT browse,</text>
<text x="113" y="211" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Perplexity, Gemini search</text>
<!-- Card 2: No understanding -->
<rect x="236" y="10" width="206" height="210" rx="8" fill="#fff8e1" stroke="#ffe082" stroke-width="1"/>
<rect x="236" y="10" width="206" height="44" rx="8" fill="#f57f17"/>
<rect x="236" y="42" width="206" height="12" fill="#f57f17"/>
<text x="339" y="29" text-anchor="middle" font-size="12" font-weight="700" fill="#fff" font-family="sans-serif">No true</text>
<text x="339" y="46" text-anchor="middle" font-size="12" font-weight="700" fill="#fff" font-family="sans-serif">understanding</text>
<line x1="254" y1="66" x2="424" y2="66" stroke="#ffe082" stroke-width="0.5"/>
<text x="339" y="86"  text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Sophisticated pattern</text>
<text x="339" y="103" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">matching — not human</text>
<text x="339" y="120" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">comprehension.</text>
<text x="339" y="145" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Outputs often seem</text>
<text x="339" y="162" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">intelligent, yet can fail</text>
<text x="339" y="179" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">on genuinely novel</text>
<text x="339" y="196" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">problems.</text>
<!-- Card 3: No memory -->
<rect x="462" y="10" width="206" height="210" rx="8" fill="#e8f0fe" stroke="#90caf9" stroke-width="1"/>
<rect x="462" y="10" width="206" height="44" rx="8" fill="#1565C0"/>
<rect x="462" y="42" width="206" height="12" fill="#1565C0"/>
<text x="565" y="29" text-anchor="middle" font-size="12" font-weight="700" fill="#fff" font-family="sans-serif">No memory</text>
<text x="565" y="46" text-anchor="middle" font-size="12" font-weight="700" fill="#fff" font-family="sans-serif">between chats</text>
<line x1="480" y1="66" x2="650" y2="66" stroke="#90caf9" stroke-width="0.5"/>
<text x="565" y="86"  text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Each new conversation</text>
<text x="565" y="103" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">starts from zero.</text>
<text x="565" y="128" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Within a chat it</text>
<text x="565" y="145" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">remembers everything</text>
<text x="565" y="162" text-anchor="middle" font-size="11" fill="#1565C0" font-weight="600" font-family="sans-serif">(the context window).</text>
<text x="565" y="187" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Close the tab —</text>
<text x="565" y="204" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">it is back to zero.</text>
</svg></div>

**It does not search the internet by default.** An LLM answers from what it learned during training, not from a live search. This is why it can *hallucinate* — confidently state something false. Always verify important factual claims independently.

*Exception: ChatGPT with browsing enabled, Perplexity, and Gemini with live search can fetch real-time information. But the base model cannot.*

**It does not understand in the human sense.** The model does sophisticated pattern matching. This matters less than you might think in practice — outputs are often indistinguishable from genuine understanding — but it explains why AI can fail in surprising ways on genuinely novel problems.

**It has no memory between conversations.** Each new chat starts fresh. Within a conversation it remembers everything (the context window). Close the tab — it is back to zero.

---

## Why Indian students and freshers need to understand this NOW

AI/ML hiring on Naukri grew 45% across FY26 — the fastest-growing job category in Indian tech, while overall IT hiring remained flat. Naukri currently lists over 77,000 active AI job vacancies, and that number keeps climbing.

<div class="img-center"><div style="max-width:680px;width:100%">
<div style="background:#f9f9f9;border:1px solid #e0e0e0;border-radius:6px;padding:16px;margin:20px 0">
<div style="display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:10px;margin-bottom:16px;text-align:center">
  <div style="background:#fff;border:1px solid #e0e0e0;border-radius:6px;padding:10px"><div style="font-size:22px;font-weight:700;color:#1565C0">+45%</div><div style="font-size:11px;color:#777;margin-top:3px">AI/ML hiring growth FY26</div></div>
  <div style="background:#fff;border:1px solid #e0e0e0;border-radius:6px;padding:10px"><div style="font-size:22px;font-weight:700;color:#888">Flat</div><div style="font-size:11px;color:#777;margin-top:3px">Overall IT sector growth</div></div>
  <div style="background:#fff;border:1px solid #e0e0e0;border-radius:6px;padding:10px"><div style="font-size:22px;font-weight:700;color:#1565C0">77K+</div><div style="font-size:11px;color:#777;margin-top:3px">Active AI vacancies on Naukri</div></div>
  <div style="background:#fff;border:1px solid #e0e0e0;border-radius:6px;padding:10px"><div style="font-size:22px;font-weight:700;color:#FF8C00">+53%</div><div style="font-size:11px;color:#777;margin-top:3px">AI salary premium</div></div>
</div>
<canvas id="hiringChart" height="180" aria-label="Bar chart comparing AI/ML hiring growth versus overall IT sector growth across FY26"></canvas>
<div style="font-size:10px;color:#aaa;margin-top:10px;text-align:right">Sources: Naukri JobSpeak March 2026 · Naukri AI Jobs Report 2025 · CBRE India Dec 2025</div>
</div>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
(function(){
  var ctx = document.getElementById('hiringChart');
  if(!ctx) return;
  new Chart(ctx, {
    type: 'bar',
    data: {
      labels: ['Q1 FY26', 'Feb 2026 (MNCs)', 'Mar 2026', 'Full Year FY26'],
      datasets: [
        { label: 'AI/ML hiring YoY %', data: [38,82,37,45], backgroundColor: '#1565C0', borderRadius: 4 },
        { label: 'Overall IT YoY %',   data: [8,12,9,8],    backgroundColor: '#e0e0e0', borderRadius: 4 }
      ]
    },
    options: {
      responsive: true,
      plugins: {
        legend: { position: 'top', labels: { font: { size: 11 } } }
      },
      scales: {
        x: { grid: { display: false }, ticks: { font: { size: 11 } } },
        y: { ticks: { callback: function(v){ return v+'%'; }, font: { size: 11 } }, grid: { color: 'rgba(0,0,0,0.06)' } }
      }
    }
  });
})();
</script>
</div></div>

But here is what many people miss — the majority of those roles are not asking for people to *build* AI. They are asking for people who can *work with* AI effectively.

Infosys alone is running over 4,600 active AI projects, has generated over 28 million lines of code using AI tools, and built more than 500 AI agents — deployed with 90% of its 200 largest clients. TCS, Wipro, and HCL are following the same path.

Developers who can write effective prompts, use AI coding tools, and understand what AI can and cannot do are being fast-tracked. Those who cannot are being left behind — regardless of years of experience.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 1.1</div>
  <ol>
    <li><strong>LLMs predict the next word</strong> — at massive scale, across massive training data, this produces remarkably capable outputs.</li>
    <li><strong>They can hallucinate</strong> — because they are pattern-matching, not fact-checking. Always verify important claims.</li>
    <li><strong>Context is everything</strong> — the more relevant context you give the model in your prompt, the better its output. This is the entire foundation of prompt engineering, which you will learn in Unit 2.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-11">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 1.1 — Identify 5 GenAI Tools in Your Environment</h3>
  </div>
  <p>No technical work required — this is a reflection exercise.</p>
  <ol>
    <li>List 5 AI tools you have used or have access to. Examples: ChatGPT, GitHub Copilot, Gemini in Google Workspace, Claude, Notion AI, Grammarly, Bing Chat.</li>
    <li>For each tool, write two sentences:
      <ul>
        <li>What task you used it for (or what task it is designed for)</li>
        <li>One observation about output quality — what it did well or where it fell short</li>
      </ul>
    </li>
    <li>Save your list. You will revisit it at the end of the course to see how your perspective has changed.</li>
  </ol>
  <p>There are no wrong answers. The goal is awareness — knowing what AI tools are already in your environment is the first step to using them strategically.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/">&#8592; Course Home</a>
  <a class="mod-nav-next" href="/courses/genai/unit1/module-1-2-chatgpt-vs-claude-vs-gemini/">Module 1.2: ChatGPT vs Claude vs Gemini &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Image credits and licences</summary>
  <table>
    <thead><tr><th>Visual</th><th>Type</th><th>Licence</th><th>Attribution</th></tr></thead>
    <tbody>
      <tr><td>Discriminative vs Generative</td><td>Inline SVG — original</td><td>CC0</td><td>No</td></tr>
      <tr><td>LLM next-token prediction</td><td>Inline SVG — original</td><td>CC0</td><td>No</td></tr>
      <tr><td>LLM scale timeline</td><td>Inline SVG — original</td><td>CC0</td><td>No</td></tr>
      <tr><td>5-step conversation flow</td><td>Inline SVG — original</td><td>CC0</td><td>No</td></tr>
      <tr><td>Misconceptions panel</td><td>Inline SVG — original</td><td>CC0</td><td>No</td></tr>
      <tr><td>India hiring chart</td><td>Inline Chart.js — original</td><td>CC0 (Naukri data)</td><td>Cite Naukri as data source</td></tr>
    </tbody>
  </table>
</div>
</details>
</div>
