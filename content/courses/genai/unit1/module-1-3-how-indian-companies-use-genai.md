---
title: "Module 1.3: How Indian Companies Are Using GenAI — TCS, Infosys, Wipro, HCL"
description: "Real GenAI projects at TCS, Infosys, Wipro, and HCL in 2025–26 — what they are building, which roles are involved, and what this means for your career as an Indian IT fresher."
weight: 3
sidebar: false
mainroad_aside: false
tags: ["tcs", "infosys", "wipro", "hcl", "genai-india", "it-careers", "india", "generative-ai"]
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
/* ── Company cards ───────────────────────────────────────────── */
.mod-company{border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:24px 0}
.mod-company-header{padding:13px 18px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px}
.mod-company-name{font-size:16px;font-weight:700;color:#fff;margin:0}
.mod-company-tag{font-size:11px;color:rgba(255,255,255,0.85);background:rgba(255,255,255,0.18);padding:3px 10px;border-radius:20px}
.mod-company-body{padding:16px 18px;background:#fff}
.mod-company-stat{display:flex;gap:12px;flex-wrap:wrap;margin-bottom:16px}
.mod-stat-pill{background:#f5f5f4;border:1px solid #e0e0e0;border-radius:6px;padding:8px 14px;text-align:center;flex:1;min-width:120px}
.mod-stat-num{font-size:18px;font-weight:700;color:#1565C0;margin-bottom:2px}
.mod-stat-label{font-size:11px;color:#777}
.mod-usecase-list{margin:0 0 14px;padding-left:0;list-style:none}
.mod-usecase-list li{font-size:13px;color:#333;padding:7px 0 7px 24px;border-bottom:1px solid #f5f5f5;position:relative;line-height:1.5}
.mod-usecase-list li:last-child{border-bottom:none}
.mod-usecase-list li::before{content:"→";position:absolute;left:4px;color:#1565C0;font-weight:700}
.mod-company-footer{background:#f9f9f9;border-top:1px solid #f0f0f0;padding:11px 18px;font-size:12px;color:#666;display:flex;align-items:flex-start;gap:6px}
.mod-company-footer strong{color:#1565C0}
/* ── Roles impact table ──────────────────────────────────────── */
.mod-table-wrap{overflow-x:auto;margin:20px 0}
.mod-table{width:100%;border-collapse:collapse;font-size:13px}
.mod-table th{background:#1565C0;color:#fff;padding:10px 13px;text-align:left;font-weight:600;font-size:12px}
.mod-table td{padding:10px 13px;border-bottom:1px solid #f0f0f0;color:#333;vertical-align:top;line-height:1.5}
.mod-table tr:last-child td{border-bottom:none}
.mod-table tr:nth-child(even) td{background:#fafafa}
.mod-table td:first-child{font-weight:600;color:#1565C0;white-space:nowrap}
/* ── Stat grid ───────────────────────────────────────────────── */
.mod-stat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:20px 0}
.mod-stat-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;text-align:center}
.mod-stat-card-num{font-size:24px;font-weight:700;color:#1565C0;margin-bottom:4px}
.mod-stat-card-label{font-size:12px;color:#666;line-height:1.4}
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
@media(max-width:520px){.mod-stat-grid{grid-template-columns:1fr 1fr}.mod-company-stat{flex-direction:column}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:10%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">2 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit current" href="/courses/genai/#module-1">Understanding GenAI</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-2">Prompt Engineering</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-3">GenAI for Your Job</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-4">Advanced Techniques</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Career & India</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 1 &nbsp;›&nbsp; MODULE 3 OF 4</span>
    <h1 class="mod-title-inline">How Indian Companies Are Using GenAI — TCS, Infosys, Wipro, HCL</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Career-focused</span>
  </div>
</div>

You now understand what GenAI is and which tools to use. This module answers the question that matters most for your career: *what is actually happening inside the companies you want to work at?*

TCS, Infosys, Wipro, and HCL are not experimenting with AI. They are deploying it in production — right now, at scale — across their client projects and internal operations. Understanding what they are building, and which roles are involved, gives you a concrete advantage in every interview and placement drive you attend from here on.

---

## The scale of GenAI adoption in Indian IT

Before looking at individual companies, here is the macro picture:

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">500K</div>
    <div class="mod-stat-card-label">Developers being upskilled in AI by TCS, Infosys, Wipro and Tech Mahindra combined</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">91%</div>
    <div class="mod-stat-card-label">Indian enterprise leaders who cite deployment speed as the key AI decision factor (EY 2026)</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">47%</div>
    <div class="mod-stat-card-label">Indian organisations operating multiple GenAI use cases in production (EY AIdea of India 2026)</div>
  </div>
</div>

<div class="mod-keypoint">
<strong>The shift has already happened.</strong> Indian IT companies are no longer evaluating GenAI — they are deploying it. Wipro CEO Srini Pallia said at Davos in January 2026: "For our clients, 2025 was more about deploying AI proof of concepts and bringing productivity benefits. That is dramatically changing in 2026." This means the companies you are applying to are actively looking for people who understand AI — not as a bonus skill, but as a baseline expectation.
</div>

---

## TCS — Agentic AI at Enterprise Scale

<div class="mod-company">
<div class="mod-company-header" style="background:#cc0000">
  <div class="mod-company-name">Tata Consultancy Services</div>
  <span class="mod-company-tag">580+ AI engagements in Q4 FY25</span>
</div>
<div class="mod-company-body">
  <div class="mod-company-stat">
    <div class="mod-stat-pill"><div class="mod-stat-num">580+</div><div class="mod-stat-label">AI business engagements Q4 FY25</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">150+</div><div class="mod-stat-label">Specialised agentic AI solutions built</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">NVIDIA</div><div class="mod-stat-label">Partnership for telecom & autonomous systems</div></div>
  </div>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT TCS IS BUILDING WITH GENAI</div>
  <ul class="mod-usecase-list">
    <li><strong>Agentic AI for financial services and supply chain</strong> — AI agents that orchestrate actual business transactions inside client value chains using reasoning and planning capabilities of LLMs</li>
    <li><strong>150+ specialised agentic AI solutions</strong> across financial services, accounting, and supply chain management — deployed for global enterprise clients</li>
    <li><strong>AI-powered AWS integrations</strong> — modernising legacy enterprise systems using GenAI for faster triage, code generation, and testing</li>
    <li><strong>NVIDIA partnership</strong> for AI products in telecom and autonomous systems — TCS is building AI-embedded products, not just services</li>
    <li><strong>University of Cincinnati partnership</strong> — "My First AI Job" programme to prepare entry-level talent for AI careers (directly relevant to you)</li>
  </ul>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT THIS MEANS FOR YOUR TCS INTERVIEW</div>
  <p style="font-size:13px;color:#444;margin:0;line-height:1.6">TCS describes GenAI as enabling "agentic AI to orchestrate actual transactions inside business value chains." In your interview, show you understand the difference between a chatbot (answering questions) and an AI agent (taking actions). Mentioning agentic AI and how it applies to the domain you are interviewing for will make you stand out immediately.</p>
</div>
<div class="mod-company-footer">
  <strong>Source:</strong>&nbsp;TCS FY25 Year-End Debrief, TCS investor relations, April 2026
</div>
</div>

---

## Infosys — Topaz Platform and AI at Client Delivery Scale

<div class="mod-company">
<div class="mod-company-header" style="background:#007cc3">
  <div class="mod-company-name">Infosys</div>
  <span class="mod-company-tag">Infosys Topaz — AI-first services platform</span>
</div>
<div class="mod-company-body">
  <div class="mod-company-stat">
    <div class="mod-stat-pill"><div class="mod-stat-num">4,600+</div><div class="mod-stat-label">Active AI projects</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">28M+</div><div class="mod-stat-label">Lines of AI-generated code</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">500+</div><div class="mod-stat-label">AI agents deployed across clients</div></div>
  </div>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT INFOSYS IS BUILDING WITH GENAI</div>
  <ul class="mod-usecase-list">
    <li><strong>Infosys Topaz</strong> — an AI-first services platform combining GenAI technologies across software development, HR, recruitment, sales, vendor management, and industry solutions</li>
    <li><strong>Automated SDLC documentation and code generation</strong> — partnered with AWS Amazon Q Developer to automate software development lifecycle work including code generation, debugging, testing, and legacy modernisation</li>
    <li><strong>100+ new GenAI agents</strong> being developed for client deployment — automating productivity, operations, and growth tasks across 200 major clients</li>
    <li><strong>Cambridge AI lab</strong> — collaboration with the University of Cambridge focused on advanced AI research</li>
    <li><strong>Manufacturing, telecom, financial services, and consumer goods</strong> — the four priority verticals where Infosys is deploying GenAI solutions at scale in 2026</li>
  </ul>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT THIS MEANS FOR YOUR INFOSYS INTERVIEW</div>
  <p style="font-size:13px;color:#444;margin:0;line-height:1.6">Infosys uses the term "Infosys Topaz" constantly in their communications. Look it up before your interview — understanding what it is and how it differs from a generic AI tool shows you follow industry news. Also, 28 million lines of AI-generated code means developers at Infosys are already using AI coding tools daily. Mentioning your experience with GitHub Copilot or Claude for code generation is highly relevant.</p>
</div>
<div class="mod-company-footer">
  <strong>Source:</strong>&nbsp;Infosys–AWS collaboration announcement January 2026, Infosys FY26 earnings commentary
</div>
</div>

---

## Wipro — Consulting-Led, AI-Powered Operating Model

<div class="mod-company">
<div class="mod-company-header" style="background:#341f6e">
  <div class="mod-company-name">Wipro</div>
  <span class="mod-company-tag">Lab45 AI research + FullStride Cloud AI platform</span>
</div>
<div class="mod-company-body">
  <div class="mod-company-stat">
    <div class="mod-stat-pill"><div class="mod-stat-num">60+</div><div class="mod-stat-label">GenAI use cases for software testing alone</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">40%</div><div class="mod-stat-label">Enterprise knowledge management via GenAI (Gartner/Wipro)</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">2026</div><div class="mod-stat-label">Year Wipro launched AI-powered operating model</div></div>
  </div>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT WIPRO IS BUILDING WITH GENAI</div>
  <ul class="mod-usecase-list">
    <li><strong>AI-powered operating model launched February 2026</strong> — combines advisory, AI, and enterprise transformation into one end-to-end service — connecting boardroom strategy to scaled operations</li>
    <li><strong>Intelligent Agents for financial data analysis</strong> — deployed for a UK-based financial services group to analyse payments data, generate intelligence dashboards, fraud detection alerts, and compliance reports in real time</li>
    <li><strong>AI-first cybersecurity operations</strong> — deployed for a leading apparel company to streamline IT operations, improve regulatory compliance, and automate security workflows</li>
    <li><strong>Prior authorisation workflows in healthcare</strong> — using AI to reduce turnaround times for a US-based healthcare payer's member services</li>
    <li><strong>Developer productivity via GenAI</strong> — 60+ GenAI use cases for software testing optimisation across client projects</li>
  </ul>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT THIS MEANS FOR YOUR WIPRO INTERVIEW</div>
  <p style="font-size:13px;color:#444;margin:0;line-height:1.6">Wipro's new operating model emphasises "persona-based, end-to-end enterprise transformation." In practice, this means they want people who can connect an AI tool to a specific business outcome — not just people who know how to use the tool. Frame your AI knowledge in terms of business impact: "I used AI to reduce X time" or "I used AI to improve Y output" rather than "I know how to use ChatGPT."</p>
</div>
<div class="mod-company-footer">
  <strong>Source:</strong>&nbsp;Wipro 6-K filing FY2025, Wipro AI-powered operating model announcement February 2026
</div>
</div>

---

## HCL Technologies — Internal AI Adoption and Client Solutions

<div class="mod-company">
<div class="mod-company-header" style="background:#005ea6">
  <div class="mod-company-name">HCL Technologies</div>
  <span class="mod-company-tag">AI across all corporate functions + client delivery</span>
</div>
<div class="mod-company-body">
  <div class="mod-company-stat">
    <div class="mod-stat-pill"><div class="mod-stat-num">100s</div><div class="mod-stat-label">GenAI opportunities in active pursuit</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">All</div><div class="mod-stat-label">Corporate functions using GenAI internally</div></div>
    <div class="mod-stat-pill"><div class="mod-stat-num">Modular</div><div class="mod-stat-label">Pre-built GenAI platform for enterprise clients</div></div>
  </div>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT HCL IS BUILDING WITH GENAI</div>
  <ul class="mod-usecase-list">
    <li><strong>Developer support lifecycle optimisation</strong> — selected as preferred AI partner by a major global tech company, deploying AI and ML across product cycles for faster triage and improved product quality</li>
    <li><strong>Global compliance framework for financial services</strong> — deploying LLMs alongside ML for proactive surveillance and risk detection for a Europe-based financial firm</li>
    <li><strong>Internal GenAI across all corporate functions</strong> — HR, finance, risk and compliance, sales and marketing all using GenAI internally to improve employee experience and productivity</li>
    <li><strong>Modular GenAI platforms</strong> for enterprise clients — pre-built, scalable solutions that reduce implementation time and cost across industries</li>
    <li><strong>Core development, deployment, testing, and managed services</strong> — all four delivery phases now have GenAI embedded as standard practice</li>
  </ul>
  <div style="font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:8px">WHAT THIS MEANS FOR YOUR HCL INTERVIEW</div>
  <p style="font-size:13px;color:#444;margin:0;line-height:1.6">HCL CEO C. Vijayakumar specifically noted "eating its own dog food" — using GenAI internally before deploying it for clients. In your interview, show you already do the same. If you have used AI tools in your academic projects, coursework, or personal work, that is direct evidence that you apply AI practically — exactly what HCL values.</p>
</div>
<div class="mod-company-footer">
  <strong>Source:</strong>&nbsp;HCLTech AI platform page 2026, Diginomica GenAI India analysis
</div>
</div>

---

## How GenAI is changing specific job roles in Indian IT

This is what matters most as a fresher: which roles are most affected and what will actually be expected of you on Day 1.

<div class="mod-table-wrap">
<table class="mod-table">
<thead>
  <tr>
    <th>Your Role</th>
    <th>What AI is Changing</th>
    <th>What You Need to Know</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Software Developer</td>
    <td>Code generation, debugging, documentation, and test case writing are increasingly AI-assisted. Infosys generated 28M lines of AI code. GitHub Copilot is now standard tooling.</td>
    <td>Learn to write effective prompts for code generation. Understand how to review and verify AI-generated code — not just accept it. Covered in Unit 3.1.</td>
  </tr>
  <tr>
    <td>QA / Testing Engineer</td>
    <td>Wipro has 60+ GenAI use cases for testing alone. AI is automating test case generation, regression testing, and defect detection.</td>
    <td>AI does not eliminate QA — it shifts the role from writing repetitive test cases to designing test strategies and reviewing AI outputs. High-value skill: prompt-driven test case generation.</td>
  </tr>
  <tr>
    <td>Business Analyst</td>
    <td>Requirements documentation, process analysis, and client reports are being auto-generated. TCS's agentic AI works inside business value chains.</td>
    <td>GenAI writes the first draft. Your job is to verify accuracy, catch hallucinations, and add business context the AI cannot know. Critical thinking > typing speed.</td>
  </tr>
  <tr>
    <td>Data Analyst</td>
    <td>Natural language queries are replacing SQL in many internal tools. HCL and Wipro deploy GenAI for real-time intelligence dashboards and compliance reports.</td>
    <td>Learn to work with AI-powered data tools. Being able to ask business questions in plain English and interpret the output correctly is now a core skill.</td>
  </tr>
  <tr>
    <td>DevOps / Cloud Engineer</td>
    <td>Incident detection, resolution, and infrastructure documentation are being automated. Wipro deployed AI-powered predictive and preventive security operations.</td>
    <td>AI handles routine incident triage. You will work alongside AI agents, not instead of them. Understanding what an AI agent is (Unit 4.2) is directly relevant.</td>
  </tr>
  <tr>
    <td>HR / Recruitment (IT Support)</td>
    <td>Infosys uses Topaz for HR and recruitment. AI screens CVs, drafts JDs, and handles onboarding documentation at scale.</td>
    <td>If you enter an IT support or admin role, AI will handle high-volume routine tasks. Your value is in judgement, escalations, and relationship management.</td>
  </tr>
</tbody>
</table>
</div>

---

## The bottom line for freshers

<div class="img-center"><svg width="680" viewBox="0 0 680 130" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Three career signals from Indian IT GenAI adoption: AI skills are baseline not bonus, business context beats tool knowledge, and verifying AI output is the new core skill</title>
<rect x="0" y="0" width="680" height="130" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="340" y="22" text-anchor="middle" font-size="11" font-weight="700" fill="#555" font-family="sans-serif">WHAT INDIAN IT COMPANIES ACTUALLY WANT FROM FRESHERS IN 2026</text>
<rect x="16" y="38" width="204" height="76" rx="7" fill="#e8f0fe" stroke="#90caf9" stroke-width="1"/>
<text x="118" y="62" text-anchor="middle" font-size="11" font-weight="700" fill="#1565C0" font-family="sans-serif">AI skills are baseline</text>
<text x="118" y="80" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Not a bonus. Not optional.</text>
<text x="118" y="97" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Expected from Day 1.</text>
<rect x="238" y="38" width="204" height="76" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="340" y="62" text-anchor="middle" font-size="11" font-weight="700" fill="#FF8C00" font-family="sans-serif">Context beats tool knowledge</text>
<text x="340" y="80" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">"I used AI to improve X"</text>
<text x="340" y="97" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">beats "I know ChatGPT"</text>
<rect x="460" y="38" width="204" height="76" rx="7" fill="#e8f5e9" stroke="#a5d6a7" stroke-width="1"/>
<text x="562" y="62" text-anchor="middle" font-size="11" font-weight="700" fill="#2e7d32" font-family="sans-serif">Verification is the new skill</text>
<text x="562" y="80" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">AI writes the first draft.</text>
<text x="562" y="97" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">You catch its mistakes.</text>
</svg></div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 1.3</div>
  <ol>
    <li><strong>All four major Indian IT companies are deploying GenAI in production</strong> — TCS has 580+ active AI engagements, Infosys has 4,600+ projects and 500+ agents, Wipro launched a new AI operating model in 2026, HCL is using GenAI across all internal functions. This is not a future trend — it is the current state.</li>
    <li><strong>Your role is changing, not disappearing</strong> — AI is automating the repetitive parts of software development, testing, documentation, and analysis. The valuable work is shifting to designing AI workflows, verifying AI output, and applying business judgement that AI cannot replicate.</li>
    <li><strong>Frame your AI skills in terms of outcomes</strong> — every interview you attend at these companies will include an AI-related question. The strongest answer is not "I know ChatGPT" but "I used AI to accomplish X, and here is what I had to do to verify and improve the output."</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-13">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 1.3 — Research Your Target Company's AI Strategy</h3>
  </div>
  <p>This assignment directly prepares you for placement interviews. It takes 20–30 minutes and produces something you can actually use in your next interview.</p>
  <ol>
    <li><strong>Pick one company</strong> you want to work at — TCS, Infosys, Wipro, HCL, or any other Indian IT company you are targeting.</li>
    <li><strong>Find one real GenAI project or initiative</strong> that company has announced in 2025 or 2026. Good sources:
      <ul>
        <li>The company's official newsroom or investor relations page</li>
        <li>Search: "[Company name] GenAI 2026" on Google</li>
        <li>The company's LinkedIn page — they always post major announcements</li>
      </ul>
    </li>
    <li><strong>Write three sentences</strong> about it:
      <ul>
        <li>What the project does</li>
        <li>Which business problem it solves</li>
        <li>Which role you could play in a project like this</li>
      </ul>
    </li>
    <li><strong>Save this as your "Company AI Research" document.</strong> You will add to it as you complete the course. In Module 5.2 you will use it to tailor your resume and LinkedIn profile.</li>
  </ol>
  <p>Interviewers at these companies are consistently impressed when a fresher references a real, recent project by name. It signals you are genuinely engaged — not just attending placement drives to collect offers.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit1/module-1-2-chatgpt-vs-claude-vs-gemini/">&#8592; Module 1.2: ChatGPT vs Claude vs Gemini</a>
  <a class="mod-nav-next" href="/courses/genai/unit1/module-1-4-risks-and-responsible-use/">Module 1.4: Risks and Responsible Use &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>TCS 580+ AI engagements Q4 FY25, 150+ agentic AI solutions</td><td>TCS FY25 Year-End Debrief, April 2026</td></tr>
      <tr><td>Infosys 4,600+ AI projects, 28M lines of AI code, 500+ agents</td><td>Infosys FY26 earnings commentary</td></tr>
      <tr><td>Infosys–AWS collaboration for SDLC automation</td><td>Infosys–AWS press release, January 7 2026</td></tr>
      <tr><td>Wipro AI-powered operating model</td><td>Wipro press release, February 12 2026</td></tr>
      <tr><td>Wipro intelligent agents for UK financial services</td><td>Wipro 6-K SEC filing FY2025</td></tr>
      <tr><td>500K developers being upskilled across major Indian IT firms</td><td>EY AIdea of India 2026 / techdee.com synthesis</td></tr>
      <tr><td>91% of Indian leaders cite deployment speed as key AI factor</td><td>EY AIdea of India 2026 report</td></tr>
      <tr><td>47% of Indian organisations operating multiple GenAI use cases</td><td>EY AIdea of India 2026 report</td></tr>
      <tr><td>Wipro CEO Davos 2026 quote</td><td>techdee.com / Davos 2026 coverage, January 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
