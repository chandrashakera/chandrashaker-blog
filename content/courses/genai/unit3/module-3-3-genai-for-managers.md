---
title: "Module 3.3: GenAI for Managers — Emails, Meeting Summaries, and Presentations"
description: "Practical guide to using GenAI for professional email writing, meeting summaries, project status reports, and presentations — for Indian IT managers and team leads."
weight: 3
sidebar: false
mainroad_aside: false
tags: ["managers", "email-writing", "meeting-summaries", "presentations", "india", "project-management", "generative-ai"]
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
/* ── Tool badges ─────────────────────────────────────────────── */
.mod-tool-row{display:flex;gap:10px;flex-wrap:wrap;margin:12px 0}
.mod-tool-badge{display:inline-flex;align-items:center;gap:6px;font-size:12px;font-weight:600;padding:5px 12px;border-radius:20px;border:1px solid}
.mod-tool-best{background:#e8f5e9;color:#2e7d32;border-color:#a5d6a7}
.mod-tool-good{background:#e3f2fd;color:#1565C0;border-color:#90caf9}
.mod-tool-ok{background:#f5f5f4;color:#666;border-color:#d3d1c7}
/* ── Scenario cards ──────────────────────────────────────────── */
.mod-scenario-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:16px 0}
.mod-scenario-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px}
.mod-scenario-label{font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;margin-bottom:6px}
.mod-scenario-title{font-size:13px;font-weight:700;color:#1565C0;margin-bottom:6px}
.mod-scenario-text{font-size:12px;font-family:monospace,sans-serif;background:#f5f5f4;border-radius:4px;padding:8px 10px;color:#333;line-height:1.6;white-space:pre-wrap;border-left:3px solid #1565C0}
/* ── Workflow ────────────────────────────────────────────────── */
.mod-workflow{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-workflow-title{font-size:11px;font-weight:700;color:#555;letter-spacing:0.05em;margin-bottom:12px}
.mod-workflow-step{display:flex;align-items:flex-start;gap:12px;padding:9px 0;border-bottom:1px solid #f0f0f0}
.mod-workflow-step:last-child{border-bottom:none}
.mod-workflow-num{width:24px;height:24px;border-radius:50%;background:#1565C0;color:#fff;font-size:12px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px}
.mod-workflow-text{font-size:13px;color:#111111;line-height:1.5;flex:1}
.mod-workflow-text strong{color:#111111}
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
@media(max-width:520px){.mod-stat-grid{grid-template-columns:1fr 1fr}.mod-scenario-grid{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:50%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">10 of 20 modules complete</div>
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
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 3 &nbsp;›&nbsp; MODULE 3 OF 4</span>
    <h1 class="mod-title-inline">GenAI for Managers — Emails, Meeting Summaries, and Presentations</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 13 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Hands-on examples</span>
  </div>
</div>

Module 3.1 covered developers. Module 3.2 covered analysts. This module is for the third role in every Indian IT team — the project manager, team lead, account manager, or delivery manager whose work is overwhelmingly communication: emails, meeting notes, status reports, client presentations, and stakeholder updates.

If your job involves more writing and communication than coding or data, this module is your highest-value module in the entire course.

---

## The manager's communication burden

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">28%</div>
    <div class="mod-stat-card-label">of the workweek spent managing email — approximately 11.2 hours — McKinsey Global Institute</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">93%</div>
    <div class="mod-stat-card-label">of project managers using GenAI for more than half their tasks report increased productivity — PMI</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">2.2 hrs</div>
    <div class="mod-stat-card-label">saved per week on average by GenAI users — equivalent to one full workday reclaimed per month (Federal Reserve research)</div>
  </div>
</div>

Knowledge workers spend approximately 28% of the workweek — about 11.2 hours — managing email. Add meeting time, status reporting, and stakeholder updates, and most managers in Indian IT spend over 60% of their time on communication rather than execution. GenAI directly addresses this — not by replacing the judgement in those communications, but by eliminating the time spent drafting and formatting them.

<div class="mod-keypoint">
<strong>The manager's edge with GenAI:</strong> Every prompt in this module produces output you send to someone — a client, your manager, your team, a vendor. The quality standard is therefore higher than in Modules 3.1 and 3.2. The goal is not just faster output but output that reflects your professional voice, your organisation's standards, and your relationship with the recipient. Context and role prompting matter more here than in any other module.
</div>

---

## Use case 1 — Professional email writing

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#9993;</span>
  <div class="mod-usecase-title">Writing professional emails for every situation</div>
</div>
<div class="mod-usecase-body">

<p>Email is where most managers waste the most time — not reading it, but writing it. Drafting a difficult escalation email, a client status update, or a vendor follow-up from scratch takes 15–30 minutes. With AI, the same email takes 2 minutes to prompt and 5 minutes to review and personalise.</p>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — Project delay escalation to client</div>
  <div class="mod-prompt-text">You are a professional delivery manager writing on behalf of an Indian IT services team.

Draft an email to my client contact (Sarah Chen, Programme Director at a UK insurance company) about a 5-day delay in the API integration milestone.

Context:
- Original deadline: 20 June 2026
- New expected date: 25 June 2026
- Root cause: Third-party vendor (payment gateway provider) delivered API documentation 8 days late
- Impact: Only the payment module is delayed — the rest of the release is on track
- What we are doing: Daily standups with the vendor, parallel testing started on mock data

Tone: Professional, factual, accountable without being overly apologetic.
Length: Under 150 words.
Do not use: "We sincerely apologise", "please be advised", "as per our discussion"
Subject line: Include one.</div>
  <div class="mod-prompt-note"><strong>The "do not use" constraint is critical for Indian IT emails.</strong> Overuse of "we sincerely apologise" and "as per our discussion" are widely recognised patterns in Indian IT client communication that can undermine credibility with international clients. Explicitly excluding them produces a more direct, confident email. The root cause attribution to the vendor (not the team) is factually important and should be stated clearly — the prompt ensures the model includes it.</div>
</div>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — Internal escalation to senior management</div>
  <div class="mod-prompt-text">You are a project manager at TCS writing to your delivery head.

Write an escalation email about a resourcing issue affecting project delivery.

Situation:
- Project: Core banking modernisation for a PSU bank client
- Problem: Two senior Java developers were moved to another project 3 weeks ago without replacement
- Current impact: Sprint velocity dropped from 42 to 24 story points; 2 features at risk for the August release
- What I need: Either return the developers by 15 July or approve hiring 2 contractors
- What happens if nothing is done: August release date will slip by 3–4 weeks, risking the ₹2.4 Cr penalty clause

Format: Short paragraphs, not bullet points.
Tone: Urgent but professional — not emotional.
Include: A clear ask in the last paragraph.</div>
  <div class="mod-prompt-note"><strong>The "clear ask in the last paragraph" instruction</strong> is the most important element in any escalation email. Without it, AI produces a narrative without a decision point — and management escalations without a clear ask get filed, not acted on. The ₹ penalty clause context signals commercial urgency without requiring the manager to write that section from scratch.</div>
</div>

<div class="mod-scenario-grid">
  <div class="mod-scenario-card">
    <div class="mod-scenario-label">SCENARIO TEMPLATE</div>
    <div class="mod-scenario-title">Vendor follow-up (no response)</div>
    <div class="mod-scenario-text">Role: Procurement manager following up with vendor.
Situation: 3rd follow-up, no response in 10 days, blocking our go-live.
Tone: Firm but not hostile.
Ask: Response by EOD Friday or escalate to their account manager.
Length: Under 100 words.</div>
  </div>
  <div class="mod-scenario-card">
    <div class="mod-scenario-label">SCENARIO TEMPLATE</div>
    <div class="mod-scenario-title">Positive client update</div>
    <div class="mod-scenario-text">Role: Delivery manager at Infosys.
Situation: Sprint completed ahead of schedule, 2 bonus features delivered.
Tone: Confident, brief, client-facing.
Include: Next sprint preview, one question for client.
Length: Under 120 words.</div>
  </div>
  <div class="mod-scenario-card">
    <div class="mod-scenario-label">SCENARIO TEMPLATE</div>
    <div class="mod-scenario-title">Team appreciation email</div>
    <div class="mod-scenario-text">Role: Team lead at Wipro.
Situation: Team delivered a critical hotfix at 2am on a Sunday, preventing a client outage.
Tone: Warm, genuine, specific — not corporate.
CC: Senior manager.
Length: Under 80 words.</div>
  </div>
  <div class="mod-scenario-card">
    <div class="mod-scenario-label">SCENARIO TEMPLATE</div>
    <div class="mod-scenario-title">Onboarding welcome email</div>
    <div class="mod-scenario-text">Role: Team lead welcoming a new joinee.
Situation: Fresh graduate joining a 12-person scrum team at HCL.
Include: First week plan, key contacts, one piece of genuine advice.
Tone: Welcoming but professional.
Length: Under 150 words.</div>
  </div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — most natural email writing, least AI-sounding</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — strong for structured professional emails</span>
  <span class="mod-tool-badge mod-tool-ok">Gemini in Gmail — integrated, good for quick drafts</span>
</div>

</div>
</div>

---

## Use case 2 — Meeting summaries and action items

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128221;</span>
  <div class="mod-usecase-title">Converting meeting notes into structured summaries</div>
</div>
<div class="mod-usecase-body">

<p>Writing meeting summaries is one of the highest-ROI GenAI tasks for managers. Meeting summarisation, automated task assignment, and querying data from meetings are the top three uses of AI meeting assistants according to Metrigy's research. Even without a dedicated tool, pasting rough notes into a well-structured prompt produces a professional summary in seconds.</p>

<div class="mod-prompt-box mod-pb-green">
  <div class="mod-prompt-label">EXAMPLE — Sprint review meeting summary</div>
  <div class="mod-prompt-text">You are a scrum master writing the official meeting summary for a sprint review.

Convert these rough notes into a professional meeting summary:

---
Sprint 23 Review — 5 June 2026
Attendees: Rajesh (PM), Priya (Tech Lead), Ananya (QA), Vikram (BA), Sarah (Client)

- Showed 4 completed features: login with OTP, dashboard redesign, export to PDF, notification preferences
- Sarah liked the OTP but said notification preferences UI is confusing — needs redesign
- PDF export has a bug with Tamil characters — Priya says will fix in Sprint 24
- Velocity this sprint: 38 story points (target was 42)
- Sarah asked if we can add WhatsApp notification option — not in scope, Rajesh said will discuss for Sprint 25
- Demo of login went well, client very happy
- Retrospective separately
- Next sprint planning Monday 9am
---

Format:
1. Meeting details (date, attendees, purpose)
2. Completed this sprint (bullet list)
3. Client feedback (categorised: positive / needs improvement)
4. Issues and blockers
5. Decisions made
6. Action items table: Owner | Action | Due date
7. Next steps

Keep language concise and professional.</div>
  <div class="mod-prompt-note"><strong>The structured output format is the key.</strong> Without it, AI produces a wall of prose. With the numbered sections and action items table, you get a document that is immediately shareable with the client and trackable by the team. The Tamil characters bug detail is an India-specific testing reality — including it in your notes produces a specific, accurate action item, not a generic "fix PDF export" task.</div>
</div>

<div class="mod-prompt-box mod-pb-green">
  <div class="mod-prompt-label">EXAMPLE — Client call follow-up email from notes</div>
  <div class="mod-prompt-text">Convert these rough call notes into a professional follow-up email to the client.

Call notes (30-min call with Anand Krishnamurthy, VP Technology, Reliance Retail):
- Discussed go-live timeline — he wants to pull forward from Aug 15 to Aug 1
- We said technically possible if we freeze scope by June 20
- He agreed to scope freeze but needs sign-off from his team by June 15
- Open issue: data migration strategy not finalised — his team owns the source data extraction
- We need their IT team to give us access to the legacy Oracle system by June 10
- He wants weekly status calls starting next week — Thursdays 3pm IST
- Budget discussion deferred to next call

Write a follow-up email:
- Summarise agreements and next steps
- Clearly list the 3 items his team needs to deliver and by when
- Confirm the weekly call schedule
- Professional but warm tone — we have a good relationship
- Under 200 words</div>
  <div class="mod-prompt-note"><strong>Relationship context changes the output significantly.</strong> "Professional but warm — we have a good relationship" produces a noticeably different email than a standard professional tone. The three deliverable items with dates are explicitly called out — this is the most important part of any follow-up email and the part most likely to be buried or forgotten without this instruction.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — most structured, best at complex meeting notes</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — fast, strong output for standard meeting formats</span>
  <span class="mod-tool-badge mod-tool-ok">Otter.ai / Fireflies — dedicated tools if you have recordings</span>
</div>

</div>
</div>

---

## Use case 3 — Status reports and project updates

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128203;</span>
  <div class="mod-usecase-title">Weekly status reports and project health updates</div>
</div>
<div class="mod-usecase-body">

<p>Weekly status reports are the most repetitive writing task in Indian IT project management. AI can generate a consistent, professional report from bullet-point inputs in under 2 minutes — with the same structure every week, which clients and management actually prefer over creative prose variation.</p>

<div class="mod-prompt-box mod-pb-orange">
  <div class="mod-prompt-label">EXAMPLE — Weekly project status report for an IT services engagement</div>
  <div class="mod-prompt-text">You are a project manager at Wipro writing a weekly status report for a client engagement.

Project: Digital transformation for a leading Indian private bank
Week ending: 6 June 2026
Report audience: Client steering committee (non-technical)

Input data:
- Overall status: Amber (was Green last week)
- Milestone 2 (API integration): 80% complete, 3 days behind schedule
- Milestone 3 (UAT): On track, starts July 1 as planned
- Issues: SSL certificate renewal took 2 extra days — root cause of delay
- Risk: Upcoming bank holidays (June 19–20) may affect vendor response times
- Team: Full team available, no attrition
- Budget: On track, 47% utilised at Week 8 of 18

Generate a status report with these sections:
1. Executive Summary (3 sentences max — status, main issue, outlook)
2. Milestone Status table: Milestone | Status | % Complete | Planned Date | Forecast Date
3. Issues and Risks (RAG status per item — Red/Amber/Green)
4. Highlights this week
5. Focus areas next week

Use RAG status colours (Red/Amber/Green) as text labels since this will be pasted into email.
Keep total length under 400 words.</div>
  <div class="mod-prompt-note"><strong>"Use RAG as text labels since pasted into email"</strong> is a practical India IT context constraint — most Indian IT status reports are sent as email body text, not formatted documents. Specifying this prevents the model from generating HTML colour codes or markdown that will look broken in Outlook. The Amber change from Green is the most important signal — the executive summary prompt forces the model to address it directly.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — best for consistent structured reports</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — good, especially with a saved system prompt template</span>
</div>

</div>
</div>

---

## Use case 4 — Presentations and slide content

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128202;</span>
  <div class="mod-usecase-title">Creating presentation outlines and slide content</div>
</div>
<div class="mod-usecase-body">

<p>AI does not make slides for you — it generates the content that goes into slides. The highest-value use is converting data, meeting notes, or strategic thinking into structured slide outlines that you then build in PowerPoint or Google Slides.</p>

<div class="mod-prompt-box mod-pb-purple">
  <div class="mod-prompt-label">EXAMPLE — Quarterly business review presentation outline</div>
  <div class="mod-prompt-text">You are a senior delivery manager preparing a Quarterly Business Review presentation for a client.

Audience: C-suite executives at a mid-size Indian manufacturing company
Duration: 20 minutes (approximately 15 slides)
Quarter: Q4 FY2026 (Jan–Mar 2026)

Key facts to include:
- 94% on-time delivery (target was 90%)
- 3 features delivered ahead of schedule
- 1 critical bug resolved within SLA (4-hour resolution vs 8-hour SLA)
- Team expanded from 8 to 12 members — all onboarded within 2 weeks
- 2 innovation proposals submitted, 1 approved for Q1 FY2027
- NPS score: 8.4 (up from 7.9 last quarter)
- Budget utilisation: 96% (within 5% variance — compliant)
- 1 risk open: Legacy database migration complexity — mitigation plan in place

Create a 12-slide presentation outline. For each slide:
- Slide number and title (max 7 words)
- 3 bullet points with the key message
- One "so what" statement — the business value for the client

Slides should tell a story arc: Performance → Highlights → Challenges → Value delivered → What's next</div>
  <div class="mod-prompt-note"><strong>The story arc instruction</strong> is what separates a good QBR from a data dump. The model structures the 12 slides into a narrative: opens with performance validation, moves to specific wins, addresses challenges honestly, quantifies value, and closes with forward momentum. Without the arc, AI generates slides in data-delivery order — which is not how executives want to receive information.</div>
</div>

<div class="mod-prompt-box mod-pb-purple">
  <div class="mod-prompt-label">EXAMPLE — Internal team retrospective presentation</div>
  <div class="mod-prompt-text">Create a retrospective presentation outline for a 45-minute team session.

Team: 10-member agile delivery team at HCL, end of a 3-month project phase
Facilitation style: Collaborative and honest — psychological safety is important

Retrospective framework: Start / Stop / Continue
Key themes I want to address:
- Communication gaps between frontend and backend teams
- Client scope changes mid-sprint disrupting planning
- Strong performance on code quality and test coverage
- New CI/CD pipeline working well
- Two team members leaving at end of phase

For each slide provide:
- Title and activity type (discussion / voting / reflection)
- Facilitator instructions (what to say or ask)
- Expected time (total must add to 45 minutes)
- One "watch out" — something that could go wrong in this part

End with a slide on celebrating wins before the transition.</div>
  <div class="mod-prompt-note"><strong>The "watch out" per slide instruction</strong> is a facilitation technique prompt — it prepares the team lead for difficult moments in the session. This is a management use case where AI genuinely adds skill, not just speed: a less experienced facilitator gets guidance on where retrospectives can derail, embedded directly into the presentation structure.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — best narrative structure and business writing</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — strong for structured slides and QBR formats</span>
  <span class="mod-tool-badge mod-tool-ok">Canva AI — generates actual slides if you need the file</span>
</div>

</div>
</div>

---

## The manager's AI workflow

<div class="mod-workflow">
<div class="mod-workflow-title">RECOMMENDED WORKFLOW — AI-ASSISTED MANAGEMENT COMMUNICATION</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">1</div>
  <div class="mod-workflow-text"><strong>Save your context once, reuse it always.</strong> Write a "manager persona" prompt describing your role, your company, your client relationship, and your communication style. Paste this at the start of every communication prompt — it takes 30 seconds and eliminates 80% of the editing you do on AI drafts.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">2</div>
  <div class="mod-workflow-text"><strong>Dump bullet points, not prose.</strong> AI converts bullet-point inputs into polished prose far better than it converts vague descriptions. Keep rough notes as you go — meeting bullets, key numbers, decisions made — and prompt from those rather than trying to remember everything when writing.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">3</div>
  <div class="mod-workflow-text"><strong>Always add your personal voice in one pass.</strong> AI drafts are structurally correct but impersonal. Read every output and add one specific, personalised detail — a reference to a shared context with the client, a specific team member's name, or a phrase that sounds like you. This takes 2 minutes and makes the difference between an email that gets a reply and one that gets filed.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">4</div>
  <div class="mod-workflow-text"><strong>Use the two-pass approach for sensitive communications.</strong> For escalations, difficult feedback, and client-facing issue communications — generate first, then use a second prompt: "Review this email. Does it sound defensive? Is the ask clear? Would a senior manager be comfortable sending this?" Fix what the model finds.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">5</div>
  <div class="mod-workflow-text"><strong>Never send AI output without reading it fully.</strong> AI gets names, dates, and numbers wrong in ways that are easy to miss. A client email with the wrong milestone date or a misspelled stakeholder name damages credibility instantly. Read every line before sending.</div>
</div>
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 3.3</div>
  <ol>
    <li><strong>Context and relationship define quality for manager communications</strong> — unlike code or SQL, every output in this module goes to a person who knows you. Include your role, your company, your relationship with the recipient, and the specific situation. Generic prompts produce generic emails that sound AI-written. Specific prompts produce communications that sound like you.</li>
    <li><strong>Structure the output you want, not just the content</strong> — for status reports, meeting summaries, and presentations, specify the exact sections, tables, and format. AI produces consistent, immediately usable output when given a precise structure. Without structure, you spend as much time reformatting as you saved drafting.</li>
    <li><strong>Add one personal touch to every AI draft before sending</strong> — one specific detail, reference, or phrase that is genuinely yours. This single habit transforms AI-assisted communication from obviously AI-written to professionally effective. It takes 2 minutes and is non-negotiable for client-facing work.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-33">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 3.3 — Draft Three Professional Communications Using AI</h3>
  </div>
  <p>Three real communication tasks. Use your actual work context or realistic scenarios from your target role.</p>
  <ol>
    <li><strong>Professional email:</strong> Write a prompt for a real email you need to send — or a realistic scenario you will face in your first job. Use the context-heavy structure: role, recipient, situation, tone, constraints. Note what you had to edit after the first AI draft and why.</li>
    <li><strong>Meeting summary:</strong> Take notes from any real meeting — a college group project meeting, a webinar, or a team discussion — and paste them into the meeting summary prompt structure. Compare the AI output to notes you would have sent manually. What did the model add? What did it miss?</li>
    <li><strong>Status update:</strong> Write a weekly status update for a project you are currently involved in — academic project, internship, or personal project. Use the RAG status structure. Note whether the Amber/Red items are framed accurately — this is where your judgement matters most.</li>
    <li><strong>Save all three prompts in your AI Learning Journal</strong> under "Module 3.3 — Manager Prompts." These feed into your complete prompt library in Module 3.4.</li>
  </ol>
  <p>After completing this assignment, you will have a working set of manager communication prompts that cover 80% of the recurring writing tasks in an Indian IT management role.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit3/module-3-2-genai-for-analysts/">&#8592; Module 3.2: GenAI for Analysts</a>
  <a class="mod-nav-next" href="/courses/genai/unit3/module-3-4-prompt-library/">Module 3.4: Your Prompt Library &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>28% of workweek spent managing email — approximately 11.2 hours</td><td>McKinsey Global Institute, The Social Economy, July 2012 — still current benchmark per readless.app 2026</td></tr>
      <tr><td>93% of project managers using GenAI for more than half their tasks report increased productivity</td><td>PMI, cited in sembly.ai GenAI in Project Management, February 2026</td></tr>
      <tr><td>2.2 hours saved per week on average by GenAI users</td><td>Federal Reserve research, cited in autofaceless.ai AI Productivity Statistics 2026</td></tr>
      <tr><td>Meeting summarisation, automated task assignment, and querying data from meetings are top AI meeting assistant uses</td><td>Metrigy research, cited in TechTarget AI meeting assistants February 2026</td></tr>
      <tr><td>27% of AI users save over 9 hours per week</td><td>autofaceless.ai AI Productivity Statistics 2026, April 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
