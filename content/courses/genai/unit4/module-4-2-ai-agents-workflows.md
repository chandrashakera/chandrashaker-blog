---
title: "Module 4.2: AI Agents and Automation Workflows"
description: "Understand how AI agents work, how they differ from chatbots, where they are being deployed in Indian IT, and how to work alongside them — explained simply for students and freshers."
weight: 2
sidebar: false
mainroad_aside: false
tags: ["ai-agents", "agentic-ai", "automation", "workflows", "india", "generative-ai", "advanced"]
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
.mod-warning{background:#ffeaea;border-left:4px solid #c62828;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a0000;line-height:1.6}
.mod-warning strong{color:#c62828}
.mod-remember{background:#e8f0fe;border-left:4px solid #1565C0;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0}
.mod-remember-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.06em;margin-bottom:8px}
.mod-remember ol{margin:0;padding-left:18px}
.mod-remember li{font-size:14px;color:#111111;line-height:1.7;margin-bottom:4px}
/* ── Stat grid ───────────────────────────────────────────────── */
.mod-stat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:20px 0}
.mod-stat-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;text-align:center}
.mod-stat-card-num{font-size:24px;font-weight:700;color:#1565C0;margin-bottom:4px}
.mod-stat-card-label{font-size:12px;color:#666;line-height:1.4}
/* ── Comparison ──────────────────────────────────────────────── */
.mod-compare{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-compare-card{border-radius:8px;padding:16px;border:1px solid}
.mod-compare-card h3{font-size:14px;font-weight:700;margin:0 0 10px}
.mod-compare-list{margin:0;padding-left:16px}
.mod-compare-list li{font-size:13px;line-height:1.65;margin-bottom:5px;color:#333}
/* ── Component cards ─────────────────────────────────────────── */
.mod-component-list{display:flex;flex-direction:column;gap:10px;margin:20px 0}
.mod-component{display:flex;gap:14px;background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;align-items:flex-start}
.mod-component-badge{width:32px;height:32px;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:700;color:#fff;flex-shrink:0;margin-top:1px}
.mod-component-body{flex:1}
.mod-component-title{font-size:14px;font-weight:700;color:#1a1a1a;margin:0 0 4px}
.mod-component-desc{font-size:13px;color:#555;line-height:1.6;margin:0 0 5px}
.mod-component-example{font-size:12px;font-family:monospace,sans-serif;background:#f5f5f4;border-radius:4px;padding:7px 10px;color:#333;line-height:1.5;border-left:3px solid #1565C0}
/* ── Workflow step-through ───────────────────────────────────── */
.mod-workflow-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0;border-left:4px solid #1565C0}
.mod-workflow-card-header{padding:12px 16px;background:#f5f8ff;border-bottom:1px solid #e0e0e0}
.mod-workflow-card-title{font-size:14px;font-weight:700;color:#1565C0;margin:0}
.mod-workflow-card-sub{font-size:12px;color:#777;margin:2px 0 0}
.mod-workflow-card-body{padding:14px 16px}
.mod-wf-step{display:flex;align-items:flex-start;gap:10px;padding:8px 0;border-bottom:1px solid #f5f5f5}
.mod-wf-step:last-child{border-bottom:none}
.mod-wf-num{width:22px;height:22px;border-radius:50%;background:#1565C0;color:#fff;font-size:11px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px}
.mod-wf-text{font-size:13px;color:#333;line-height:1.5;flex:1}
.mod-wf-tool{display:inline-block;font-size:10px;font-weight:700;padding:1px 7px;border-radius:10px;background:#e3f2fd;color:#1565C0;border:1px solid #90caf9;margin-left:6px;vertical-align:middle}
/* ── Use case grid ───────────────────────────────────────────── */
.mod-usecase-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-uc-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-uc-header{display:flex;align-items:center;gap:8px;margin-bottom:8px}
.mod-uc-icon{font-size:15px;flex-shrink:0}
.mod-uc-title{font-size:13px;font-weight:700;color:#1565C0;margin:0}
.mod-uc-text{font-size:13px;color:#333;line-height:1.6;margin:0 0 5px}
.mod-uc-stat{font-size:11px;font-weight:600;color:#FF8C00}
/* ── Tool table ──────────────────────────────────────────────── */
.mod-table-wrap{overflow-x:auto;margin:20px 0}
.mod-table{width:100%;border-collapse:collapse;font-size:13px}
.mod-table th{background:#1565C0;color:#fff;padding:10px 13px;text-align:left;font-weight:600;font-size:12px}
.mod-table td{padding:10px 13px;border-bottom:1px solid #f0f0f0;color:#111111;vertical-align:top;line-height:1.5}
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
    <div class="mod-progress-fill" style="width:65%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">13 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Understanding GenAI ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-2">Prompt Engineering ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-3">GenAI for Your Job ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-4">Advanced Techniques</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Career & India</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 4 &nbsp;›&nbsp; MODULE 2 OF 4</span>
    <h1 class="mod-title-inline">AI Agents and Automation Workflows</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">No coding required</span>
  </div>
</div>

In Module 4.1 you learned how RAG gives an LLM access to your documents. This module covers the next step: what happens when an LLM does not just answer a question but takes actions — browsing the web, writing and running code, calling APIs, filling forms, and coordinating with other AI systems. That is what AI agents do.

Agentic AI is the fastest-moving area of enterprise AI in 2026. Understanding it at a conceptual level is now a baseline expectation for anyone entering an Indian IT organisation.

---

## The scale of agentic AI adoption

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">40%</div>
    <div class="mod-stat-card-label">of enterprise applications will include task-specific AI agents by 2026, up from less than 5% in 2025 — Gartner</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">57%</div>
    <div class="mod-stat-card-label">of companies already have AI agents running in production — G2 Enterprise AI Agents Report 2025</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">$182B</div>
    <div class="mod-stat-card-label">projected global agentic AI market by 2033, from $7.6B in 2025 — Grand View Research</div>
  </div>
</div>

India's AI journey reached a turning point in 2025. The national conversation has shifted from whether AI will change business to how it can be implemented responsibly and efficiently. About 47% of Indian organisations now operate multiple GenAI use cases, and as AI systems evolve from assistive to agentic, this steady shift reflects how technology is beginning to redefine work, governance, and innovation.

---

## Chatbot vs AI agent — the critical difference

Most people's mental model of AI is a chatbot: you ask a question, it answers. AI agents are fundamentally different.

<div class="mod-compare">
  <div class="mod-compare-card" style="background:#ffeaea;border-color:#ef9a9a">
    <h3 style="color:#c62828">A chatbot (what you already know)</h3>
    <ul class="mod-compare-list">
      <li><strong>Responds</strong> to what you ask — reactive</li>
      <li>One turn: you ask → it answers → done</li>
      <li>Cannot take actions in the world</li>
      <li>Cannot use tools unless explicitly built in</li>
      <li>Forgets everything when the chat ends</li>
      <li>You are always in control of what happens next</li>
    </ul>
  </div>
  <div class="mod-compare-card" style="background:#e8f5e9;border-color:#a5d6a7">
    <h3 style="color:#2e7d32">An AI agent (what this module covers)</h3>
    <ul class="mod-compare-list">
      <li><strong>Acts</strong> toward a goal you define — proactive</li>
      <li>Multi-step loop: plan → act → observe → adapt → repeat</li>
      <li>Can take real actions: browse web, run code, call APIs, send emails</li>
      <li>Uses tools to interact with external systems</li>
      <li>Maintains memory across a task (and sometimes across sessions)</li>
      <li>Operates with varying degrees of autonomy — from supervised to nearly independent</li>
    </ul>
  </div>
</div>

<div class="mod-keypoint">
<strong>The one-line definition:</strong> An AI agent is software that can decide the next step, use tools, and complete tasks toward a defined goal — without human approval at every step. Unlike chatbots, agents operate in a continuous loop of plan, act, observe, and adapt until the task is complete.
</div>

---

## The five core components of an AI agent

Core components of an AI agent are perception, reasoning, memory, planning, and tool-based actions such as web search, code execution, APIs, and file systems. Here is what each means in practice:

<div class="mod-component-list">

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#1565C0">&#128065;</div>
    <div class="mod-component-body">
      <div class="mod-component-title">1. Perception — reading the environment</div>
      <div class="mod-component-desc">The agent takes in information — your instruction, a web page, a document, a database query result, an API response, or the output of the previous step. Perception is what the agent knows before it decides what to do next.</div>
      <div class="mod-component-example">Agent receives: "Find the last 5 support tickets assigned to Team A, summarise the top issue, and send a Slack message to the team lead."</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#FF8C00">&#129504;</div>
    <div class="mod-component-body">
      <div class="mod-component-title">2. Reasoning — deciding what to do next</div>
      <div class="mod-component-desc">The LLM at the core of the agent decides what action to take next based on the goal and the current state. This is the intelligence layer — the agent does not follow a fixed script; it reasons about the best next step.</div>
      <div class="mod-component-example">Agent reasons: "I need to query the support ticket system first. I will use the ServiceNow API. After getting results, I will summarise them. Then I will compose a Slack message."</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#2e7d32">&#128190;</div>
    <div class="mod-component-body">
      <div class="mod-component-title">3. Memory — retaining context across steps</div>
      <div class="mod-component-desc">Agents have both short-term memory (what happened in this task so far) and optionally long-term memory (information persisted across multiple tasks). This is what allows a multi-step task to be coherent — the agent remembers what it already did.</div>
      <div class="mod-component-example">After retrieving 5 tickets, the agent remembers all 5 results while composing the summary — it does not re-query the system for each step.</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#6a1b9a">&#128203;</div>
    <div class="mod-component-body">
      <div class="mod-component-title">4. Planning — breaking goals into steps</div>
      <div class="mod-component-desc">For complex goals, the agent creates a plan — an ordered sequence of sub-tasks. More advanced agents revise this plan mid-task when they discover unexpected information. Planning is what separates a simple tool-call from a genuine multi-step workflow.</div>
      <div class="mod-component-example">Plan: [1] Query ServiceNow API → [2] Parse 5 ticket results → [3] Identify top issue pattern → [4] Draft Slack message → [5] Send via Slack API</div>
    </div>
  </div>

  <div class="mod-component">
    <div class="mod-component-badge" style="background:#c62828">&#128295;</div>
    <div class="mod-component-body">
      <div class="mod-component-title">5. Tool use — taking actions in the world</div>
      <div class="mod-component-desc">Agents are connected to tools — APIs, web browsers, code interpreters, file systems, databases, email clients, Slack, Jira, GitHub, etc. When the agent decides to take an action, it calls the appropriate tool. The tool's output feeds back into the agent's perception for the next step.</div>
      <div class="mod-component-example">Agent calls: ServiceNow API (get tickets) → Python interpreter (parse data) → Slack API (send message). Each tool result is fed back into the agent's context.</div>
    </div>
  </div>

</div>

---

## How the agent loop works — a complete example

<div class="img-center"><svg width="680" viewBox="0 0 680 140" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>AI agent loop: Goal defined, agent plans steps, acts using tools, observes result, adapts plan, repeats until task complete</title>
<defs><marker id="ag" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<rect x="0" y="0" width="680" height="140" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="340" y="20" text-anchor="middle" font-size="11" font-weight="700" fill="#555" font-family="sans-serif">THE AGENT LOOP — PLAN → ACT → OBSERVE → ADAPT → REPEAT</text>
<rect x="14" y="34" width="90" height="52" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="59" y="55" text-anchor="middle" font-size="10" font-weight="700" fill="#1565C0" font-family="sans-serif">1. Goal</text>
<text x="59" y="70" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">User defines</text>
<text x="59" y="82" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">the task</text>
<line x1="104" y1="60" x2="120" y2="60" stroke="#1565C0" stroke-width="1.5" marker-end="url(#ag)"/>
<rect x="120" y="34" width="106" height="52" rx="7" fill="#1565C0" stroke="#0d47a1" stroke-width="1"/>
<text x="173" y="55" text-anchor="middle" font-size="10" font-weight="700" fill="#fff" font-family="sans-serif">2. Plan</text>
<text x="173" y="70" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">LLM breaks goal</text>
<text x="173" y="82" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">into steps</text>
<line x1="226" y1="60" x2="242" y2="60" stroke="#1565C0" stroke-width="1.5" marker-end="url(#ag)"/>
<rect x="242" y="34" width="106" height="52" rx="7" fill="#1565C0" stroke="#0d47a1" stroke-width="1"/>
<text x="295" y="55" text-anchor="middle" font-size="10" font-weight="700" fill="#fff" font-family="sans-serif">3. Act</text>
<text x="295" y="70" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">Call a tool</text>
<text x="295" y="82" text-anchor="middle" font-size="10" fill="rgba(255,255,255,0.9)" font-family="sans-serif">(API, code, web)</text>
<line x1="348" y1="60" x2="364" y2="60" stroke="#1565C0" stroke-width="1.5" marker-end="url(#ag)"/>
<rect x="364" y="34" width="106" height="52" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="417" y="55" text-anchor="middle" font-size="10" font-weight="700" fill="#FF8C00" font-family="sans-serif">4. Observe</text>
<text x="417" y="70" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">Read tool</text>
<text x="417" y="82" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">output / result</text>
<line x1="470" y1="60" x2="486" y2="60" stroke="#1565C0" stroke-width="1.5" marker-end="url(#ag)"/>
<rect x="486" y="34" width="180" height="52" rx="7" fill="#e8f5e9" stroke="#a5d6a7" stroke-width="1"/>
<text x="576" y="55" text-anchor="middle" font-size="10" font-weight="700" fill="#2e7d32" font-family="sans-serif">5. Done or repeat?</text>
<text x="576" y="70" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">Task complete → deliver result</text>
<text x="576" y="82" text-anchor="middle" font-size="10" fill="#333" font-family="sans-serif">Not done → adapt plan → go to 3</text>
<path d="M576 86 L576 120 L295 120 L295 86" fill="none" stroke="#999" stroke-width="1" stroke-dasharray="4 3" marker-end="url(#ag)"/>
<text x="435" y="134" text-anchor="middle" font-size="9" fill="#888" font-family="sans-serif">loop repeats until task complete or human intervention required</text>
</svg></div>

---

## Three real agent workflows — how they work in Indian IT

<div class="mod-workflow-card">
<div class="mod-workflow-card-header">
  <div class="mod-workflow-card-title">Workflow 1 — Bug triage and resolution agent</div>
  <div class="mod-workflow-card-sub">Used at Indian IT delivery teams for Level 1 incident response</div>
</div>
<div class="mod-workflow-card-body">
  <div class="mod-wf-step"><div class="mod-wf-num">1</div><div class="mod-wf-text">New Jira ticket arrives: "Login API returning 500 errors — 23 occurrences in last hour" <span class="mod-wf-tool">Perception</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">2</div><div class="mod-wf-text">Agent queries application logs for the time window and error pattern <span class="mod-wf-tool">Splunk API</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">3</div><div class="mod-wf-text">Identifies root cause: database connection pool exhaustion during peak traffic <span class="mod-wf-tool">Reasoning</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">4</div><div class="mod-wf-text">Searches knowledge base for similar past incidents and their resolutions <span class="mod-wf-tool">RAG lookup</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">5</div><div class="mod-wf-text">Drafts resolution steps and creates a Jira comment with root cause, evidence, and suggested fix <span class="mod-wf-tool">Jira API</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">6</div><div class="mod-wf-text">Sends Slack notification to on-call engineer with summary and Jira link for human approval before any fix is applied <span class="mod-wf-tool">Slack API + Human checkpoint</span></div></div>
</div>
</div>

<div class="mod-workflow-card">
<div class="mod-workflow-card-header">
  <div class="mod-workflow-card-title">Workflow 2 — Candidate screening agent</div>
  <div class="mod-workflow-card-sub">Used by Indian IT HR teams and staffing firms for volume hiring</div>
</div>
<div class="mod-workflow-card-body">
  <div class="mod-wf-step"><div class="mod-wf-num">1</div><div class="mod-wf-text">New job application received for "Python Developer — 2–3 years experience" <span class="mod-wf-tool">Perception</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">2</div><div class="mod-wf-text">Agent reads resume PDF and extracts structured data: skills, years of experience, last role, education <span class="mod-wf-tool">PDF parser + LLM extraction</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">3</div><div class="mod-wf-text">Compares extracted data against the job description requirements and scores the candidate <span class="mod-wf-tool">Reasoning</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">4</div><div class="mod-wf-text">If score above threshold: drafts personalised email inviting candidate for technical screening <span class="mod-wf-tool">Email draft</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">5</div><div class="mod-wf-text">HR manager reviews and approves the email before it is sent — no autonomous sending without human sign-off <span class="mod-wf-tool">Human checkpoint</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">6</div><div class="mod-wf-text">Updates ATS (Applicant Tracking System) with screening status and score <span class="mod-wf-tool">ATS API</span></div></div>
</div>
</div>

<div class="mod-workflow-card">
<div class="mod-workflow-card-header">
  <div class="mod-workflow-card-title">Workflow 3 — Financial compliance monitoring agent</div>
  <div class="mod-workflow-card-sub">Wipro deployed for a UK financial services client — from Module 1.3</div>
</div>
<div class="mod-workflow-card-body">
  <div class="mod-wf-step"><div class="mod-wf-num">1</div><div class="mod-wf-text">Agent continuously monitors payment transaction streams in real time <span class="mod-wf-tool">Perception — live data feed</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">2</div><div class="mod-wf-text">Flags transactions matching anomaly patterns: unusual amounts, velocity, cross-border combinations <span class="mod-wf-tool">ML model + Reasoning</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">3</div><div class="mod-wf-text">Retrieves relevant regulatory rules from compliance knowledge base for each flagged transaction <span class="mod-wf-tool">RAG lookup</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">4</div><div class="mod-wf-text">Generates a structured compliance report: transaction details, anomaly evidence, applicable regulation, risk level <span class="mod-wf-tool">Report generation</span></div></div>
  <div class="mod-wf-step"><div class="mod-wf-num">5</div><div class="mod-wf-text">Routes high-risk flags to human compliance officer for final decision — no autonomous account blocking <span class="mod-wf-tool">Human checkpoint</span></div></div>
</div>
</div>

---

## Where AI agents are deployed in Indian IT in 2026

<div class="mod-usecase-grid">
  <div class="mod-uc-card">
    <div class="mod-uc-header"><span class="mod-uc-icon">&#128187;</span><div class="mod-uc-title">Software development</div></div>
    <div class="mod-uc-text">Agents write code, run tests, identify failures, propose fixes, and open pull requests — the full development cycle with human review gates. TCS has 150+ specialised agentic AI solutions in this space.</div>
    <div class="mod-uc-stat">Claude Code, GitHub Copilot Workspace, Cursor — all agent-powered</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-header"><span class="mod-uc-icon">&#127979;</span><div class="mod-uc-title">Customer support</div></div>
    <div class="mod-uc-text">Agents handle Level 1 and Level 2 support: look up account information, process standard requests, update records, and escalate complex cases to humans. Always on, no attrition, consistent quality.</div>
    <div class="mod-uc-stat">Widely deployed at Indian banks, telecom companies, e-commerce</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-header"><span class="mod-uc-icon">&#128203;</span><div class="mod-uc-title">Document processing</div></div>
    <div class="mod-uc-text">Agents read invoices, contracts, forms, and applications — extract structured data, validate against rules, flag exceptions, and route to the right team. Replaces manual data entry at scale.</div>
    <div class="mod-uc-stat">Infosys deployed 500+ AI agents for document workflows across major clients</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-header"><span class="mod-uc-icon">&#128200;</span><div class="mod-uc-title">Research and competitive intelligence</div></div>
    <div class="mod-uc-text">Agents browse the web, read industry reports, extract key data points, and synthesise findings into structured briefings — replacing hours of manual research per week for analysts and strategy teams.</div>
    <div class="mod-uc-stat">Used at consulting teams in TCS, Wipro, and Accenture India</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-header"><span class="mod-uc-icon">&#129328;</span><div class="mod-uc-title">IT operations and monitoring</div></div>
    <div class="mod-uc-text">Agents monitor infrastructure, detect anomalies, correlate alerts across systems, diagnose root causes, and trigger standard remediation scripts — with human approval for anything that affects production.</div>
    <div class="mod-uc-stat">HCL and Wipro cybersecurity operations — referenced in Module 1.3</div>
  </div>
  <div class="mod-uc-card">
    <div class="mod-uc-header"><span class="mod-uc-icon">&#127959;</span><div class="mod-uc-title">Supply chain and procurement</div></div>
    <div class="mod-uc-text">Agents monitor supplier lead times, flag risks, compare quotes, and draft purchase orders. TCS's agentic AI solutions in supply chain operate inside client value chains, orchestrating actual business transactions.</div>
    <div class="mod-uc-stat">TCS 150+ specialised agentic AI solutions — supply chain and financial services</div>
  </div>
</div>

---

## The tools that power AI agents in 2026

<div class="mod-table-wrap">
<table class="mod-table">
<thead><tr><th>Tool / Framework</th><th>What it does</th><th>Who uses it</th></tr></thead>
<tbody>
  <tr>
    <td>Claude Code</td>
    <td>Agentic coding — reads your codebase, writes code, runs tests, fixes failures autonomously. Leading coding agent in 2026.</td>
    <td>Developers at Indian IT companies, individual engineers</td>
  </tr>
  <tr>
    <td>Microsoft 365 Copilot</td>
    <td>RAG + agent capabilities across Outlook, Teams, Word, Excel. Can summarise meetings, draft emails, update spreadsheets autonomously. Deployed to 330K+ employees at TCS, Infosys, Wipro.</td>
    <td>All roles — the most widely deployed agent tool in Indian IT</td>
  </tr>
  <tr>
    <td>LangGraph / LangChain</td>
    <td>Python frameworks for building multi-step agent workflows. Developers use these to wire together LLMs, tools, and memory.</td>
    <td>Developers building custom agent systems</td>
  </tr>
  <tr>
    <td>n8n / Zapier</td>
    <td>No-code workflow automation. Connect apps, trigger actions based on events, build simple agent-like automations without writing code. Covered in Module 4.4.</td>
    <td>Non-developers, analysts, managers building automations</td>
  </tr>
  <tr>
    <td>AutoGen (Microsoft)</td>
    <td>Multi-agent framework — multiple specialised AI agents that collaborate, debate, and divide work on complex tasks.</td>
    <td>Enterprise AI teams building production agent systems</td>
  </tr>
</tbody>
</table>
</div>

---

## What you need to know about agent risks

Challenges in deploying AI agents include hallucinations, inconsistent outputs, and error cascades in complex workflows — issues that can introduce serious risks, making reliability and governance critical. Most Indian enterprises are implementing strict monitoring, limited autonomy, and clear oversight to prevent operational failures.

<div class="mod-warning">
<strong>The three agent risks that matter for Indian IT professionals:</strong><br><br>
<strong>1. Error cascades</strong> — in a multi-step agent workflow, a wrong decision in step 2 can produce a chain of correct-looking actions based on wrong premises. By step 7, the outcome is far from what was intended. This is why human checkpoints at high-stakes steps are non-negotiable in enterprise deployments.<br><br>
<strong>2. Autonomous action without review</strong> — an agent that can send emails, update databases, or trigger financial transactions without human approval is a compliance and operational risk. Always know which tools your agent can use autonomously and which require human sign-off.<br><br>
<strong>3. Data access and privacy</strong> — agents that can read files, query databases, and call APIs must have carefully scoped permissions. An agent with access to all company data is a security and DPDP Act compliance risk. Principle of least privilege applies — give agents access to only what they need for the specific task.
</strong>
</div>

---

## How to work alongside AI agents — your role in an agentic workflow

<div class="mod-keypoint">
<strong>The human-in-the-loop is not optional — it is the product.</strong> To gain lasting value from AI agents, enterprises must reimagine workflows and upskill employees to work alongside these systems. Success depends on balancing human judgement with automation. The engineers and analysts who understand how to design, monitor, and govern agent workflows are the most valuable people in any AI team.
</div>

Your role in an agentic workflow is not to do what the agent does — it is to:

**Define the goal clearly** — agents are only as good as the task definition they receive. Ambiguous goals produce unpredictable agent behaviour. This is prompt engineering applied to agent instructions.

**Set the approval gates** — decide which steps in the workflow require human review before the agent proceeds. Sending an email? Human review. Querying a database? Autonomous. Updating a production record? Human review.

**Monitor and debug** — agents fail silently in ways that are harder to catch than code errors. Reviewing agent logs, spotting unexpected tool calls, and identifying when the agent took a wrong turn are increasingly valued skills.

**Validate outputs** — the agent's final output is not automatically correct. Verify against the original goal. Check that each step produced the intended result. This is the human-in-the-loop role that Indian IT companies are actively hiring for.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 4.2</div>
  <ol>
    <li><strong>AI agents act, chatbots answer</strong> — the defining difference is tool use and multi-step autonomous action. An agent can browse the web, run code, call APIs, and complete a multi-step task without human approval at every step. Understanding this distinction is now a baseline expectation in Indian IT interviews.</li>
    <li><strong>The five components are your vocabulary</strong> — perception, reasoning, memory, planning, and tool use. When you hear "agentic AI" in a meeting or interview, you can now decompose any agent system into these five components and describe how each works. This is the conceptual fluency that separates informed professionals from passive observers.</li>
    <li><strong>Human-in-the-loop is the career opportunity</strong> — enterprises are not deploying fully autonomous agents for high-stakes tasks. They are deploying supervised agents with human checkpoints. The professionals who know how to define goals, set approval gates, monitor workflows, and validate outputs are the most valued people in any AI deployment team.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-42">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 4.2 — Map an AI Agent Workflow for a Real Task</h3>
  </div>
  <p>This assignment develops the workflow design skill that Indian IT companies look for in AI delivery roles.</p>
  <ol>
    <li><strong>Choose a repetitive task</strong> in your target domain — something currently done manually that involves multiple steps, multiple systems, or both. Good candidates: weekly report generation, ticket triage, data extraction from documents, candidate screening, status update emails.</li>
    <li><strong>Map it as an agent workflow</strong> using the five-component framework:
      <ul>
        <li><strong>Goal:</strong> What is the agent trying to accomplish? (One clear sentence)</li>
        <li><strong>Tools needed:</strong> Which systems does the agent need to access? (APIs, files, databases, email)</li>
        <li><strong>Steps:</strong> Break the task into 4–7 numbered steps the agent would take</li>
        <li><strong>Human checkpoints:</strong> At which steps should a human review before the agent proceeds?</li>
        <li><strong>Risk:</strong> What could go wrong if the agent makes a wrong decision at step X?</li>
      </ul>
    </li>
    <li><strong>Add to your AI Learning Journal</strong> under "Module 4.2 — Agent Workflow Design." This pairs with your RAG use case from Assignment 4.1 — together they show you can think at an AI systems level, not just a tools level.</li>
  </ol>
  <p>Being able to design a human-supervised agent workflow on a whiteboard — identifying tools, steps, and approval gates — is a skill that will set you apart in every AI-related placement interview you attend from here on.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit4/module-4-1-rag-explained/">&#8592; Module 4.1: RAG Explained Simply</a>
  <a class="mod-nav-next" href="/courses/genai/unit4/module-4-3-finetuning-vs-prompting/">Module 4.3: Fine-Tuning vs Prompting &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>40% of enterprise applications will include task-specific AI agents by 2026 — Gartner</td><td>Medium / Noukha Technologies, February 2026; techaheadcorp.com May 2026</td></tr>
      <tr><td>57% of companies already have AI agents running in production</td><td>G2 Enterprise AI Agents Report, December 2025</td></tr>
      <tr><td>Global agentic AI market $7.6B in 2025 → $182B by 2033</td><td>Grand View Research, cited in chirpn.com June 2026</td></tr>
      <tr><td>47% of Indian organisations operate multiple GenAI use cases; India's AI journey turning point</td><td>EY AIdea of India 2026 report, January 2026</td></tr>
      <tr><td>AI agent definition: software that decides next step, uses tools, completes tasks toward goal</td><td>Medium / Noukha Technologies February 2026; cogitx.ai April 2026</td></tr>
      <tr><td>Core components: perception, reasoning, memory, planning, tool-based actions</td><td>cogitx.ai AI Agents Complete Overview 2026, April 2026</td></tr>
      <tr><td>Agents operate in continuous loop of plan, act, observe, adapt</td><td>cogitx.ai AI Agents Complete Overview 2026, April 2026</td></tr>
      <tr><td>Hallucinations, error cascades, inconsistent outputs — Indian enterprises using strict monitoring and limited autonomy</td><td>EY AIdea of India 2026 / Agents and Digital Workforce, January 2026</td></tr>
      <tr><td>Success depends on balancing human judgement with automation</td><td>EY AIdea of India 2026, January 2026</td></tr>
      <tr><td>TCS 150+ agentic AI solutions; Infosys 500+ agents; Wipro financial services agent deployment</td><td>Module 1.3 sources — TCS FY25 Year-End Debrief; Infosys FY26 earnings; Wipro 6-K FY2025</td></tr>
    </tbody>
  </table>
</details>

</div>
