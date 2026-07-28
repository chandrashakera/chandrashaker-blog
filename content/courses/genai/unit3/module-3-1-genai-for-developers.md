---
title: "Module 3.1: GenAI for Developers — Code Generation, Debugging, and Documentation"
description: "Practical guide to using GitHub Copilot, Claude, and ChatGPT for code generation, debugging, test writing, and documentation — with real examples for Indian IT developers and freshers."
weight: 1
sidebar: false
mainroad_aside: false
tags: ["github-copilot", "code-generation", "debugging", "documentation", "india", "developers", "generative-ai"]
---

<style>
/* ── Module progress bar ─────────────────────────────────────── */
.mod-progress-wrap{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:12px 16px;margin-bottom:20px}
.mod-progress-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;flex-wrap:wrap;gap:6px}
.mod-progress-title{font-size:12px;font-weight:700;color:#555;letter-spacing:0.04em}
.mod-progress-label{font-size:12px;color:#1565C0;font-weight:600}
.mod-progress-bg{height:6px;background:#e0e0e0;border-radius:3px;margin-bottom:10px}
.mod-progress-fill{height:6px;border-radius:3px;background:#FF8C00;transition:width 0.3s ease}
.mod-progress-units{display:flex;gap:6px;flex-wrap:wrap}
.mod-progress-unit{font-size:11px;padding:3px 10px;border-radius:20px;text-decoration:none;font-weight:500;border:1px solid}
.mod-progress-unit.done{background:#e8f5e9;color:#2e7d32;border-color:#a5d6a7}
.mod-progress-unit.current{background:#1565C0;color:#fff;border-color:#1565C0}
.mod-progress-unit.upcoming{background:#f5f5f4;color:#999;border-color:#e0e0e0}
/* ── Module header bar ───────────────────────────────────────── */
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
/* ── Use case sections ───────────────────────────────────────── */
.mod-usecase{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:24px 0;border-left:4px solid #1565C0}
.mod-usecase-header{padding:12px 16px;background:#f5f8ff;border-bottom:1px solid #e0e0e0;display:flex;align-items:center;gap:10px}
.mod-usecase-icon{font-size:16px;flex-shrink:0}
.mod-usecase-title{font-size:15px;font-weight:700;color:#1565C0;margin:0}
.mod-usecase-body{padding:16px}
/* ── Prompt boxes ────────────────────────────────────────────── */
.mod-prompt-box{border-radius:8px;overflow:hidden;margin:12px 0;border:1px solid}
.mod-prompt-label{padding:7px 13px;font-size:11px;font-weight:700;letter-spacing:0.05em}
.mod-prompt-text{padding:12px 14px;font-size:13px;font-family:monospace,sans-serif;line-height:1.75;white-space:pre-wrap;word-break:break-word;color:#111111}
.mod-prompt-note{padding:8px 13px;font-size:12px;color:#555;border-top:1px solid;line-height:1.5;background:#fafafa}
.mod-prompt-note strong{color:#1565C0}
.mod-pb-blue .mod-prompt-label{background:#e3f2fd;color:#1565C0;border-bottom:1px solid #90caf9}
.mod-pb-blue{border-color:#90caf9}
.mod-pb-blue .mod-prompt-text{background:#f5f9ff}
.mod-pb-blue .mod-prompt-note{border-color:#e3f2fd}
.mod-pb-green .mod-prompt-label{background:#e8f5e9;color:#2e7d32;border-bottom:1px solid #a5d6a7}
.mod-pb-green{border-color:#a5d6a7}
.mod-pb-green .mod-prompt-text{background:#f5fff6}
.mod-pb-green .mod-prompt-note{border-color:#e8f5e9}
.mod-pb-orange .mod-prompt-label{background:#fff8e1;color:#e65c00;border-bottom:1px solid #FFB300}
.mod-pb-orange{border-color:#FFB300}
.mod-pb-orange .mod-prompt-text{background:#fffdf0}
.mod-pb-orange .mod-prompt-note{border-color:#fff8e1}
.mod-pb-purple .mod-prompt-label{background:#f3e5f5;color:#6a1b9a;border-bottom:1px solid #ce93d8}
.mod-pb-purple{border-color:#ce93d8}
.mod-pb-purple .mod-prompt-text{background:#fdf5ff}
.mod-pb-purple .mod-prompt-note{border-color:#f3e5f5}
/* ── Tool recommendation row ─────────────────────────────────── */
.mod-tool-row{display:flex;gap:10px;flex-wrap:wrap;margin:12px 0}
.mod-tool-badge{display:inline-flex;align-items:center;gap:6px;font-size:12px;font-weight:600;padding:5px 12px;border-radius:20px;border:1px solid}
.mod-tool-best{background:#e8f5e9;color:#2e7d32;border-color:#a5d6a7}
.mod-tool-good{background:#e3f2fd;color:#1565C0;border-color:#90caf9}
.mod-tool-ok{background:#f5f5f4;color:#666;border-color:#d3d1c7}
/* ── Workflow steps ──────────────────────────────────────────── */
.mod-workflow{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-workflow-title{font-size:11px;font-weight:700;color:#555;letter-spacing:0.05em;margin-bottom:12px}
.mod-workflow-step{display:flex;align-items:flex-start;gap:12px;padding:9px 0;border-bottom:1px solid #f0f0f0}
.mod-workflow-step:last-child{border-bottom:none}
.mod-workflow-num{width:24px;height:24px;border-radius:50%;background:#1565C0;color:#fff;font-size:12px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px}
.mod-workflow-text{font-size:13px;color:#111111;line-height:1.5;flex:1}
.mod-workflow-text strong{color:#111111}
/* ── Warning ─────────────────────────────────────────────────── */
.mod-warning{background:#ffeaea;border-left:4px solid #c62828;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a0000;line-height:1.6}
.mod-warning strong{color:#c62828}
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
@media(max-width:520px){.mod-stat-grid{grid-template-columns:1fr 1fr}.mod-tool-row{gap:6px}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:40%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">8 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Understanding GenAI ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-2">Prompt Engineering ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-3">GenAI for Your Job</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-4">Advanced Techniques</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Career & India</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 3 &nbsp;›&nbsp; MODULE 1 OF 4</span>
    <h1 class="mod-title-inline">GenAI for Developers — Code Generation, Debugging, and Documentation</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 15 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Hands-on examples</span>
  </div>
</div>

Welcome to Unit 3. You now have the prompt engineering skills from Unit 2. This unit is about applying those skills to your actual work — starting with the role most of you are entering or preparing for: software development.

This module is not theoretical. Every technique here maps to a task you will encounter in your first week at TCS, Infosys, Wipro, HCL, or any Indian IT company — or in your current academic projects if you are still in college.

---

## Why AI is now a baseline skill for developers

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">55%</div>
    <div class="mod-stat-card-label">faster task completion by developers using GitHub Copilot — tested across 4,800 developers</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">46%</div>
    <div class="mod-stat-card-label">of all code written by active Copilot users is now AI-generated — up from 27% in 2022</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">84%</div>
    <div class="mod-stat-card-label">of developers use or plan to use AI tools in 2026 — up from 76% the previous year</div>
  </div>
</div>

At Infosys, 28 million lines of code were generated using AI tools in FY26. At Accenture, teams using Copilot saw pull request time drop from 9.6 days to 2.4 days — a 4x acceleration. Code review turnaround improved by 67%.

This is not a future prediction. It is the current working environment at every major Indian IT company. Developers who use AI tools effectively are completing the same work in half the time. Those who do not are working twice as hard to keep up.

<div class="mod-keypoint">
<strong>The critical nuance:</strong> Only 29–46% of developers trust AI-generated code without review. The fastest developers are not the ones who accept AI output blindly — they are the ones who use AI to generate a solid first draft, then review and refine quickly. This review skill is what this module teaches.
</div>

---

## Use case 1 — Code generation

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#9997;</span>
  <div class="mod-usecase-title">Writing new code from scratch</div>
</div>
<div class="mod-usecase-body">

<p>The most common developer use case. Give the AI enough context about your stack, constraints, and requirements and it will produce a working first draft in seconds. The key is specificity — the more precisely you describe what you need, the less cleanup you do afterwards.</p>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — Django REST API endpoint for Indian fintech</div>
  <div class="mod-prompt-text">You are a senior Django developer building a fintech REST API.

Write a Django REST Framework view for a loan eligibility check endpoint.

Requirements:
- Endpoint: POST /api/v1/loan/check/
- Input: JSON with fields: user_id (int), monthly_income (float), existing_emi (float), requested_amount (float), tenure_months (int)
- Logic: Debt-to-income ratio check — if (existing_emi + proposed_emi) > 40% of monthly_income, reject
- Proposed EMI formula: P * r * (1+r)^n / ((1+r)^n - 1) where r = 0.01 (1% monthly rate)
- Output: JSON with fields: eligible (bool), reason (str), max_eligible_amount (float)
- Error handling: validate all input fields, return 400 for missing/invalid data
- Include serializer and URL config

Stack: Django 4.2, DRF 3.15, Python 3.11</div>
  <div class="mod-prompt-note"><strong>What makes this prompt work:</strong> Specific stack versions, exact field names, the business logic written out explicitly (DTI ratio, EMI formula), error handling requirements, and output format defined. The model produces working, production-ready code — not a skeleton that needs rewriting.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude Sonnet — best for complex logic</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — good, strong DRF knowledge</span>
  <span class="mod-tool-badge mod-tool-ok">GitHub Copilot — best in-editor, weaker for full features</span>
</div>

<p style="margin-top:12px">For simpler functions — utility methods, data transformations, standard CRUD operations — GitHub Copilot inside VS Code is the fastest tool. It auto-completes as you type, with no prompt needed. For complex features like the one above, Claude or ChatGPT with a detailed prompt is more reliable.</p>

</div>
</div>

---

## Use case 2 — Debugging

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128030;</span>
  <div class="mod-usecase-title">Finding and fixing bugs</div>
</div>
<div class="mod-usecase-body">

<p>Debugging is where AI saves the most time for junior developers. A bug that takes 45 minutes to trace manually often takes under 2 minutes with AI — if you provide enough context. The three things that matter: the error message, the code, and what you expected to happen.</p>

<div class="mod-prompt-box mod-pb-green">
  <div class="mod-prompt-label">EXAMPLE — Python KeyError debugging</div>
  <div class="mod-prompt-text">I am getting a KeyError in my Django view. Here is the error traceback and the relevant code:

Error:
KeyError at /api/v1/portfolio/summary/
'total_invested'
File "/app/views/portfolio.py", line 47, in get_portfolio_summary
    return Response({'invested': data['total_invested']})

My code (views/portfolio.py, lines 40-55):
def get_portfolio_summary(request):
    user_id = request.user.id
    holdings = StockHolding.objects.filter(user_id=user_id)
    data = {}
    for holding in holdings:
        data['total_value'] = data.get('total_value', 0) + holding.current_value
        data['total_invested'] = data.get('total_invested', 0) + holding.purchase_price
    serializer = PortfolioSerializer(data)
    return Response({'invested': data['total_invested']})

Expected: Return the total invested amount for the user.
Actual: KeyError on 'total_invested' even though I set it in the loop.

Identify the bug, explain why it occurs, and provide the fix.</div>
  <div class="mod-prompt-note"><strong>What makes this prompt work:</strong> Full traceback, exact line reference, the relevant code block, expected vs actual behaviour. The model can immediately identify that <code>data['total_invested']</code> fails when <code>holdings</code> is an empty queryset (the loop never runs). Without the code and context, it would guess.</div>
</div>

<div class="mod-prompt-box mod-pb-green">
  <div class="mod-prompt-label">TEMPLATE — Universal debugging prompt</div>
  <div class="mod-prompt-text">I am debugging a [language/framework] issue.

Error message:
[paste exact error or traceback]

Relevant code:
[paste the function or section where the error occurs]

Context:
- What I expected to happen: [describe]
- What actually happens: [describe]
- What I have already tried: [list any attempted fixes]

Stack: [language version, framework version, relevant libraries]

Identify the bug, explain why it occurs, and provide the corrected code.</div>
  <div class="mod-prompt-note"><strong>Save this template</strong> in your AI Learning Journal. It works for any language — Python, Java, JavaScript, C++. The "what I have already tried" section prevents the model from suggesting things you have already ruled out.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude Sonnet — lowest hallucination on code</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — fast, strong on common frameworks</span>
  <span class="mod-tool-badge mod-tool-good">GitHub Copilot Chat — works in-editor on open files</span>
</div>

</div>
</div>

---

## Use case 3 — Code review and improvement

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128269;</span>
  <div class="mod-usecase-title">Reviewing existing code for quality and issues</div>
</div>
<div class="mod-usecase-body">

<p>In Indian IT service delivery, code review is a core part of every sprint. AI can act as a first-pass reviewer — catching issues before a senior engineer reviews it. This reduces review cycles, improves your code quality, and signals professionalism to your team lead.</p>

<div class="mod-prompt-box mod-pb-orange">
  <div class="mod-prompt-label">EXAMPLE — Pre-review self-check</div>
  <div class="mod-prompt-text">You are a senior software engineer reviewing code before it goes to production at an Indian IT services company.

Review this Python function and check for the following — respond in this exact format:

1. BUGS: List any logic errors or exceptions that could occur in production
2. PERFORMANCE: Identify any inefficiencies (N+1 queries, unnecessary loops, memory issues)
3. SECURITY: Flag any security concerns (SQL injection, hardcoded secrets, unsafe inputs)
4. READABILITY: Note any naming, structure, or documentation issues
5. VERDICT: Pass / Needs changes — with one-line summary

Code to review:
def get_user_transactions(user_email):
    conn = sqlite3.connect('transactions.db')
    cursor = conn.cursor()
    query = "SELECT * FROM transactions WHERE email = '" + user_email + "'"
    cursor.execute(query)
    results = cursor.fetchall()
    return results</div>
  <div class="mod-prompt-note"><strong>The structured output format is critical here.</strong> Without specifying the exact sections, the model gives a prose review that is hard to act on. With this format, you get a checklist you can work through systematically. The model will correctly flag the SQL injection vulnerability in the <code>+</code> string concatenation.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude Sonnet — most thorough code review</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — fast, catches common issues well</span>
</div>

</div>
</div>

---

## Use case 4 — Writing tests

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#9989;</span>
  <div class="mod-usecase-title">Generating unit tests and test cases</div>
</div>
<div class="mod-usecase-body">

<p>Test writing is the task developers hate most and AI handles best. Given a function, the model can generate unit tests covering normal cases, edge cases, and error conditions in seconds. At Wipro, 60+ GenAI use cases exist for software testing alone.</p>

<div class="mod-prompt-box mod-pb-purple">
  <div class="mod-prompt-label">EXAMPLE — pytest unit tests for a validation function</div>
  <div class="mod-prompt-text">You are a senior QA engineer writing pytest unit tests.

Write comprehensive unit tests for this Python function:

def validate_pan_number(pan: str) -> dict:
    """Validates Indian PAN card number format.
    Format: 5 letters + 4 digits + 1 letter (e.g., ABCDE1234F)
    Returns: {'valid': bool, 'error': str or None}
    """
    import re
    if not pan:
        return {'valid': False, 'error': 'PAN number is required'}
    pan = pan.upper().strip()
    pattern = r'^[A-Z]{5}[0-9]{4}[A-Z]{1}$'
    if re.match(pattern, pan):
        return {'valid': True, 'error': None}
    return {'valid': False, 'error': 'Invalid PAN format'}

Cover these test categories:
1. Valid PAN numbers (at least 3 examples)
2. Invalid format cases (wrong length, wrong pattern, special characters)
3. Edge cases (empty string, None, whitespace, lowercase input)
4. Boundary cases (numbers where letters expected, vice versa)

Use pytest. Use descriptive test function names. Include docstrings on each test.</div>
  <div class="mod-prompt-note"><strong>India-specific context matters here.</strong> PAN validation is a real task in every Indian fintech and HR system. By using a domain-relevant example, you get tests that are immediately usable — not generic tests you have to adapt. The explicit test categories prevent the model from writing 5 similar valid cases and missing all the edge cases.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude Sonnet — best test coverage, fewest missing cases</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — good for common testing frameworks</span>
  <span class="mod-tool-badge mod-tool-ok">GitHub Copilot — autocomplete only, no coverage planning</span>
</div>

</div>
</div>

---

## Use case 5 — Writing documentation

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128196;</span>
  <div class="mod-usecase-title">Docstrings, README files, API documentation</div>
</div>
<div class="mod-usecase-body">

<p>Documentation is the task that almost never gets done properly and AI does extremely well. A well-prompted model will generate docstrings, README files, and API documentation that are consistent, complete, and formatted correctly — saving hours of work per sprint.</p>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — Docstring generation</div>
  <div class="mod-prompt-text">Generate a comprehensive Google-style docstring for this Python function.

Include: summary line, Args section with types and descriptions, Returns section with type and description, Raises section for all possible exceptions, and one usage Example.

def calculate_sip_returns(monthly_investment: float,
                           annual_rate: float,
                           years: int) -> dict:
    months = years * 12
    monthly_rate = annual_rate / 100 / 12
    if monthly_rate == 0:
        total_value = monthly_investment * months
    else:
        total_value = monthly_investment * (
            ((1 + monthly_rate) ** months - 1) / monthly_rate
        ) * (1 + monthly_rate)
    total_invested = monthly_investment * months
    total_returns = total_value - total_invested
    return {
        'total_invested': round(total_invested, 2),
        'total_value': round(total_value, 2),
        'total_returns': round(total_returns, 2),
        'return_percentage': round((total_returns / total_invested) * 100, 2)
    }</div>
  <div class="mod-prompt-note"><strong>Specify the docstring format explicitly</strong> — Google style, NumPy style, or reStructuredText. Each looks different. If your team uses a specific format, say so. The SIP (Systematic Investment Plan) context makes this immediately relevant to Indian fintech work.</div>
</div>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — README generation for a GitHub project</div>
  <div class="mod-prompt-text">Write a professional README.md for my GitHub project.

Project: A FastAPI backend for an Indian stock portfolio tracker
Stack: Python 3.11, FastAPI, PostgreSQL, Redis, Docker
Features: User authentication (JWT), portfolio CRUD, real-time NSE price updates via WebSocket, profit/loss calculation, tax liability estimation (LTCG/STCG)

Include these sections in order:
1. Project title and one-line description
2. Features list (bullet points)
3. Tech stack table
4. Prerequisites
5. Installation steps (numbered, Docker-first approach)
6. API endpoints table (method, endpoint, description, auth required)
7. Environment variables table
8. Contributing guide (2–3 sentences)
9. Licence (MIT)

Use GitHub Markdown formatting. Keep language professional but not corporate.</div>
  <div class="mod-prompt-note"><strong>A well-written README dramatically improves your GitHub profile</strong> for placements. Recruiters at TCS, Infosys, and product companies specifically look at GitHub README quality as a signal of professional communication skills. This prompt produces a complete README in 30 seconds.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude Sonnet — most natural writing, least AI-sounding</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — good for technical docs and READMEs</span>
</div>

</div>
</div>

---

## The AI-assisted development workflow

Here is how the best developers at Indian IT companies structure their AI usage — not using it for everything, but using it at the right points in the workflow:

<div class="mod-workflow">
<div class="mod-workflow-title">RECOMMENDED WORKFLOW — AI-ASSISTED DEVELOPMENT</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">1</div>
  <div class="mod-workflow-text"><strong>Understand the requirement first, manually.</strong> Before touching AI, read the ticket/story and make sure you understand the business logic. AI cannot understand requirements it has not seen.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">2</div>
  <div class="mod-workflow-text"><strong>Use GitHub Copilot for boilerplate and standard patterns.</strong> CRUD operations, serializers, standard middleware, common utility functions — let Copilot autocomplete in the editor. Accept or reject each suggestion.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">3</div>
  <div class="mod-workflow-text"><strong>Use Claude or ChatGPT for complex logic.</strong> Business rules, algorithms, non-standard implementations — write a detailed prompt with context, stack, constraints, and expected output. Review the generated code thoroughly before using it.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">4</div>
  <div class="mod-workflow-text"><strong>Use AI for the first pass of tests.</strong> After writing your feature, prompt Claude to generate tests covering normal, edge, and error cases. Add any domain-specific cases the model missed. Never skip manual review of tests.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">5</div>
  <div class="mod-workflow-text"><strong>Use AI for pre-review self-check.</strong> Before submitting for code review, run your code through the structured review prompt above. Fix what it finds. Your senior engineer will notice the improvement.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">6</div>
  <div class="mod-workflow-text"><strong>Use AI for documentation last.</strong> Once the code is finalised, generate docstrings, README updates, and API documentation. Documentation generated after finalisation is more accurate than documentation generated during development.</div>
</div>
</div>

---

## What to never do with AI-generated code

<div class="mod-warning">
<strong>Three absolute rules for professional AI code use:</strong><br><br>
1. <strong>Never commit AI-generated code without reading every line.</strong> The 88% retention rate means 12% of Copilot suggestions contain errors. In a 500-line feature, that is 60 lines that need fixing. Blindly committing AI code is how bugs reach production.<br><br>
2. <strong>Never use AI-generated code involving security, authentication, or financial calculations without a senior review.</strong> The SQL injection example above would pass a casual review. Security vulnerabilities in AI-generated code are one of the fastest-growing categories of production incidents in 2026.<br><br>
3. <strong>Never paste client code or proprietary business logic into a consumer AI tool</strong> (ChatGPT free, Claude free). Use your company's approved enterprise AI tool for anything confidential. If no enterprise tool is available, describe the problem abstractly without pasting actual client code.
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 3.1</div>
  <ol>
    <li><strong>AI generates a first draft, not a final product</strong> — 46% of code is AI-generated but 12% of suggestions contain errors. The skill is fast, accurate review — not blind acceptance. Read every line before committing.</li>
    <li><strong>Specificity is the difference between useful and generic code</strong> — include your exact stack versions, field names, business logic, error handling requirements, and output format in every code generation prompt. Vague prompts produce skeleton code you have to rewrite anyway.</li>
    <li><strong>Use the right tool for the right task</strong> — Copilot for in-editor boilerplate, Claude for complex logic and thorough code review, ChatGPT for documentation and general-purpose tasks. No single tool is best at everything.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-31">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 3.1 — Apply AI to a Real Development Task</h3>
  </div>
  <p>This assignment builds your prompt library for development work. Each task should take 15–20 minutes.</p>
  <ol>
    <li><strong>Code generation:</strong> Pick a function or feature you need to write for a current project, assignment, or practice problem. Write a detailed prompt using the six-component structure. Include your exact stack, requirements, and constraints. Test the output and note what you had to fix.</li>
    <li><strong>Debugging:</strong> Take a bug you are currently stuck on (or have been stuck on recently). Use the universal debugging template from this module. Paste the error, code, and context. Note how long it would have taken you to find this manually versus with AI.</li>
    <li><strong>Code review:</strong> Take any function you have written in the past week — assignment, project, or practice code. Run it through the structured review prompt. Note what the model finds that you did not catch yourself.</li>
    <li><strong>Save all three prompts in your AI Learning Journal</strong> under "Module 3.1 — Developer Prompts." These form the start of your developer prompt library, which you will build out in Module 3.4.</li>
  </ol>
  <p>After this assignment you will have concrete evidence of what AI can and cannot do for your development work — calibrated to your actual stack, not a generic tutorial example.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — CHANDRAS EDU (chandrashaker.in)</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — CHANDRAS EDU (chandrashaker.in)</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit2/module-2-4-common-prompt-mistakes/">&#8592; Module 2.4: Common Prompt Mistakes</a>
  <a class="mod-nav-next" href="/courses/genai/unit3/module-3-2-genai-for-analysts/">Module 3.2: GenAI for Analysts &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>Developers complete tasks 55% faster with GitHub Copilot — tested with 4,800 developers</td><td>Quantumrun / companieshistory.com GitHub Copilot Statistics 2026</td></tr>
      <tr><td>GitHub Copilot generates 46% of all code written by active users; 88% code retention rate</td><td>aboutchromebooks.com / getpanto.ai GitHub Copilot Statistics Jan 2026</td></tr>
      <tr><td>84% of developers use or plan to use AI tools in 2026</td><td>index.dev Developer Productivity Statistics with AI Tools 2026</td></tr>
      <tr><td>Only 29–46% of developers trust AI-generated code without review; 46–68% report quality issues</td><td>index.dev Developer Productivity Statistics with AI Tools 2026</td></tr>
      <tr><td>Accenture: pull request time dropped from 9.6 to 2.4 days; 67% reduction in code review turnaround</td><td>wearetenet.com GitHub Copilot Usage Data Statistics 2025</td></tr>
      <tr><td>Infosys 28 million lines of AI-generated code</td><td>Infosys FY26 earnings commentary</td></tr>
      <tr><td>Wipro 60+ GenAI use cases for software testing</td><td>Wipro 6-K SEC filing FY2025</td></tr>
    </tbody>
  </table>
</details>

</div>
