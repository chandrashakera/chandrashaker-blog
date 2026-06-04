---
title: "Module 3.4: Building Your Personal Prompt Library"
description: "How to build, organise, and maintain a reusable prompt library for your specific role — the most practical career deliverable of Unit 3 for Indian IT students and professionals."
weight: 4
sidebar: false
mainroad_aside: false
tags: ["prompt-library", "prompt-engineering", "productivity", "india", "it-professionals", "generative-ai"]
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
/* ── Library card ────────────────────────────────────────────── */
.mod-lib-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:16px 0}
.mod-lib-card-header{padding:10px 16px;display:flex;align-items:center;justify-content:space-between;gap:8px;border-bottom:1px solid #f0f0f0}
.mod-lib-card-title{font-size:13px;font-weight:700;color:#1565C0}
.mod-lib-card-tag{font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;background:#e3f2fd;color:#1565C0;border:1px solid #90caf9}
.mod-lib-card-body{padding:12px 16px}
.mod-lib-prompt{font-size:12px;font-family:monospace,sans-serif;background:#f5f5f4;border-radius:5px;padding:10px 12px;color:#333;line-height:1.7;white-space:pre-wrap;border-left:3px solid #1565C0;margin-bottom:8px}
.mod-lib-meta{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
.mod-lib-chip{font-size:10px;padding:2px 8px;border-radius:20px;background:#f5f5f4;color:#666;border:1px solid #e0e0e0}
/* ── Template format ─────────────────────────────────────────── */
.mod-template{background:#e8f0fe;border:1px solid #90caf9;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-template-title{font-size:12px;font-weight:700;color:#1565C0;letter-spacing:0.05em;margin-bottom:10px}
.mod-template-text{font-size:13px;font-family:monospace,sans-serif;color:#333;line-height:1.75;white-space:pre-wrap;background:#fff;border-radius:5px;padding:12px 14px;border:1px solid #c5d8f5}
/* ── Organisation options ────────────────────────────────────── */
.mod-org-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin:20px 0}
.mod-org-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-org-card-title{font-size:13px;font-weight:700;color:#1565C0;margin-bottom:6px}
.mod-org-card-text{font-size:12px;color:#444;line-height:1.6}
.mod-org-badge{display:inline-block;font-size:10px;font-weight:700;padding:2px 8px;border-radius:20px;margin-top:6px}
.mod-best-badge{background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7}
.mod-good-badge{background:#e3f2fd;color:#1565C0;border:1px solid #90caf9}
.mod-ok-badge{background:#f5f5f4;color:#666;border:1px solid #d3d1c7}
/* ── Role checklist ──────────────────────────────────────────── */
.mod-role-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin:20px 0}
.mod-role-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;border-left:3px solid #1565C0}
.mod-role-title{font-size:13px;font-weight:700;color:#1565C0;margin-bottom:8px}
.mod-role-list{margin:0;padding-left:16px}
.mod-role-list li{font-size:12px;color:#333;line-height:1.6;margin-bottom:3px}
/* ── Unit summary ────────────────────────────────────────────── */
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
@media(max-width:520px){.mod-org-grid{grid-template-columns:1fr}.mod-role-grid{grid-template-columns:1fr}.mod-unit-summary{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:55%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">11 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Module 1 ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-2">Module 2 ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-3">Module 3 — current</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-4">Module 4</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Module 5</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 3 &nbsp;›&nbsp; MODULE 4 OF 4</span>
    <h1 class="mod-title-inline">Building Your Personal Prompt Library</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 12 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Unit 3 Finale</span>
  </div>
</div>

This is the final module of Unit 3 — and the most directly actionable one. Over the past three modules you built prompts for developers, analysts, and managers. This module shows you how to collect, organise, and maintain all of them into a personal prompt library that compounds in value over time.

A prompt library is the single most practical career deliverable of this course. It is what separates someone who uses AI occasionally from someone who uses it systematically.

---

## What is a prompt library and why does it matter?

<div class="mod-keypoint">
<strong>A prompt library</strong> is a personal collection of tested, reusable prompts organised by task and role — your own reference system for getting consistent, high-quality AI output without writing prompts from scratch each time. Think of it as the AI equivalent of a code snippet library or a templates folder.
</div>

The value compounds over time. Your first 10 prompts save you 30 minutes a week. Your first 50 prompts save you 2–3 hours. Engineers and analysts who have been maintaining prompt libraries for a year report saving 8–10 hours a week — the equivalent of a part-time job.

There are three specific benefits beyond time saving:

**Consistency** — the same prompt produces the same quality output every time. You stop getting variable results because you stop writing variable prompts.

**Institutional knowledge** — your library captures what works for *your* specific context: your company, your clients, your tech stack, your role. Generic prompts from the internet do not have this. Yours do.

**Career portability** — your prompt library moves with you. When you change teams, companies, or roles, your library accelerates your ramp-up. It is a professional asset in the same way a portfolio is.

---

## The prompt library entry format

Every prompt in your library should follow a consistent entry format. This makes it searchable, maintainable, and shareable with your team.

<div class="mod-template">
<div class="mod-template-title">STANDARD PROMPT LIBRARY ENTRY FORMAT</div>
<div class="mod-template-text">## [Prompt Name — clear, specific]

**Category:** Developer / Analyst / Manager / Communication / Learning
**Tool:** ChatGPT / Claude / Gemini / Any
**Last tested:** [Month Year]
**Use case:** One sentence describing when to use this prompt

---

**Prompt:**
[The full prompt text, with [PLACEHOLDERS] for variable parts]

---

**Notes:**
- What this does well
- What to watch out for (common failure mode)
- Variations that work well

**Example output quality:** High / Medium (adjust with follow-up) / Low (starting point only)</div>
</div>

The `[PLACEHOLDERS]` pattern is the most important element. Instead of a prompt that is hardcoded to one project, you write a reusable template:

Instead of: *"You are a TCS delivery manager writing to Sarah Chen at UK Insurance about the API delay..."*

Write: *"You are a [ROLE] writing to [RECIPIENT] at [COMPANY] about [SITUATION]..."*

This turns a one-time prompt into a reusable template for every similar situation.

---

## Starter library — 10 prompts to begin with

Here are 10 fully written, ready-to-use prompts across the roles covered in Unit 3. Copy these directly into your library and customise the placeholders.

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">1. Universal Code Review</span>
  <span class="mod-lib-card-tag">Developer</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are a senior [LANGUAGE] developer reviewing code for a [COMPANY TYPE] production system.

Review this code and respond in exactly this format:
1. BUGS: Logic errors or runtime exceptions possible in production
2. PERFORMANCE: Inefficiencies — N+1 queries, unnecessary loops, memory issues
3. SECURITY: SQL injection, hardcoded secrets, unvalidated inputs
4. READABILITY: Naming, structure, missing documentation
5. VERDICT: Pass / Needs changes — one-line summary

Code:
[PASTE CODE HERE]</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude preferred</span>
    <span class="mod-lib-chip">Any language</span>
    <span class="mod-lib-chip">Pre-commit review</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">2. Debug Any Error</span>
  <span class="mod-lib-card-tag">Developer</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">I am debugging a [LANGUAGE/FRAMEWORK] issue.

Error: [PASTE EXACT ERROR OR TRACEBACK]

Code: [PASTE RELEVANT FUNCTION OR SECTION]

Context:
- Expected: [WHAT SHOULD HAPPEN]
- Actual: [WHAT IS HAPPENING]
- Already tried: [LIST ATTEMPTED FIXES]
- Stack: [LANGUAGE VERSION, FRAMEWORK, KEY LIBRARIES]

Identify the bug, explain why it occurs, and provide the corrected code.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude / ChatGPT</span>
    <span class="mod-lib-chip">Any language</span>
    <span class="mod-lib-chip">Save hours on debugging</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">3. SQL from Schema</span>
  <span class="mod-lib-card-tag">Analyst</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are a senior data analyst writing SQL for a [DATABASE TYPE] database.

Tables:
[PASTE YOUR SCHEMA — table names and column names]

Write a query that:
- [DESCRIBE WHAT YOU WANT IN PLAIN ENGLISH]
- [ADD FILTERS, DATE RANGES, AGGREGATIONS]
- Output format: [COLUMNS YOU WANT IN THE RESULT]

Include comments explaining each major section.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">ChatGPT preferred</span>
    <span class="mod-lib-chip">MySQL / PostgreSQL / BigQuery</span>
    <span class="mod-lib-chip">Always verify output</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">4. Data Insight Summary</span>
  <span class="mod-lib-card-tag">Analyst</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are a senior analyst writing for [AUDIENCE — e.g. "non-technical operations head"].

Here is the data: [PASTE TABLE OR KEY NUMBERS]

Write a [NUMBER]-paragraph summary.
- Each sentence must contain at least one number
- Tone: direct and factual, no corporate filler
- Paragraph 1: overall performance
- Paragraph 2: highlights and concerns
- Paragraph [LAST]: [NUMBER] specific recommendations

Under [WORD LIMIT] words.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude preferred</span>
    <span class="mod-lib-chip">Reports / dashboards</span>
    <span class="mod-lib-chip">Each sentence needs a number</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">5. Professional Email — Difficult Situation</span>
  <span class="mod-lib-card-tag">Manager / All roles</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are a [MY ROLE] at [MY COMPANY] writing a professional email.

To: [RECIPIENT NAME, TITLE, COMPANY]
Situation: [DESCRIBE THE SITUATION IN 2–3 SENTENCES]
Key message: [WHAT YOU NEED THEM TO KNOW OR DO]
Tone: [PROFESSIONAL + SPECIFIC TONE NOTE]
Length: Under [WORD LIMIT] words
Do NOT use: "as per", "please be advised", "we sincerely apologise", "going forward"
Include a clear subject line.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude preferred</span>
    <span class="mod-lib-chip">Client / internal / vendor</span>
    <span class="mod-lib-chip">Always add personal touch before sending</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">6. Meeting Notes → Summary</span>
  <span class="mod-lib-card-tag">Manager / All roles</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">Convert these rough meeting notes into a professional summary.

Notes: [PASTE RAW NOTES]

Format:
1. Meeting details (date, attendees, purpose — 1 line each)
2. Decisions made (bullet list)
3. Action items table: Owner | Action | Due date
4. Issues / risks flagged
5. Next steps

Keep language concise. Flag any ambiguous items with [NEEDS CLARIFICATION].</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude / ChatGPT</span>
    <span class="mod-lib-chip">Any meeting type</span>
    <span class="mod-lib-chip">[NEEDS CLARIFICATION] flag is key</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">7. Weekly Status Report</span>
  <span class="mod-lib-card-tag">Manager</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are a project manager writing a weekly status report.

Project: [PROJECT NAME AND BRIEF DESCRIPTION]
Audience: [CLIENT / MANAGEMENT — technical level]
Week ending: [DATE]
Overall status: [Red / Amber / Green — and why it changed if it did]

Input data:
- Milestones: [STATUS, % COMPLETE, PLANNED VS FORECAST DATE]
- Issues: [LIST WITH SEVERITY]
- Risks: [LIST WITH MITIGATION STATUS]
- Highlights: [THIS WEEK'S WINS]
- Next week focus: [TOP 3 PRIORITIES]

Generate report with: Executive summary (3 sentences), milestone table, issues and risks (RAG labels as text), highlights, next week focus.
Use RAG as text labels (Red/Amber/Green) — not HTML colours.
Under 400 words total.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude preferred</span>
    <span class="mod-lib-chip">Indian IT delivery</span>
    <span class="mod-lib-chip">RAG as text for Outlook compatibility</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">8. Concept Explainer for Interviews</span>
  <span class="mod-lib-card-tag">Learning / Placement prep</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are an experienced [DOMAIN] professor explaining a concept to a final-year engineering student preparing for a campus placement interview.

Explain: [CONCEPT]

Structure:
1. One-line definition (plain language, no jargon)
2. Real-world analogy relevant to Indian context
3. How it works — step by step (maximum 4 steps)
4. One concrete code or application example
5. Two likely interview questions on this topic with model answers
6. Common mistake candidates make when answering

Keep total length under 500 words.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Any tool</span>
    <span class="mod-lib-chip">Technical concepts</span>
    <span class="mod-lib-chip">Interview prep powerhouse</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">9. LinkedIn Post — Personal Story Style</span>
  <span class="mod-lib-card-tag">Personal branding</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">Write a LinkedIn post about [TOPIC / ACHIEVEMENT / LEARNING].

My context: [1–2 sentences about who you are and why this matters to you]

Style requirements:
- Opens with a hook (surprising fact, counterintuitive statement, or short story)
- 150–200 words
- Short paragraphs (2–3 sentences max each)
- Ends with a question or call to action
- Sounds personal, not corporate
- No hashtag spam (maximum 3 relevant hashtags at the end)

Do NOT start with "I am excited to share" or "I am thrilled to announce".</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude preferred</span>
    <span class="mod-lib-chip">Always edit to add your voice</span>
    <span class="mod-lib-chip">Test: would you actually post this?</span>
  </div>
</div>
</div>

<div class="mod-lib-card">
<div class="mod-lib-card-header">
  <span class="mod-lib-card-title">10. Devil's Advocate — Stress Test Any Plan</span>
  <span class="mod-lib-card-tag">Decision making</span>
</div>
<div class="mod-lib-card-body">
  <div class="mod-lib-prompt">You are a rigorous devil's advocate. Your job is to find every weakness in what I am about to share.

[PASTE YOUR PLAN, PROPOSAL, ARGUMENT, OR DECISION]

Identify:
1. The 3 strongest objections a sceptic would raise
2. Assumptions I am making that could be wrong
3. Edge cases or scenarios where this fails
4. What I would need to prove to make this airtight

Do NOT agree with me. Do NOT soften your critique. Be specific — general criticism is not useful.</div>
  <div class="mod-lib-meta">
    <span class="mod-lib-chip">Claude preferred</span>
    <span class="mod-lib-chip">Plans / proposals / decisions</span>
    <span class="mod-lib-chip">Use before any important submission</span>
  </div>
</div>
</div>

---

## Where to store your library

<div class="mod-org-grid">
  <div class="mod-org-card">
    <div class="mod-org-card-title">Notion</div>
    <div class="mod-org-card-text">Best overall option. Create a database with tags for Category, Tool, and Quality rating. Full-text search across all prompts. Accessible on mobile. Can share with teammates.</div>
    <span class="mod-org-badge mod-best-badge">Recommended</span>
  </div>
  <div class="mod-org-card">
    <div class="mod-org-card-title">Google Docs</div>
    <div class="mod-org-card-text">Simple and accessible anywhere. One doc per category (Developer, Analyst, Manager). Use headings for Ctrl+F search. Easiest to start with if you already use Google Workspace.</div>
    <span class="mod-org-badge mod-good-badge">Good start</span>
  </div>
  <div class="mod-org-card">
    <div class="mod-org-card-title">Obsidian / Markdown</div>
    <div class="mod-org-card-text">Best for technical users. Local storage, full control, works offline. Tag system for filtering. Can sync via iCloud or Dropbox. Ideal if you already use Obsidian for notes.</div>
    <span class="mod-org-badge mod-good-badge">For power users</span>
  </div>
</div>

Avoid storing prompts in chat history. Chat history is not searchable, not organised, and gets lost. Your library needs to be a document you intentionally maintain.

---

## Prompts by role — what your library should contain

Use this checklist to identify gaps in your library. Aim to have at least one tested prompt per category before Unit 5.

<div class="mod-role-grid">
  <div class="mod-role-card">
    <div class="mod-role-title">&#128187; Developer prompts</div>
    <ul class="mod-role-list">
      <li>Code generation (your stack)</li>
      <li>Universal debug template</li>
      <li>Code review (pre-commit)</li>
      <li>Unit test generation</li>
      <li>Docstring / README generation</li>
      <li>SQL generation (your DB)</li>
    </ul>
  </div>
  <div class="mod-role-card">
    <div class="mod-role-title">&#128200; Analyst prompts</div>
    <ul class="mod-role-list">
      <li>SQL from schema (your tables)</li>
      <li>Data insight summary</li>
      <li>Anomaly identification</li>
      <li>Python analysis boilerplate</li>
      <li>Report narrative template</li>
      <li>Slide content from findings</li>
    </ul>
  </div>
  <div class="mod-role-card">
    <div class="mod-role-title">&#128203; Manager / communication prompts</div>
    <ul class="mod-role-list">
      <li>Difficult email template</li>
      <li>Client status update</li>
      <li>Meeting notes → summary</li>
      <li>Weekly status report</li>
      <li>Escalation email</li>
      <li>QBR / presentation outline</li>
    </ul>
  </div>
  <div class="mod-role-card">
    <div class="mod-role-title">&#127891; Learning / career prompts</div>
    <ul class="mod-role-list">
      <li>Concept explainer for interviews</li>
      <li>Mock interview question generator</li>
      <li>LinkedIn post (your style)</li>
      <li>Resume bullet rewriter</li>
      <li>Devil's advocate for plans</li>
      <li>Company AI research template</li>
    </ul>
  </div>
</div>

---

## How to grow and maintain your library

A prompt library that is not maintained quickly becomes a graveyard of prompts you do not trust. Three habits keep it alive:

**1. Add immediately, refine later.** When a prompt works well — even once — add it to the library immediately with a note on what it did well. You can refine the wording later. The barrier to entry should be as low as possible.

**2. Rate every prompt after testing.** Use a simple quality rating: High (use as-is), Medium (use with one follow-up), Low (starting point only). Prompts that consistently land at Low should be rewritten or deleted.

**3. Review and update quarterly.** AI tools change fast. A prompt that worked best in Claude Sonnet 3.5 may work better in ChatGPT after a model update. Review your library every three months, test your top 10 prompts, and update the "Last tested" date and tool recommendation.

---

## Module 3 — What you have learned

<div class="mod-unit-summary">
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 3.1</div>
    <div class="mod-unit-card-title">GenAI for Developers</div>
    <div class="mod-unit-card-summary">Code generation, debugging, code review, test writing, documentation. Read every line before committing. Specificity produces production-ready output.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 3.2</div>
    <div class="mod-unit-card-title">GenAI for Analysts</div>
    <div class="mod-unit-card-summary">SQL from schema, data summarisation, Python analysis, report narratives. AI writes the draft — you provide the business judgement. Verify every query.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 3.3</div>
    <div class="mod-unit-card-title">GenAI for Managers</div>
    <div class="mod-unit-card-summary">Professional emails, meeting summaries, status reports, presentations. Context and relationship define quality. Always add one personal touch before sending.</div>
  </div>
  <div class="mod-unit-card">
    <div class="mod-unit-card-num">MODULE 3.4</div>
    <div class="mod-unit-card-title">Your Prompt Library</div>
    <div class="mod-unit-card-summary">A personal, organised, maintained collection of tested prompts. The most compounding career asset from this course. Starts today, grows with every task.</div>
  </div>
</div>

Module 4 goes deeper — into RAG, AI agents, and automation workflows. The prompt library you build today will be extended with advanced technique prompts after Module 4.

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 3.4</div>
  <ol>
    <li><strong>Use placeholders, not hardcoded prompts</strong> — a prompt with [ROLE], [COMPANY], and [SITUATION] placeholders is 10x more useful than one written for a single occasion. The 30 seconds it takes to generalise a prompt pays back every time you reuse it.</li>
    <li><strong>Store it where you will actually find it</strong> — a prompt library in a document you open daily is worth more than a perfect system you never use. Start with Google Docs if that is what you already use. Migrate to Notion when you outgrow it.</li>
    <li><strong>Your library compounds</strong> — 10 prompts save 30 minutes a week. 50 prompts save 2–3 hours. 100 prompts save half a workday. The professionals getting the most value from AI in 2026 are not using better tools — they are using the same tools with a personal system built over months of deliberate practice.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-34">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 3.4 — Build Your 10-Prompt Starter Library</h3>
  </div>
  <p>This is the Module 3 capstone assignment. It consolidates everything from Modules 3.1, 3.2, and 3.3 into a single deliverable you will actually use.</p>
  <ol>
    <li><strong>Choose your storage tool</strong> — Notion, Google Docs, or Obsidian. Create a new document or database called "My Prompt Library." Set up the standard entry format from this module.</li>
    <li><strong>Add the 10 starter prompts from this module</strong> — customise every [PLACEHOLDER] for your specific context: your role, your tech stack, your target company, your domain. A prompt that still has generic placeholders is not in your library — it is a template.</li>
    <li><strong>Add your best prompts from Modules 3.1, 3.2, and 3.3 assignments</strong> — each assignment asked you to save prompts in your AI Learning Journal. Transfer the best ones to your library using the standard format. Test each one and rate it High / Medium / Low.</li>
    <li><strong>Identify 3 gaps</strong> — using the role checklist in this module, identify 3 prompt categories you need but do not yet have. Write those prompts from scratch, test them, and add them to the library.</li>
    <li><strong>Target: 15 prompts minimum by the end of Module 3.</strong> By Module 5, you will extend this to 25+ prompts covering your full workflow.</li>
  </ol>
  <p>Your prompt library is a living document. The most important habit is adding to it immediately when something works — before the next meeting, the next task, the next distraction takes over. Start that habit today with this assignment.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit3/module-3-3-genai-for-managers/">&#8592; Module 3.3: GenAI for Managers</a>
  <a class="mod-nav-next" href="/courses/genai/unit4/module-4-1-rag-explained/">Unit 4: Advanced Techniques &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and references</summary>
  <table>
    <thead><tr><th>Claim / Component</th><th>Source / Note</th></tr></thead>
    <tbody>
      <tr><td>Prompt library value compounding — 10 prompts → 50 prompts → time savings</td><td>Synthesised from Lakera Prompt Engineering Guide 2026; promptbuilder.cc Best Practices 2026</td></tr>
      <tr><td>Notion recommended for prompt libraries; Obsidian for power users</td><td>Community consensus from prompt engineering practitioner communities 2025–2026</td></tr>
      <tr><td>10 starter prompts — all original, tested against real Indian IT work contexts</td><td>Original content — CC0, no attribution required</td></tr>
    </tbody>
  </table>
</details>

</div>
