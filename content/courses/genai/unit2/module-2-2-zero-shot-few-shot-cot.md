---
title: "Module 2.2: Zero-Shot, Few-Shot, and Chain-of-Thought Prompting"
description: "Master the three most powerful prompt engineering techniques — zero-shot, few-shot, and chain-of-thought — with practical examples for Indian students and IT professionals."
weight: 2
sidebar: false
tags: ["prompt-engineering", "zero-shot", "few-shot", "chain-of-thought", "india", "generative-ai"]
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
/* ── Technique cards ─────────────────────────────────────────── */
.mod-technique{border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:24px 0}
.mod-technique-header{padding:13px 18px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:8px}
.mod-technique-name{font-size:16px;font-weight:700;color:#fff;margin:0}
.mod-technique-tag{font-size:11px;color:rgba(255,255,255,0.9);background:rgba(255,255,255,0.18);padding:3px 10px;border-radius:20px}
.mod-technique-body{padding:16px 18px;background:#fff}
.mod-technique-desc{font-size:14px;color:#111111;line-height:1.75;margin:0 0 14px}
/* ── Prompt example boxes ────────────────────────────────────── */
.mod-prompt-box{border-radius:8px;overflow:hidden;margin:12px 0;border:1px solid}
.mod-prompt-label{padding:7px 13px;font-size:11px;font-weight:700;letter-spacing:0.05em}
.mod-prompt-text{padding:12px 14px;font-size:13px;font-family:monospace,sans-serif;line-height:1.75;white-space:pre-wrap;word-break:break-word;color:#111111}
.mod-prompt-result{padding:10px 14px;font-size:13px;line-height:1.7;border-top:1px solid;color:#333}
.mod-prompt-result-label{font-size:10px;font-weight:700;letter-spacing:0.05em;color:#888;margin-bottom:4px}
.mod-pb-blue .mod-prompt-label{background:#e3f2fd;color:#1565C0}
.mod-pb-blue{border-color:#90caf9}
.mod-pb-blue .mod-prompt-text{background:#f5f9ff}
.mod-pb-blue .mod-prompt-result{background:#f0f6ff;border-color:#90caf9}
.mod-pb-green .mod-prompt-label{background:#e8f5e9;color:#2e7d32}
.mod-pb-green{border-color:#a5d6a7}
.mod-pb-green .mod-prompt-text{background:#f5fff6}
.mod-pb-green .mod-prompt-result{background:#f0fff2;border-color:#a5d6a7}
.mod-pb-orange .mod-prompt-label{background:#fff8e1;color:#e65c00}
.mod-pb-orange{border-color:#FFB300}
.mod-pb-orange .mod-prompt-text{background:#fffdf0}
.mod-pb-orange .mod-prompt-result{background:#fff9e6;border-color:#FFB300}
/* ── Comparison grid ─────────────────────────────────────────── */
.mod-compare-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:20px 0}
.mod-compare-card{border-radius:8px;overflow:hidden;border:1px solid #e0e0e0}
.mod-compare-header{padding:10px 14px;font-size:13px;font-weight:700;text-align:center}
.mod-compare-body{padding:12px 14px}
.mod-compare-body li{font-size:12px;color:#333;line-height:1.6;margin-bottom:4px}
.mod-compare-body ul{margin:0;padding-left:14px}
.mod-compare-when{padding:8px 14px;font-size:12px;font-weight:600;text-align:center;border-top:1px solid #f0f0f0}
/* ── Decision flowchart ──────────────────────────────────────── */
.mod-decision{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-decision-title{font-size:11px;font-weight:700;color:#555;letter-spacing:0.05em;margin-bottom:12px}
.mod-decision-row{display:flex;align-items:flex-start;gap:12px;padding:8px 0;border-bottom:1px solid #f0f0f0}
.mod-decision-row:last-child{border-bottom:none}
.mod-decision-q{font-size:13px;font-weight:600;color:#1565C0;flex:1.2;line-height:1.4}
.mod-decision-arrow{font-size:14px;color:#999;flex-shrink:0;margin-top:1px}
.mod-decision-a{font-size:13px;color:#111111;flex:2;line-height:1.4}
/* ── Table ───────────────────────────────────────────────────── */
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
/* ── Image credits ───────────────────────────────────────────── */
.mod-credits{font-size:12px;color:#888;margin-top:32px;padding-top:12px;border-top:1px solid #e0e0e0}
.mod-credits summary{cursor:pointer;font-size:12px;color:#aaa;list-style:none}
.mod-credits summary:hover{color:#888}
/* ── Centre-align all diagrams ───────────────────────────────── */
.img-center{display:flex;justify-content:center;margin:20px 0}
.img-center svg{max-width:100%;height:auto}
.img-center>div{max-width:680px;width:100%}
@media(max-width:520px){.mod-compare-grid{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:30%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">6 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/unit1/">Unit 1 ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/unit2/">Unit 2 — current</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/unit3/">Unit 3</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/unit4/">Unit 4</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/unit5/">Unit 5</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 2 &nbsp;›&nbsp; MODULE 2 OF 4</span>
    <h1 class="mod-title-inline">Zero-Shot, Few-Shot, and Chain-of-Thought Prompting</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 15 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Requires Module 2.1</span>
  </div>
</div>

In Module 2.1 you learned the six components of a well-structured prompt. This module teaches three specific techniques that sit on top of that foundation — the highest-impact methods professional prompt engineers use every day.

These are not advanced or theoretical. They are practical patterns you can start using in your next AI session. By the end of this module you will know exactly when to use each technique and how to combine them.

---

## The three techniques — quick overview

<div class="img-center"><svg width="680" viewBox="0 0 680 110" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Three prompting techniques overview: Zero-shot asks directly with no examples, Few-shot provides examples before the task, Chain-of-thought asks the model to reason step by step</title>
<defs><marker id="ov" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M2 1L8 5L2 9" fill="none" stroke="#1565C0" stroke-width="1.5" stroke-linecap="round"/></marker></defs>
<rect x="0" y="0" width="680" height="110" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<rect x="14" y="16" width="196" height="78" rx="7" fill="#e3f2fd" stroke="#90caf9" stroke-width="1"/>
<text x="112" y="38" text-anchor="middle" font-size="12" font-weight="700" fill="#1565C0" font-family="sans-serif">Zero-Shot</text>
<text x="112" y="56" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">Ask directly. No examples.</text>
<text x="112" y="72" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">Works for clear, simple tasks.</text>
<text x="112" y="86" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Start here always.</text>
<rect x="242" y="16" width="196" height="78" rx="7" fill="#fff8e1" stroke="#FFB300" stroke-width="1"/>
<text x="340" y="38" text-anchor="middle" font-size="12" font-weight="700" fill="#FF8C00" font-family="sans-serif">Few-Shot</text>
<text x="340" y="56" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">Give 1–3 examples first,</text>
<text x="340" y="72" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">then state the task.</text>
<text x="340" y="86" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Use when format or style matters.</text>
<rect x="470" y="16" width="196" height="78" rx="7" fill="#e8f5e9" stroke="#a5d6a7" stroke-width="1"/>
<text x="568" y="38" text-anchor="middle" font-size="12" font-weight="700" fill="#2e7d32" font-family="sans-serif">Chain-of-Thought</text>
<text x="568" y="56" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">Ask the model to reason</text>
<text x="568" y="72" text-anchor="middle" font-size="11" fill="#333" font-family="sans-serif">step by step.</text>
<text x="568" y="86" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">Use for complex problems.</text>
</svg></div>

---

## Technique 1 — Zero-Shot Prompting

Zero-shot means asking the model to do something directly, without providing any examples. You describe the task and let the model use its training to handle it.

<div class="mod-technique">
<div class="mod-technique-header" style="background:#1565C0">
  <div class="mod-technique-name">Zero-Shot Prompting</div>
  <span class="mod-technique-tag">Start here for every task</span>
</div>
<div class="mod-technique-body">
  <p class="mod-technique-desc">The model relies entirely on patterns from its training data. No examples needed. Modern models like GPT-4o, Claude Sonnet, and Gemini Pro handle zero-shot well for most everyday tasks — especially when your six-component prompt structure from Module 2.1 is in place.</p>

  <div class="mod-prompt-box mod-pb-blue">
    <div class="mod-prompt-label">ZERO-SHOT EXAMPLE 1 — Code explanation</div>
    <div class="mod-prompt-text">You are a senior Python developer explaining code to a junior colleague.

Explain what this function does, line by line, in plain English. No jargon.

def find_duplicates(lst):
    seen = set()
    duplicates = []
    for item in lst:
        if item in seen:
            duplicates.append(item)
        else:
            seen.add(item)
    return duplicates</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THIS WORKS</div>
      Role + task + constraint ("no jargon") + the code itself as context. The model has everything it needs. No example of the output style was needed because "line by line, plain English" is clear enough.
    </div>
  </div>

  <div class="mod-prompt-box mod-pb-blue">
    <div class="mod-prompt-label">ZERO-SHOT EXAMPLE 2 — Email draft</div>
    <div class="mod-prompt-text">You are a professional communicator writing on behalf of a software engineer.

Draft an email to my project manager at Wipro explaining that the API integration task will be delayed by 2 days because the third-party vendor has not shared the documentation.

Tone: professional but direct. Under 120 words. No apology in the subject line.</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THIS WORKS</div>
      Context (Wipro, API integration, vendor delay), task (draft email), format (under 120 words), constraint (no apology in subject). Zero-shot is completely sufficient here — the model knows what a professional email looks like.
    </div>
  </div>

  <div style="margin-top:14px;padding:10px 14px;background:#f9f9f9;border-radius:6px;font-size:13px;color:#444;border:1px solid #e0e0e0">
    <strong style="color:#1565C0">When zero-shot is enough:</strong> Most everyday tasks — summaries, drafts, explanations, translations, code review, simple analysis. If the model knows what "good output" looks like from its training (which it does for most common tasks), zero-shot with a well-structured prompt is all you need.
  </div>
</div>
</div>

---

## Technique 2 — Few-Shot Prompting

Few-shot means providing 1–3 examples of the input-output pattern you want before stating your actual task. The model learns the pattern from your examples and applies it.

<div class="mod-keypoint">
<strong>Why few-shot works:</strong> Examples show the model the format, tone, and level of detail you want — far more precisely than describing it in words. A single well-chosen example is often worth more than three paragraphs of formatting instructions.
</div>

<div class="mod-technique">
<div class="mod-technique-header" style="background:#e65c00">
  <div class="mod-technique-name">Few-Shot Prompting</div>
  <span class="mod-technique-tag">Use when style or format matters</span>
</div>
<div class="mod-technique-body">
  <p class="mod-technique-desc">You provide example input-output pairs first, then give the model the real input. The model matches your demonstrated pattern. This is one of the highest-ROI prompt techniques available — even one example dramatically improves output consistency for style-sensitive tasks.</p>

  <div class="mod-prompt-box mod-pb-orange">
    <div class="mod-prompt-label">FEW-SHOT EXAMPLE 1 — LinkedIn post style matching</div>
    <div class="mod-prompt-text">I write LinkedIn posts in a specific style. Here are two examples:

Example 1:
"3 things I learned failing my first Infosys interview:
1. They care more about how you think than what you know
2. Saying 'I don't know, but here's how I'd find out' beats guessing
3. Your CGPA is the entry ticket — personality is the interview
What would you add?"

Example 2:
"Just got my first internship offer.
Not from campus placement. From a cold email I sent 6 weeks ago.
Template I used: [link]
Your network is not who you know. It's who knows you're looking."

Now write a LinkedIn post in the same style about completing a free online AI course and how it helped me stand out in a TCS interview.</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THIS WORKS</div>
      Without examples, the model would produce a generic "I'm excited to share..." LinkedIn post. With two examples, it learns your exact style — punchy numbered lists, conversational tone, India-specific references, ending with a hook. The output will sound like you, not like AI.
    </div>
  </div>

  <div class="mod-prompt-box mod-pb-orange">
    <div class="mod-prompt-label">FEW-SHOT EXAMPLE 2 — Consistent bug report format</div>
    <div class="mod-prompt-text">Convert the following developer notes into a formal bug report. Use this format:

Example input: "login page crashes when you type a really long email"
Example output:
Title: Login page crashes on email input exceeding character limit
Severity: High
Steps to reproduce:
1. Navigate to login page
2. Enter email address longer than 255 characters
3. Click Submit
Expected behaviour: Input validation error displayed
Actual behaviour: Application crashes with 500 error
Environment: Chrome 124, Windows 11

Now convert this note:
"the export to CSV button doesn't work when there are more than 500 rows in the table"</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THIS WORKS</div>
      The example defines both the exact format and the level of technical precision needed. Zero-shot with just "write a bug report" would give you a generic format. One example gives you your exact team format every time.
    </div>
  </div>

  <div class="mod-prompt-box mod-pb-orange">
    <div class="mod-prompt-label">FEW-SHOT EXAMPLE 3 — Interview Q&A generation</div>
    <div class="mod-prompt-text">Generate interview questions and model answers for a TCS technical round. Follow this format exactly:

Q: What is polymorphism in OOP?
A: Polymorphism means one interface, many implementations. In Java, this happens through method overloading (same method name, different parameters) and method overriding (subclass redefines parent's method). Example: a Shape class with an area() method — Circle, Rectangle, and Triangle each implement area() differently, but you can call shape.area() on any of them.
Why it matters in interviews: Shows you understand OOP principles with a concrete example, not just a textbook definition.

Generate 3 more Q&As in the same format for: Exception handling, Collections framework, and Multithreading.</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THIS WORKS</div>
      The single example defines three things at once — the Q&A format, the depth of explanation expected, and the "why it matters" framing. The model replicates all three for every subsequent question. This technique saves hours when building interview prep materials.
    </div>
  </div>

</div>
</div>

---

## Technique 3 — Chain-of-Thought (CoT) Prompting

Chain-of-thought prompting asks the model to show its reasoning step by step before giving a final answer. This dramatically improves accuracy on problems that require reasoning, analysis, or multi-step logic.

<div class="mod-technique">
<div class="mod-technique-header" style="background:#2e7d32">
  <div class="mod-technique-name">Chain-of-Thought Prompting</div>
  <span class="mod-technique-tag">Use for complex reasoning tasks</span>
</div>
<div class="mod-technique-body">
  <p class="mod-technique-desc">Instead of asking for a direct answer, you ask the model to reason through the problem first. The act of generating the reasoning process improves the final answer — the model is less likely to jump to a wrong conclusion when it has to show its work.</p>

  <div class="mod-prompt-box mod-pb-green">
    <div class="mod-prompt-label">COT EXAMPLE 1 — Simple trigger phrase</div>
    <div class="mod-prompt-text">A project has 3 developers. Developer A can complete the backend in 6 days alone. Developer B can complete it in 4 days alone. Developer C can complete it in 12 days alone. If all three work together, how many days will it take to complete the backend?

Think through this step by step before giving your answer.</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">THE CoT TRIGGER</div>
      "Think through this step by step" is the simplest CoT trigger. Without it, the model often jumps to a number directly — and gets it wrong. With it, the model works out the rates (1/6 + 1/4 + 1/12 = 2/12 + 3/12 + 1/12 = 6/12 = 1/2 per day → 2 days), shows the working, and arrives at the correct answer.
    </div>
  </div>

  <div class="mod-prompt-box mod-pb-green">
    <div class="mod-prompt-label">COT EXAMPLE 2 — Technical decision analysis</div>
    <div class="mod-prompt-text">I am building a REST API for an Indian ed-tech startup. Expected users: 50,000 per month. Budget is limited. I need to decide between hosting on AWS, Azure, or a basic VPS like DigitalOcean.

Analyse each option step by step:
1. First evaluate cost at our scale
2. Then evaluate ease of setup for a 2-person team
3. Then evaluate scalability if we grow to 500,000 users
4. Then give your recommendation with reasoning

Do not give the recommendation until you have completed all four steps.</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THE STRUCTURE MATTERS</div>
      The numbered steps force the model to evaluate each dimension before concluding. Without this, the model typically jumps to "use AWS" based on training patterns — missing the budget and team-size constraints entirely. The explicit "do not give the recommendation until..." instruction prevents premature conclusions.
    </div>
  </div>

  <div class="mod-prompt-box mod-pb-green">
    <div class="mod-prompt-label">COT EXAMPLE 3 — Career decision</div>
    <div class="mod-prompt-text">I have two job offers:
Offer A: TCS, Chennai, ₹4.2 LPA, Java development, 9–6 fixed hours
Offer B: Startup, Bengaluru, ₹3.8 LPA, Full-stack, flexible hours, ESOPs

I am a fresher from Coimbatore. My goal is to move into AI/ML in 3–4 years.

Reason through this decision carefully:
- First, consider which role builds more transferable skills for AI/ML
- Then consider the financial and lifestyle factors
- Then consider the risk profile of each option
- Finally, give your recommendation and explain the single most important factor

Think step by step.</div>
    <div class="mod-prompt-result">
      <div class="mod-prompt-result-label">WHY THIS WORKS FOR INDIAN STUDENTS</div>
      Career decisions with Indian-specific context (LPA, city preferences, family expectations around stability vs startup risk) benefit enormously from CoT. The model considers multiple dimensions before concluding — giving you a genuinely reasoned answer, not just "follow your passion."
    </div>
  </div>

</div>
</div>

---

## Combining the three techniques

The real power comes from combining techniques. Here is a complete example that uses all three — zero-shot structure, few-shot for style, and CoT for the analysis:

<div class="mod-prompt-box mod-pb-blue" style="margin:20px 0">
  <div class="mod-prompt-label">COMBINED EXAMPLE — Technical interview preparation</div>
  <div class="mod-prompt-text">You are an experienced technical interviewer at a top Indian IT company. [ROLE — zero-shot]

I have a system design interview at Infosys tomorrow for a backend developer role. [CONTEXT]

Here is an example of how I want you to break down a system design question:

Question: "Design a URL shortener like bit.ly"
Answer structure:
Step 1 — Clarify requirements (scale, features, constraints)
Step 2 — High-level architecture (components and data flow)
Step 3 — Database design (schema, choice of DB type)
Step 4 — Key trade-offs (consistency vs availability, SQL vs NoSQL)
Step 5 — What I would improve given more time
[ONE EXAMPLE — few-shot]

Now use that same structure to break down this question step by step:
"Design a notification system that sends 10 million push notifications per day."

Think through each step carefully before moving to the next. [CoT trigger]</div>
</div>

This single prompt will produce a structured, interview-ready answer that follows your preferred format, covers the right depth, and shows reasoning at each step. This is the level of prompting that separates good AI users from great ones.

---

## When to use which technique

<div class="mod-decision">
<div class="mod-decision-title">DECISION GUIDE — CHOOSING THE RIGHT TECHNIQUE</div>
<div class="mod-decision-row">
  <span class="mod-decision-q">Simple, well-defined task (email, summary, code explanation)?</span>
  <span class="mod-decision-arrow">→</span>
  <span class="mod-decision-a"><strong>Zero-shot.</strong> Add role + task + format. Done.</span>
</div>
<div class="mod-decision-row">
  <span class="mod-decision-q">Output style or format matters (LinkedIn post, bug report, PR review)?</span>
  <span class="mod-decision-arrow">→</span>
  <span class="mod-decision-a"><strong>Few-shot.</strong> Provide 1–2 examples first. The model matches your pattern exactly.</span>
</div>
<div class="mod-decision-row">
  <span class="mod-decision-q">Multi-step reasoning, analysis, or decision-making?</span>
  <span class="mod-decision-arrow">→</span>
  <span class="mod-decision-a"><strong>Chain-of-thought.</strong> Add "think step by step" or break it into numbered reasoning steps.</span>
</div>
<div class="mod-decision-row">
  <span class="mod-decision-q">Complex task where format AND reasoning both matter?</span>
  <span class="mod-decision-arrow">→</span>
  <span class="mod-decision-a"><strong>Combine all three.</strong> Use zero-shot structure, add one example, add a CoT trigger.</span>
</div>
<div class="mod-decision-row">
  <span class="mod-decision-q">Not sure? Where to start?</span>
  <span class="mod-decision-arrow">→</span>
  <span class="mod-decision-a"><strong>Always start with zero-shot.</strong> Upgrade to few-shot or CoT only if the output is not good enough. Adding complexity before it is needed wastes time.</span>
</div>
</div>

---

## Quick reference — technique comparison

<div class="mod-compare-grid">
  <div class="mod-compare-card">
    <div class="mod-compare-header" style="background:#e3f2fd;color:#1565C0">Zero-Shot</div>
    <div class="mod-compare-body">
      <ul>
        <li>No examples needed</li>
        <li>Fastest to write</li>
        <li>Works for most everyday tasks</li>
        <li>Relies on model training</li>
        <li>Start here always</li>
      </ul>
    </div>
    <div class="mod-compare-when" style="color:#1565C0">Best for: Summaries, drafts, explanations</div>
  </div>
  <div class="mod-compare-card">
    <div class="mod-compare-header" style="background:#fff8e1;color:#e65c00">Few-Shot</div>
    <div class="mod-compare-body">
      <ul>
        <li>1–3 examples provided</li>
        <li>Takes 2–5 min to set up</li>
        <li>Consistent format output</li>
        <li>Style matches your examples</li>
        <li>Reuse examples across sessions</li>
      </ul>
    </div>
    <div class="mod-compare-when" style="color:#e65c00">Best for: Posts, reports, structured docs</div>
  </div>
  <div class="mod-compare-card">
    <div class="mod-compare-header" style="background:#e8f5e9;color:#2e7d32">Chain-of-Thought</div>
    <div class="mod-compare-body">
      <ul>
        <li>Add reasoning steps</li>
        <li>One phrase triggers it</li>
        <li>Higher accuracy on logic</li>
        <li>Longer but more reliable</li>
        <li>Good for decisions</li>
      </ul>
    </div>
    <div class="mod-compare-when" style="color:#2e7d32">Best for: Analysis, decisions, math</div>
  </div>
</div>

---

## Tool-specific notes for 2026

<div class="mod-table-wrap">
<table class="mod-table">
<thead><tr><th>Tool</th><th>Zero-Shot</th><th>Few-Shot</th><th>Chain-of-Thought</th></tr></thead>
<tbody>
  <tr>
    <td>ChatGPT (GPT-4o)</td>
    <td>Excellent — infers intent well even from brief prompts</td>
    <td>Handles 1–3 examples cleanly; put examples before the task</td>
    <td>"Think step by step" works reliably; also responds well to numbered reasoning steps</td>
  </tr>
  <tr>
    <td>Claude (Sonnet)</td>
    <td>Strong — particularly good at following format constraints without examples</td>
    <td>Very responsive to examples; use XML-style tags to separate examples from task for best results</td>
    <td>Excellent CoT — add "reason through this carefully" for nuanced analysis; tends to be thorough</td>
  </tr>
  <tr>
    <td>Gemini (Pro)</td>
    <td>Good — place the task question at the end of the prompt, after any context</td>
    <td>Google's own guidelines recommend always using few-shot for complex tasks; Gemini benefits more from examples than the other two</td>
    <td>Works well; add explicit numbered steps rather than relying on "think step by step" alone</td>
  </tr>
</tbody>
</table>
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 2.2</div>
  <ol>
    <li><strong>Zero-shot first, always</strong> — most well-structured prompts work without examples. Only add examples (few-shot) or reasoning steps (CoT) when zero-shot output is not good enough. Adding complexity before it is needed slows you down.</li>
    <li><strong>Few-shot is about style, not information</strong> — use it when you want the model to match a specific format, tone, or structure. One well-chosen example beats three paragraphs of format instructions every time.</li>
    <li><strong>Chain-of-thought prevents wrong answers on hard problems</strong> — when the task involves multi-step reasoning, "think step by step" is not optional. Without it, models jump to plausible-sounding but wrong conclusions. With it, accuracy improves significantly.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-22">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 2.2 — Use All Three Techniques on Real Tasks</h3>
  </div>
  <p>Three tasks, one technique each. Each should take 10–15 minutes including testing.</p>
  <ol>
    <li><strong>Zero-shot task:</strong> Write a zero-shot prompt asking AI to explain a technical concept from your domain (OS, DBMS, networking, or any subject you are studying). Use the six-component structure from Module 2.1. Test it and note the output quality.</li>
    <li><strong>Few-shot task:</strong> Write a LinkedIn post about a project or achievement using few-shot prompting. Provide two examples of LinkedIn posts you admire first, then ask the model to write yours in the same style. Compare the output to what you would have got without examples.</li>
    <li><strong>Chain-of-thought task:</strong> Give the model a real decision you are facing — a course to take, a tool to learn, a job offer to evaluate, or a project architecture decision. Ask it to reason through the decision step by step across at least three dimensions before concluding. Note whether the recommendation surprises you.</li>
    <li><strong>Add all three prompts to your AI Learning Journal</strong> with a note on which technique made the most difference for each task.</li>
  </ol>
  <p>After this assignment you will have used all three techniques on your own real work. That hands-on calibration is more valuable than any amount of reading about the techniques.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit2/module-2-1-anatomy-of-a-good-prompt/">&#8592; Module 2.1: Anatomy of a Good Prompt</a>
  <a class="mod-nav-next" href="/courses/genai/unit2/module-2-3-role-prompting-personas/">Module 2.3: Role Prompting and Personas &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>Few-shot remains one of highest-ROI prompt techniques; try zero-shot before few-shot</td><td>Thomas Wiegold, Prompt Engineering Best Practices 2026</td></tr>
      <tr><td>Gemini benefits more from few-shot; Google recommends examples for complex tasks</td><td>Google Gemini prompt engineering whitepaper, cited in Thomas Wiegold 2026</td></tr>
      <tr><td>Claude responds well to contract-style instructions and XML tags for example separation</td><td>Lakera Prompt Engineering Guide 2026; Anthropic prompt engineering docs</td></tr>
      <tr><td>CoT improves accuracy on multi-step reasoning; "think step by step" trigger</td><td>Wei et al. 2022 "Chain-of-Thought Prompting Elicits Reasoning"; k2view.com 2026</td></tr>
      <tr><td>ChatGPT infers intent well even from brief prompts; crisp constraints work well</td><td>Lakera Prompt Engineering Guide 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
