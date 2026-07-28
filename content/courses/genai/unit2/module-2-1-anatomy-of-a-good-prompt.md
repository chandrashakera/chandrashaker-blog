---
title: "Module 2.1: Anatomy of a Good Prompt"
description: "Learn the six components of a well-structured prompt and why most AI prompts fail — practical prompt engineering for Indian students and IT professionals using ChatGPT, Claude, and Gemini."
weight: 1
sidebar: false
mainroad_aside: false
tags: ["prompt-engineering", "chatgpt", "claude", "gemini", "india", "generative-ai", "beginners"]
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
.mod-remember li{font-size:14px;color:#1a1a1a;line-height:1.7;margin-bottom:4px}
/* ── Prompt comparison boxes ─────────────────────────────────── */
.mod-prompt-pair{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-prompt-box{border-radius:8px;overflow:hidden;border:1px solid}
.mod-prompt-label{padding:8px 14px;font-size:11px;font-weight:700;letter-spacing:0.06em}
.mod-prompt-text{padding:12px 14px;font-size:13px;line-height:1.7;font-family:monospace,sans-serif;white-space:pre-wrap;word-break:break-word}
.mod-prompt-bad .mod-prompt-label{background:#ffeaea;color:#c62828;border-bottom:1px solid #ef9a9a}
.mod-prompt-bad .mod-prompt-text{background:#fff8f8;color:#444}
.mod-prompt-bad{border-color:#ef9a9a}
.mod-prompt-good .mod-prompt-label{background:#e8f5e9;color:#2e7d32;border-bottom:1px solid #a5d6a7}
.mod-prompt-good .mod-prompt-text{background:#f9fff9;color:#333}
.mod-prompt-good{border-color:#a5d6a7}
/* ── Component cards ─────────────────────────────────────────── */
.mod-component-list{display:flex;flex-direction:column;gap:10px;margin:20px 0}
.mod-component{display:flex;gap:14px;background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;align-items:flex-start}
.mod-component-badge{width:32px;height:32px;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:700;color:#fff;flex-shrink:0;margin-top:1px}
.mod-component-body{flex:1}
.mod-component-title{font-size:14px;font-weight:700;color:#1a1a1a;margin:0 0 4px}
.mod-component-desc{font-size:13px;color:#555;line-height:1.6;margin:0 0 6px}
.mod-component-example{background:#f5f5f4;border-radius:4px;padding:8px 10px;font-size:12px;font-family:monospace,sans-serif;color:#333;line-height:1.5;white-space:pre-wrap;border-left:3px solid}
.mod-component-tag{font-size:10px;font-weight:700;padding:2px 7px;border-radius:10px;margin-left:8px;vertical-align:middle}
/* ── Before/after full prompt ────────────────────────────────── */
.mod-before-after{margin:20px 0}
.mod-ba-label{font-size:11px;font-weight:700;letter-spacing:0.06em;padding:8px 14px;border-radius:6px 6px 0 0}
.mod-ba-text{font-size:13px;font-family:monospace,sans-serif;line-height:1.8;padding:14px 16px;border-radius:0 0 6px 6px;white-space:pre-wrap;word-break:break-word;border:1px solid;border-top:none}
.mod-ba-annotation{display:flex;align-items:flex-start;gap:6px;padding:4px 16px;font-size:12px;color:#555;border-left:1px solid;border-right:1px solid}
.mod-ba-annotation:last-of-type{border-bottom:1px solid;border-radius:0 0 6px 6px;padding-bottom:10px}
/* ── Improvement table ───────────────────────────────────────── */
.mod-table-wrap{overflow-x:auto;margin:20px 0}
.mod-table{width:100%;border-collapse:collapse;font-size:13px}
.mod-table th{background:#1565C0;color:#fff;padding:10px 13px;text-align:left;font-weight:600;font-size:12px}
.mod-table td{padding:10px 13px;border-bottom:1px solid #f0f0f0;color:#333;vertical-align:top;line-height:1.5}
.mod-table tr:last-child td{border-bottom:none}
.mod-table tr:nth-child(even) td{background:#fafafa}
.mod-table td:first-child{font-weight:600;color:#1565C0;white-space:nowrap}
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
.mod-wrap p,.mod-wrap li,.mod-wrap td{font-size:15px;color:#222;line-height:1.8}
.mod-wrap h2{font-size:20px;color:#111;margin-top:32px;margin-bottom:12px}
.mod-wrap h3{font-size:17px;color:#111;margin-top:24px;margin-bottom:8px}
.mod-wrap strong{color:#111;font-weight:600}
.mod-wrap em{color:#333}
.mod-wrap code{font-size:14px;background:#f0f0f0;padding:2px 6px;border-radius:3px;color:#c62828}
.mod-credits{font-size:12px;color:#888;margin-top:32px;padding-top:12px;border-top:1px solid #e0e0e0}
.mod-credits summary{cursor:pointer;font-size:12px;color:#aaa;list-style:none}
.mod-credits summary:hover{color:#888}
.img-center{display:flex;justify-content:center;margin:20px 0}
.img-center svg{max-width:100%;height:auto}
.img-center>div{max-width:680px;width:100%}
@media(max-width:520px){.mod-prompt-pair{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:20%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">4 of 20 modules complete</div>
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
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 2 &nbsp;›&nbsp; MODULE 1 OF 4</span>
    <h1 class="mod-title-inline">Anatomy of a Good Prompt</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Hands-on examples</span>
  </div>
</div>

Welcome to Unit 2. In Unit 1 you built a mental model of what GenAI is and where it fails. Now you start using it effectively.

This module teaches the single most important practical skill in this course: how to write a prompt that actually gets what you want. Most people who are disappointed with AI outputs are not using a bad tool — they are writing bad prompts. The model is only as good as the instructions you give it.

By the end of this module you will be able to break any task down into a structured prompt that produces consistent, high-quality output from any tool.

---

## Why most prompts fail

Before learning what makes a good prompt, look at what makes a bad one.

<div class="mod-prompt-pair">
  <div class="mod-prompt-box mod-prompt-bad">
    <div class="mod-prompt-label">✗ WHAT MOST PEOPLE TYPE</div>
    <div class="mod-prompt-text">write a report on machine learning</div>
  </div>
  <div class="mod-prompt-box mod-prompt-good">
    <div class="mod-prompt-label">✓ WHAT ACTUALLY WORKS</div>
    <div class="mod-prompt-text">You are a technical writer creating study material for final-year BTech students in India.

Write a 400-word overview of supervised machine learning. Cover: what it is, how training works, and 2 real-world applications relevant to Indian industry (e.g. banking fraud detection, crop yield prediction).

Use simple language. No jargon without explanation. End with 3 bullet points summarising the key ideas.</div>
  </div>
</div>

The bad prompt is not wrong — it is just empty. The model has no idea who you are, what level of detail you need, what format you want, or what context matters. So it produces a generic, mediocre response.

The good prompt gives the model everything it needs to produce exactly what you want on the first try.

<div class="mod-keypoint">
<strong>The core principle:</strong> A prompt is a specification, not a question. The more precisely you define the output, the better the output will be. In 2026, prompt engineering is not about writing longer prompts — it is about writing <em>clearer specs</em>.
</div>

---

## The six components of a well-structured prompt

Every effective prompt is built from some combination of these six components. You do not need all six every time — but knowing each one lets you diagnose why a prompt is failing and fix it.

<div class="mod-component-list">

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#1565C0">1</div>
    <div class="mod-component-body">
      <div class="mod-component-title">Role &nbsp;<span class="mod-component-tag" style="background:#e3f2fd;color:#1565C0;border:1px solid #90caf9">optional but powerful</span></div>
      <div class="mod-component-desc">Tell the model who it is. This sets the tone, vocabulary, and depth of the response. A response from "a senior software engineer" will read very differently from "a patient teacher explaining to a beginner."</div>
      <div class="mod-component-example" style="border-color:#1565C0">"You are a senior Python developer reviewing code for a fintech startup."
"You are a placement counsellor at an Indian engineering college."
"You are a concise technical writer who avoids jargon."</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#FF8C00">2</div>
    <div class="mod-component-body">
      <div class="mod-component-title">Task &nbsp;<span class="mod-component-tag" style="background:#fff8e1;color:#e65c00;border:1px solid #FFB300">required</span></div>
      <div class="mod-component-desc">The clear, specific instruction — what you want the model to do. Use action verbs: write, summarise, explain, compare, list, debug, translate, review. Vague tasks produce vague outputs.</div>
      <div class="mod-component-example" style="border-color:#FF8C00">✗  "tell me about neural networks"
✓  "Explain how a neural network learns, step by step, using a simple analogy"
✓  "Summarise this job description in 3 bullet points highlighting required skills"</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#2e7d32">3</div>
    <div class="mod-component-body">
      <div class="mod-component-title">Context &nbsp;<span class="mod-component-tag" style="background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7">highly recommended</span></div>
      <div class="mod-component-desc">Background information the model needs to give you a relevant answer. Without context, the model guesses your situation. With context, it can tailor the response precisely to your needs.</div>
      <div class="mod-component-example" style="border-color:#2e7d32">"I am a 3rd-year ECE student applying for a software internship at Infosys."
"This code is part of a Django REST API serving 10,000 users per day."
"The audience is non-technical HR managers at Indian manufacturing companies."</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#6a1b9a">4</div>
    <div class="mod-component-body">
      <div class="mod-component-title">Format &nbsp;<span class="mod-component-tag" style="background:#f3e5f5;color:#6a1b9a;border:1px solid #ce93d8">recommended</span></div>
      <div class="mod-component-desc">Specify how you want the output structured. Without this, the model picks a format — which may not suit your use case. This is one of the fastest ways to improve prompt output quality.</div>
      <div class="mod-component-example" style="border-color:#6a1b9a">"Respond in bullet points, maximum 5 points."
"Format as a table with columns: Tool | Best for | Free tier | India pricing"
"Write in plain paragraphs. No bullet points. Under 300 words."
"Output only the corrected code. No explanation."</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#00838f">5</div>
    <div class="mod-component-body">
      <div class="mod-component-title">Examples &nbsp;<span class="mod-component-tag" style="background:#e0f7fa;color:#006064;border:1px solid #80deea">optional but high-impact</span></div>
      <div class="mod-component-desc">Show the model what a good output looks like. This is called few-shot prompting (covered in Module 2.2) and is one of the highest-ROI prompt techniques available. Even one example dramatically improves output consistency.</div>
      <div class="mod-component-example" style="border-color:#00838f">"Here is an example of the tone I want:
Example: 'Pandas makes data manipulation intuitive — think of it as Excel, but scriptable.'
Now explain NumPy in the same style."</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#c62828">6</div>
    <div class="mod-component-body">
      <div class="mod-component-title">Constraints &nbsp;<span class="mod-component-tag" style="background:#ffeaea;color:#c62828;border:1px solid #ef9a9a">optional</span></div>
      <div class="mod-component-desc">Boundaries and exclusions — what to avoid, length limits, what not to include. Constraints are how you prevent the model from going off in a direction you do not want. In 2026, writing clear constraints is as important as writing clear instructions.</div>
      <div class="mod-component-example" style="border-color:#c62828">"Do not use technical jargon."
"Keep the response under 150 words."
"Do not suggest paid tools — only free options."
"Do not repeat points already covered in the introduction."</div>
    </div>
  </div>

</div>

---

## Seeing all six in action

Here is the same task — asking for help preparing for a job interview — written as a weak prompt, then rebuilt using all six components.

<div class="mod-before-after">
  <div class="mod-ba-label" style="background:#ffeaea;color:#c62828">✗ WEAK PROMPT</div>
  <div class="mod-ba-text" style="background:#fff8f8;color:#444;border-color:#ef9a9a">help me prepare for a TCS interview</div>
</div>

What is wrong with this? The model does not know your background, the role you are applying for, what stage of interview preparation you are at, how much time you have, or what format of help you want. The output will be a generic list that could apply to anyone applying anywhere.

<div class="mod-before-after" style="margin-top:20px">
  <div class="mod-ba-label" style="background:#e8f5e9;color:#2e7d32">✓ STRUCTURED PROMPT — all 6 components</div>
  <div class="mod-ba-text" style="background:#f9fff9;color:#333;border-color:#a5d6a7">You are an experienced placement mentor at a top Indian engineering college. [ROLE]

I have a TCS NQT technical interview in 5 days. [CONTEXT]
I am a final-year CSE student. I am comfortable with Python and data structures but weak on DBMS and OS concepts.

Create a 5-day preparation plan. [TASK]

Format it as a day-by-day table: Day | Topics | Resources (free only) | Practice tasks. [FORMAT]

Keep each day's plan achievable in 3 hours. [CONSTRAINT]
Do not include topics like networking or compiler design — those are not in TCS NQT scope. [CONSTRAINT]</div>
</div>

The second prompt will produce a personalised, structured, immediately usable preparation plan — not a generic bullet list. The difference in output quality will be dramatic, and it took about 60 seconds longer to write.

---

## The most common prompt mistakes — and how to fix them

<div class="mod-table-wrap">
<table class="mod-table">
<thead>
  <tr><th>Mistake</th><th>What happens</th><th>Fix</th></tr>
</thead>
<tbody>
  <tr>
    <td>No task verb</td>
    <td>"Machine learning in healthcare" — the model does not know if you want a summary, a tutorial, a list of companies, or an essay</td>
    <td>Always start with an action verb: explain, write, list, compare, debug, summarise, translate</td>
  </tr>
  <tr>
    <td>No audience specified</td>
    <td>The model defaults to a generic educated adult — too advanced for beginners, too basic for experts</td>
    <td>Add "for a [role/level]" — "for a 2nd-year BTech student" or "for a non-technical manager"</td>
  </tr>
  <tr>
    <td>No format requested</td>
    <td>The model picks a format — often long flowing paragraphs when you wanted bullet points, or vice versa</td>
    <td>Add explicit format: "respond in a table", "use bullet points", "write in plain paragraphs under 200 words"</td>
  </tr>
  <tr>
    <td>Asking multiple questions at once</td>
    <td>"Explain ML, list Python libraries, and tell me how to get a job in AI" — the model rushes all three and does none well</td>
    <td>One task per prompt. Break multi-part work into sequential prompts in the same conversation</td>
  </tr>
  <tr>
    <td>No context about purpose</td>
    <td>"Write an email about the project delay" — the model invents details: who delayed what, for whom, at what severity level</td>
    <td>Paste in the relevant context: "The email is to my project manager at Wipro. The delay is 3 days due to a dependency on the API team."</td>
  </tr>
  <tr>
    <td>Accepting the first output</td>
    <td>First outputs are often good but not great. Most people stop here and miss 30–40% quality improvement</td>
    <td>Follow up with refinement prompts: "Make it more concise", "Add a specific Indian banking example", "Rewrite the introduction — it is too formal"</td>
  </tr>
</tbody>
</table>
</div>

---

## Tool-specific tips for Indian users

Different tools respond slightly differently to the same prompt structure. Here is what to know:

<div class="mod-keypoint">
<strong>ChatGPT</strong> responds well to numbered instructions and crisp numeric constraints ("3 bullets", "under 50 words"). It infers intent well even from shorter prompts — you can often start with a medium-detail prompt and refine in follow-ups.<br><br>
<strong>Claude</strong> works best with contract-style instructions — explicit goals, clear output format, and tone cues. It tends to over-explain unless you set a length constraint. Add "be concise" or "keep under 300 words" explicitly.<br><br>
<strong>Gemini</strong> prefers shorter, more direct prompts than the other two. Place specific questions at the end of your prompt, after any context. Google's own prompt guidelines recommend always including at least one example for complex tasks.
</div>

---

## The prompt improvement loop

Writing a good prompt is rarely a one-shot activity — it is an iterative loop. Here is the workflow that experienced prompt engineers use:

<div class="img-center"><svg width="680" viewBox="0 0 680 120" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Prompt improvement loop: Write a draft prompt, review the output, identify what is missing or wrong, refine the prompt, repeat until satisfied</title>
<defs><marker id="pl" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<rect x="0" y="0" width="680" height="120" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<rect x="16" y="30" width="116" height="56" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="74" y="52" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">1. Write</text>
<text x="74" y="68" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">draft prompt</text>
<text x="74" y="82" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">with 6 components</text>
<line x1="132" y1="58" x2="152" y2="58" stroke="#1565C0" stroke-width="1.5" marker-end="url(#pl)"/>
<rect x="152" y="30" width="116" height="56" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="210" y="52" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">2. Review</text>
<text x="210" y="68" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">read the output</text>
<text x="210" y="82" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">critically</text>
<line x1="268" y1="58" x2="288" y2="58" stroke="#1565C0" stroke-width="1.5" marker-end="url(#pl)"/>
<rect x="288" y="30" width="116" height="56" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="346" y="52" text-anchor="middle" font-size="11" font-weight="700" fill="#FF8C00" font-family="sans-serif">3. Diagnose</text>
<text x="346" y="68" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">what component</text>
<text x="346" y="82" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">is missing?</text>
<line x1="404" y1="58" x2="424" y2="58" stroke="#1565C0" stroke-width="1.5" marker-end="url(#pl)"/>
<rect x="424" y="30" width="116" height="56" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="482" y="52" text-anchor="middle" font-size="11" font-weight="700" fill="#FF8C00" font-family="sans-serif">4. Refine</text>
<text x="482" y="68" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">add or clarify</text>
<text x="482" y="82" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">missing component</text>
<line x1="540" y1="58" x2="560" y2="58" stroke="#1565C0" stroke-width="1.5" marker-end="url(#pl)"/>
<rect x="560" y="30" width="104" height="56" rx="7" fill="#e8f5e9" stroke="#a5d6a7" stroke-width="1"/>
<text x="612" y="52" text-anchor="middle" font-size="11" font-weight="700" fill="#2e7d32" font-family="sans-serif">5. Done?</text>
<text x="612" y="68" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">yes → use output</text>
<text x="612" y="82" text-anchor="middle" font-size="10" fill="#444" font-family="sans-serif">no → back to 3</text>
</svg></div>

Most prompts need 2–3 iterations to reach high quality. This is not a failure — it is the normal workflow. Each iteration teaches you something about what the model needs from you, and over time your first-draft prompts improve because you have internalised what "missing components" look like.

---

## A practical template to start with

Until writing structured prompts feels natural, use this template for any task:

<div class="mod-before-after">
  <div class="mod-ba-label" style="background:#e8f0fe;color:#1565C0">STARTER TEMPLATE — copy and fill in the blanks</div>
  <div class="mod-ba-text" style="background:#f5f8ff;color:#333;border-color:#90caf9">You are a [ROLE].

I need you to [TASK — action verb + what].

Context: [WHO YOU ARE + WHAT THIS IS FOR].

Format: [HOW YOU WANT THE OUTPUT].

Constraints: [WHAT TO AVOID OR LIMIT].

[Optional: Here is an example of the style/format I want: ...]</div>
</div>

You will not need this template forever — after 20–30 prompts, structuring this way becomes instinctive. But use it consciously for the next week and your output quality will improve immediately.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 2.1</div>
  <ol>
    <li><strong>A prompt is a specification, not a question</strong> — the more precisely you define role, task, context, format, examples, and constraints, the better the output. Vague prompts produce vague results.</li>
    <li><strong>The six components are your diagnostic toolkit</strong> — when a prompt gives a bad output, check which component is missing. Adding the missing piece is almost always faster than rewriting the prompt from scratch.</li>
    <li><strong>Refinement is the workflow, not a fallback</strong> — professional prompt engineers iterate 2–3 times per task. Accepting the first output and blaming the tool is the most common mistake beginners make.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-21">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 2.1 — Rewrite 3 Weak Prompts Using the 6 Components</h3>
  </div>
  <p>This is the core skill-building exercise for Unit 2. Each rewrite should take 5–10 minutes.</p>
  <ol>
    <li><strong>Take these three weak prompts</strong> and rewrite each one using the six-component structure:
      <ul>
        <li><code>explain data structures</code></li>
        <li><code>write a LinkedIn post about my project</code></li>
        <li><code>how do I get a job in AI</code></li>
      </ul>
    </li>
    <li><strong>For each rewrite</strong>, explicitly label which components you used — Role, Task, Context, Format, Examples, Constraints. Not all six are required, but you should consciously choose which ones to include and why.</li>
    <li><strong>Test your rewritten prompts</strong> in ChatGPT, Claude, or Gemini (free tier). Compare the output quality to what the weak prompt would produce.</li>
    <li><strong>Add your rewrites to your AI Learning Journal</strong> (started in Assignment 1.4). Note which components made the biggest difference to the output quality.</li>
  </ol>
  <p>There are no perfect answers — the goal is to practise conscious prompt construction. You will use these same techniques throughout Units 2, 3, and 4.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit1/module-1-4-risks-and-responsible-use/">&#8592; Module 1.4: Risks and Responsible Use</a>
  <a class="mod-nav-next" href="/courses/genai/unit2/module-2-2-zero-shot-few-shot-cot/">Module 2.2: Zero-shot, Few-shot and CoT &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>Six prompt components framework</td><td>Lakera Prompt Engineering Guide 2026; promptbuilder.cc 2026</td></tr>
      <tr><td>"Prompt engineering is writing clearer specs" (2026 framing)</td><td>promptbuilder.cc Prompt Engineering Best Practices 2026</td></tr>
      <tr><td>ChatGPT crisp numeric constraints; Claude over-explains without constraints; Gemini prefers shorter direct prompts</td><td>Lakera Prompt Engineering Guide 2026; Thomas Wiegold blog February 2026</td></tr>
      <tr><td>Few-shot remains one of highest-ROI techniques; try zero-shot before few-shot</td><td>Thomas Wiegold Prompt Engineering Best Practices 2026</td></tr>
      <tr><td>Google recommends placing specific questions after context; few-shot preferred over zero-shot for Gemini</td><td>Google Gemini prompt engineering whitepaper, cited in Thomas Wiegold 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
