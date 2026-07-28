---
title: "Module 5.4: Final Project — Your Personal AI Toolkit"
description: "Create your personal AI Toolkit document — a living reference that consolidates everything from this course into a career-ready, interview-ready, and work-ready resource."
weight: 4
sidebar: false
mainroad_aside: false
tags: ["final-project", "ai-toolkit", "portfolio", "india", "career", "generative-ai", "completion"]
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
/* ── Callouts ────────────────────────────────────────────────── */
.mod-keypoint{background:#fff8e1;border-left:4px solid #FF8C00;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a3000;line-height:1.6}
.mod-keypoint strong{color:#FF8C00}
.mod-success{background:#e8f5e9;border-left:4px solid #2e7d32;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#1b5e20;line-height:1.6}
.mod-success strong{color:#2e7d32}
/* ── Toolkit section cards ───────────────────────────────────── */
.mod-section-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:16px 0}
.mod-section-header{padding:11px 16px;display:flex;align-items:center;gap:10px;border-bottom:1px solid #f0f0f0;background:#f5f8ff}
.mod-section-num{width:28px;height:28px;border-radius:50%;background:#1565C0;color:#fff;font-size:13px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.mod-section-title{font-size:14px;font-weight:700;color:#1565C0;margin:0;flex:1}
.mod-section-source{font-size:11px;color:#888;font-style:italic}
.mod-section-body{padding:13px 16px}
.mod-section-desc{font-size:13px;color:#333;line-height:1.6;margin:0 0 10px}
.mod-section-template{font-size:12px;font-family:monospace,sans-serif;background:#f5f5f4;border-radius:5px;padding:10px 12px;color:#333;line-height:1.7;white-space:pre-wrap;border-left:3px solid #1565C0}
/* ── What it unlocks ─────────────────────────────────────────── */
.mod-unlock-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-unlock-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-unlock-icon{font-size:20px;margin-bottom:8px}
.mod-unlock-title{font-size:13px;font-weight:700;color:#1565C0;margin:0 0 5px}
.mod-unlock-text{font-size:13px;color:#333;line-height:1.6;margin:0}
/* ── Course completion ───────────────────────────────────────── */
.mod-complete{background:#fff;border:2px solid #2e7d32;border-radius:12px;padding:28px 24px;margin:28px 0;text-align:center}
.mod-complete-icon{font-size:48px;margin-bottom:12px}
.mod-complete-title{font-size:22px;font-weight:700;color:#1a1a1a;margin:0 0 8px}
.mod-complete-sub{font-size:15px;color:#555;line-height:1.7;margin:0 0 20px}
.mod-complete-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin:20px 0}
.mod-complete-stat{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:12px;text-align:center}
.mod-complete-num{font-size:22px;font-weight:700;color:#1565C0;margin-bottom:2px}
.mod-complete-label{font-size:11px;color:#777}
/* ── Unit summary ────────────────────────────────────────────── */
.mod-unit-summary{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin:20px 0}
.mod-unit-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-unit-card-num{font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:4px}
.mod-unit-card-title{font-size:14px;font-weight:700;color:#1565C0;margin:0 0 6px}
.mod-unit-card-summary{font-size:13px;color:#444;line-height:1.6;margin:0}
/* ── Next steps ──────────────────────────────────────────────── */
.mod-next-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin:20px 0}
.mod-next-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;border-top:3px solid #FF8C00}
.mod-next-label{font-size:11px;font-weight:700;color:#FF8C00;letter-spacing:0.05em;margin-bottom:6px}
.mod-next-title{font-size:13px;font-weight:700;color:#1a1a1a;margin:0 0 5px}
.mod-next-text{font-size:12px;color:#555;line-height:1.5;margin:0}
/* ── Assignment, nav, blog, credits ─────────────────────────── */
.mod-assignment{background:#fff8e1;border:2px solid #FF8C00;border-radius:8px;padding:20px 22px;margin:28px 0}
.mod-assignment-header{display:flex;align-items:center;gap:10px;margin-bottom:12px}
.mod-assignment-icon{font-size:20px;color:#FF8C00}
.mod-assignment-title{font-size:16px;font-weight:700;color:#5d4037;margin:0}
.mod-assignment p,.mod-assignment li{font-size:14px;color:#4a3000;line-height:1.7}
.mod-assignment ol,.mod-assignment ul{padding-left:20px;margin:8px 0}
.mod-nav{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;margin-top:32px;padding-top:18px;border-top:1px solid #e0e0e0}
.mod-nav-back{font-size:13px;color:#1565C0;text-decoration:none}
.mod-nav-back:hover{color:#0d47a1;text-decoration:underline}
.mod-nav-home{display:inline-flex;align-items:center;gap:6px;font-size:13px;font-weight:600;padding:9px 18px;border-radius:4px;background:#1565C0;color:#fff !important;text-decoration:none}
.mod-nav-home:hover{background:#0d47a1;color:#fff !important;text-decoration:none}
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
@media(max-width:520px){.mod-unlock-grid{grid-template-columns:1fr}.mod-complete-grid{grid-template-columns:1fr 1fr}.mod-next-grid{grid-template-columns:1fr}.mod-unit-summary{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:95%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">19 of 20 modules complete — final module</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Understanding GenAI ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-2">Prompt Engineering ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-3">GenAI for Your Job ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-4">Advanced Techniques ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-5">Career & India</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 5 &nbsp;›&nbsp; MODULE 4 OF 4</span>
    <h1 class="mod-title-inline">Final Project — Your Personal AI Toolkit</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">&#127942; Course finale</span>
    <span class="mod-meta-item">&#128196; Deliverable: AI Toolkit doc</span>
    <span class="mod-meta-item">&#9200; 2–3 hours to complete</span>
  </div>
</div>

This is the final module. You have covered 20 modules across 5 units — from what Generative AI is to how Indian companies use it, from prompt engineering fundamentals to RAG, agents, fine-tuning, automation, certifications, resume optimisation, and freelancing.

The final project consolidates all of that into one living document: your Personal AI Toolkit. This document is not a certificate you print and forget. It is a practical reference you will use every week — in your job, in your placement interviews, and in your freelance work.

---

## What the AI Toolkit is

<div class="mod-keypoint">
<strong>Your Personal AI Toolkit</strong> is a single, structured document that contains everything you have built in this course: your prompt library, your role library, your company AI research, your automation workflow, and your 90-day action plan. It is the professional output of this course — the thing you have been building module by module, and now assemble into one coherent document.
</div>

It serves four concrete purposes:

<div class="mod-unlock-grid">
  <div class="mod-unlock-card">
    <div class="mod-unlock-icon">&#128188;</div>
    <div class="mod-unlock-title">Interview reference</div>
    <div class="mod-unlock-text">When an interviewer at TCS, Infosys, or a product company asks "How do you use AI in your work?" — you open your Toolkit and walk them through it. Concrete examples beat general answers every time.</div>
  </div>
  <div class="mod-unlock-card">
    <div class="mod-unlock-icon">&#128640;</div>
    <div class="mod-unlock-title">Day 1 advantage</div>
    <div class="mod-unlock-text">On your first day at a new company, you have a tested prompt library and automation toolkit ready to use. While your colleagues are still figuring out AI tools, you are already productive.</div>
  </div>
  <div class="mod-unlock-card">
    <div class="mod-unlock-icon">&#128196;</div>
    <div class="mod-unlock-title">Freelance portfolio</div>
    <div class="mod-unlock-text">For Module 5.3's freelancing path — your Toolkit is your portfolio. It shows a potential client exactly what you can build and how you think. Share the link instead of sending a CV.</div>
  </div>
  <div class="mod-unlock-card">
    <div class="mod-unlock-icon">&#128200;</div>
    <div class="mod-unlock-title">Living reference</div>
    <div class="mod-unlock-text">AI tools change fast. Your Toolkit is designed to be updated quarterly — new prompts, updated tool recommendations, new workflows. It compounds in value as you add to it over time.</div>
  </div>
</div>

---

## The seven sections of your AI Toolkit

Each section maps to work you have already done in this course. The final project is assembly, not creation from scratch.

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">1</div>
  <div class="mod-section-title">My AI Stack — tools I use and why</div>
  <span class="mod-section-source">Source: Modules 1.2, 3.1–3.4</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">A one-page summary of which AI tools you use for which tasks, with a one-line reason for each choice. This section answers the interview question "Which AI tools do you use?" with specificity and clarity rather than a generic list.</div>
  <div class="mod-section-template">MY AI STACK — [Your Name] — Last updated: [Month Year]

DAILY TOOLS
- ChatGPT (free/Plus): [what I use it for]
- Claude (free): [what I use it for]
- GitHub Copilot: [what I use it for]

SPECIALIST TOOLS
- n8n: [what I use it for — specific workflow name]
- Gemini: [what I use it for]

TOOL I'M LEARNING NEXT: [name + why]

WHY I CHOSE THESE OVER ALTERNATIVES: [2–3 sentences]</div>
</div>
</div>

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">2</div>
  <div class="mod-section-title">My Prompt Library — 15+ tested prompts</div>
  <span class="mod-section-source">Source: Modules 2.1–2.4, 3.1–3.4, Assignment 3.4</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">Your prompt library from Assignment 3.4, expanded to at least 15 entries using the standard format from Module 3.4. This is the highest-reuse section of the Toolkit — you will come back to it daily.</div>
  <div class="mod-section-template">PROMPT LIBRARY ENTRY FORMAT (repeat for each prompt)

## [Prompt Name]
Category: Developer / Analyst / Manager / Learning / Other
Tool: ChatGPT / Claude / Gemini / Any
Last tested: [Month Year]
Use case: [one sentence — when to use this]

Prompt:
[Full prompt text with [PLACEHOLDERS] for variable parts]

Notes:
- What this does well
- Common failure mode to watch for
Quality: High / Medium / Low (starting point only)</div>
</div>
</div>

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">3</div>
  <div class="mod-section-title">My Role Library — 5+ persona prompts</div>
  <span class="mod-section-source">Source: Module 2.3, Assignment 2.3</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">The role prompts you customised for your specific context in Assignment 2.3 — your placement mentor, code reviewer, email writer, and any others you have built since. Include the full text of each role with your customisations.</div>
  <div class="mod-section-template">MY ROLE LIBRARY

ROLE 1: [Name — e.g. "My Placement Mentor"]
[Full role prompt text customised for your background, target companies, and domain]

ROLE 2: [Name — e.g. "My Senior Code Reviewer"]
[Full role prompt text customised for your tech stack and coding style]

ROLE 3: [Name]
[Full role prompt text]

[Add more as you build them]</div>
</div>
</div>

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">4</div>
  <div class="mod-section-title">Company AI Research — 2+ target company profiles</div>
  <span class="mod-section-source">Source: Modules 1.3, 4.1, 4.2, Assignments 1.3 and 4.1</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">The company AI research you built across Assignments 1.3, 4.1, and 4.2 — consolidated into structured profiles for each company you are targeting. This section transforms interview preparation from generic to specific.</div>
  <div class="mod-section-template">COMPANY AI PROFILE — [Company Name]

Their AI platform/product: [e.g. "Infosys Topaz — AI-first services platform"]
Key GenAI initiative: [specific project or deployment — with source]
What they are building: [2–3 bullet points from your Module 1.3 research]
AI architecture they use: [RAG / Agents / Fine-tuning — from your Module 4 research]
Role I could play in their AI work: [specific, role-appropriate answer]
Interview talking point: [one question you could ask them about their AI work]
Source + date: [URL or publication, month/year]</div>
</div>
</div>

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">5</div>
  <div class="mod-section-title">My Automation Workflow — built in Module 4.4</div>
  <span class="mod-section-source">Source: Module 4.4, Assignment 4.4</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">Documentation of the automation workflow you built in Assignment 4.4 — what it does, which tools it uses, a screenshot of the workflow canvas, and the link to the GitHub repository or Zapier/n8n exported workflow.</div>
  <div class="mod-section-template">MY AUTOMATION WORKFLOW

Name: [e.g. "Weekly Job Alert to WhatsApp"]
Tool: n8n / Zapier / Make
Problem it solves: [one sentence]
Time saved per week: [estimated hours]

Steps:
1. [Trigger — what starts the workflow]
2. [Step 2]
3. [AI step — what the AI does]
4. [Output step]
5. [Human checkpoint if any]

GitHub link / Zapier template link: [URL]
Screenshot: [embed or link]
Date built: [Month Year]</div>
</div>
</div>

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">6</div>
  <div class="mod-section-title">My Architecture Decision Framework</div>
  <span class="mod-section-source">Source: Modules 4.1, 4.2, 4.3, Assignments 4.1–4.3</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">Your personal decision framework for choosing between Prompting, RAG, Agents, and Fine-tuning — with the real use case examples you analysed in Assignments 4.1, 4.2, and 4.3. This section directly addresses the most common AI architecture question in Indian IT interviews.</div>
  <div class="mod-section-template">MY ARCHITECTURE DECISION FRAMEWORK

WHEN I RECOMMEND PROMPTING:
[Your criteria from Module 4.3 in your own words]
My example: [real use case from your Assignments]

WHEN I RECOMMEND RAG:
[Your criteria]
My example: [your Assignment 4.1 RAG use case]

WHEN I RECOMMEND AGENTS:
[Your criteria]
My example: [your Assignment 4.2 agent workflow]

WHEN I RECOMMEND FINE-TUNING:
[Your criteria from Module 4.3]
My example: [use case where fine-tuning was the right answer]

THE QUESTION I ALWAYS ASK FIRST:
[Your one diagnostic question — from the Module 4.3 decision framework]</div>
</div>
</div>

<div class="mod-section-card">
<div class="mod-section-header">
  <div class="mod-section-num">7</div>
  <div class="mod-section-title">My 90-Day Action Plan</div>
  <span class="mod-section-source">Source: Modules 5.1, 5.2, 5.3</span>
</div>
<div class="mod-section-body">
  <div class="mod-section-desc">A concrete 90-day plan combining your certification path from Module 5.1, profile update from Module 5.2, and first freelance client from Module 5.3. This is the bridge from completing the course to acting on what you have learned.</div>
  <div class="mod-section-template">MY 90-DAY AI ACTION PLAN — Starting: [Date]

MONTH 1 — CERTIFY AND APPLY
Week 1–2: Complete [certification name] free audit on Coursera
Week 3: Apply for Financial Aid OR purchase certificate
Week 4: Update LinkedIn headline and About section (Module 5.2 checklist)
Target: LinkedIn views increased, Naukri profile at 80%+ completeness

MONTH 2 — BUILD AND SHOW
Week 5–6: Build [your automation workflow] — document on GitHub
Week 7: Apply to [specific number] job openings with tailored resume
Week 8: Reach out to [name of first potential freelance client]
Target: One GitHub project live, one freelance conversation started

MONTH 3 — APPLY AND EARN
Week 9–10: Apply to [target number] placements/jobs per week
Week 11: Deliver first freelance project (or submit first interview)
Week 12: Review Toolkit, update prompt library, plan next 90 days
Target: [specific goal — first interview, first client, first offer]</div>
</div>
</div>

---

## How to build and share your Toolkit

**Format — use Notion or Google Docs.** Notion works best because it is searchable, supports callout blocks, and generates a shareable link in one click. Google Docs is fine if you already use it daily. Either is better than a PDF — PDFs cannot be updated.

**Sharing — generate a public link.** A Notion page or Google Doc set to "Anyone with the link can view" becomes a living portfolio link you can:
- Add to your LinkedIn Featured section (Module 5.2)
- Include in your Upwork or Fiverr profile
- Share with an interviewer: "Would you like to see how I have applied GenAI to real tasks?"
- Send to a potential freelance client instead of a CV

**Updating — quarterly review.** Schedule a recurring reminder every three months to review the Toolkit: test your top prompts, update the tool recommendations, add new workflows, and update the 90-day plan. An AI Toolkit that is 12 months out of date is a liability, not an asset.

---

## What you have built — the complete course

<div class="mod-unit-summary">
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">UNIT 1 — MODULES 1.1–1.4</div>
    <div class="mod-unit-card-title">Understanding GenAI</div>
    <div class="mod-unit-card-summary">How LLMs work, which tools to use when, how Indian IT companies deploy GenAI in production, and how to use it responsibly — including India's DPDP Act and hallucination risks.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">UNIT 2 — MODULES 2.1–2.4</div>
    <div class="mod-unit-card-title">Prompt Engineering Basics</div>
    <div class="mod-unit-card-summary">Six-component prompt structure, zero-shot/few-shot/CoT techniques, role prompting and persona design, and a diagnostic framework for fixing prompts that fail.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">UNIT 3 — MODULES 3.1–3.4</div>
    <div class="mod-unit-card-title">GenAI for Your Job</div>
    <div class="mod-unit-card-summary">Practical AI for developers (code generation, debugging, testing), analysts (SQL, Python, reports), and managers (emails, meeting summaries, presentations) — plus a 15-prompt personal library.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">UNIT 4 — MODULES 4.1–4.4</div>
    <div class="mod-unit-card-title">Advanced Techniques</div>
    <div class="mod-unit-card-summary">RAG architecture, AI agents and multi-step workflows, the Prompt→RAG→Fine-tune decision framework, and no-code automation with n8n/Zapier/Make.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">UNIT 5 — MODULES 5.1–5.4</div>
    <div class="mod-unit-card-title">Career and India Context</div>
    <div class="mod-unit-card-summary">Certifications ranked for Indian IT, AI-optimised resume/LinkedIn/Naukri profiles, six freelancing services with real pricing, and your Personal AI Toolkit — the career-ready capstone.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">DELIVERABLES BUILT</div>
    <div class="mod-unit-card-title">What you take away</div>
    <div class="mod-unit-card-summary">Prompt library (15+ prompts), role library (5+ personas), company AI research (2+ profiles), automation workflow (live on GitHub), architecture decision framework, 90-day plan, and optimised profiles on LinkedIn and Naukri.</div>
  </div>
</div>

---

## What comes next

<div class="mod-next-grid">
  <div class="mod-next-card">
    <div class="mod-next-label">IMMEDIATELY</div>
    <div class="mod-next-title">Update your profiles</div>
    <div class="mod-next-text">Apply the Module 5.2 checklist to LinkedIn and Naukri today. Every day your profiles are not optimised is a day recruiters cannot find you.</div>
  </div>
  <div class="mod-next-card">
    <div class="mod-next-label">THIS WEEK</div>
    <div class="mod-next-title">Start your certification</div>
    <div class="mod-next-text">Enrol in the Google AI Essentials free audit (5 hours). Complete it this week. The momentum from finishing a course is best channelled immediately into the next concrete action.</div>
  </div>
  <div class="mod-next-card">
    <div class="mod-next-label">THIS MONTH</div>
    <div class="mod-next-title">Apply your Toolkit</div>
    <div class="mod-next-text">Use your prompt library in your actual work this week. Apply to one real job with a tailored resume. Reach out to one potential freelance client. Start moving from learning to doing.</div>
  </div>
</div>

---

<div class="mod-complete" id="final-project">
  <div class="mod-complete-icon">&#127942;</div>
  <div class="mod-complete-title">Course Complete — Generative AI: Zero to Job-Ready</div>
  <div class="mod-complete-sub">You have completed all 20 modules. Here is what you have covered:</div>
  <div class="mod-complete-grid">
    <div class="mod-complete-stat"><div class="mod-complete-num">20</div><div class="mod-complete-label">Modules completed</div></div>
    <div class="mod-complete-stat"><div class="mod-complete-num">5</div><div class="mod-complete-label">Units across 4 weeks</div></div>
    <div class="mod-complete-stat"><div class="mod-complete-num">15+</div><div class="mod-complete-label">Prompts in your library</div></div>
    <div class="mod-complete-stat"><div class="mod-complete-num">1</div><div class="mod-complete-label">Live automation workflow</div></div>
  </div>
  <div class="mod-complete-sub" style="margin:0">This course was free. The knowledge is yours. The Toolkit compounds in value every week you use it.<br>Stay current at <a href="https://chandrashaker.in" target="_blank" rel="noopener"><strong>CHANDRAS EDU</strong></a> — new posts on AI, careers, and investing every week.</div>
</div>

---

<div class="mod-assignment" id="assignment-54">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#127942;</span>
    <h3 class="mod-assignment-title">Final Project — Create Your Personal AI Toolkit Document</h3>
  </div>
  <p>This is the course capstone. Block 2–3 hours — ideally a weekend session — and build it from start to finish.</p>
  <ol>
    <li><strong>Create a new Notion page or Google Doc</strong> titled "My Personal AI Toolkit — [Your Name] — [Month Year]."</li>
    <li><strong>Add all seven sections</strong> using the templates from this module. Fill each section with the actual work you have done in this course:
      <ul>
        <li>Section 1 — AI Stack: your tool choices from Modules 1.2 and 3.1–3.4</li>
        <li>Section 2 — Prompt Library: transfer your 15+ prompts from Assignment 3.4, formatted with the standard entry</li>
        <li>Section 3 — Role Library: your 5+ customised personas from Assignment 2.3</li>
        <li>Section 4 — Company Research: your profiles from Assignments 1.3, 4.1, and 4.2</li>
        <li>Section 5 — Automation Workflow: documentation and link from Assignment 4.4</li>
        <li>Section 6 — Architecture Framework: your decision criteria from Assignments 4.1–4.3</li>
        <li>Section 7 — 90-Day Plan: your specific dates, certifications, and targets from Module 5.1–5.3</li>
      </ul>
    </li>
    <li><strong>Generate a public sharing link</strong> from Notion or Google Docs.</li>
    <li><strong>Add the link to your LinkedIn Featured section</strong> — this makes your Toolkit visible to every recruiter who views your profile.</li>
    <li><strong>Optional but strongly recommended:</strong> Share your completed Toolkit link in a LinkedIn post explaining what the course covered and what you built. Tag <a href="https://www.linkedin.com/in/chandra-shaker-arrabotu/" target="_blank" rel="noopener">Chandra Shaker</a> and use the hashtag #GenAIZeroToJobReady. The act of sharing publicly commits you to the 90-day plan in Section 7.</li>
  </ol>
  <p>Your Toolkit is now your primary career asset for AI-related work. Update it quarterly. Add to your prompt library every week. Revisit the company research before every interview. The course ends here — the Toolkit does not.</p>
</div>

<div class="mod-success">
<strong>Thank you for completing this course.</strong> It was designed specifically for Indian engineering students and IT professionals who want to move from understanding AI to using it effectively in their careers. Everything in it — the examples, the company data, the pricing, the legal context — was built for India in 2026. I hope it serves you well for years beyond that.<br><br>
Stay connected at <a href="https://chandrashaker.in" target="_blank" rel="noopener"><strong>CHANDRAS EDU</strong></a> — new content on AI, careers, and investing every week. — <strong>Chandra Shaker</strong>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">CONTINUE LEARNING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — CHANDRAS EDU (chandrashaker.in)</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — CHANDRAS EDU (chandrashaker.in)</a>
  <a href="https://chandrashaker.in">More posts on AI, careers, and investing → CHANDRAS EDU (chandrashaker.in)</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit5/module-5-3-ai-freelancing-india/">&#8592; Module 5.3: Freelancing with AI</a>
  <a class="mod-nav-home" href="/courses/genai/">&#127968; Back to course home</a>
</div>

<details class="mod-credits">
  <summary>About this course</summary>
  <table>
    <thead><tr><th>Item</th><th>Detail</th></tr></thead>
    <tbody>
      <tr><td>Course title</td><td>Generative AI: Zero to Job-Ready</td></tr>
      <tr><td>Instructor</td><td>Chandra Shaker — CHANDRAS EDU (chandrashaker.in)</td></tr>
      <tr><td>Units</td><td>5 units, 20 modules</td></tr>
      <tr><td>Target audience</td><td>Indian engineering students and IT freshers</td></tr>
      <tr><td>Prerequisites</td><td>None — no prior AI or coding experience required</td></tr>
      <tr><td>Cost</td><td>Free — all 20 modules permanently free</td></tr>
      <tr><td>Last updated</td><td>June 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
