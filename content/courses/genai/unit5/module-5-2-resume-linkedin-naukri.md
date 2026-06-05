---
title: "Module 5.2: Resume, LinkedIn, and Naukri — Showcasing Your AI Skills"
description: "How to list GenAI skills on your resume, LinkedIn, and Naukri profile to stand out to Indian IT recruiters in 2026 — with exact language, keyword lists, and before/after examples."
weight: 2
sidebar: false
mainroad_aside: false
tags: ["resume", "linkedin", "naukri", "career", "india", "job-search", "ai-skills", "freshers"]
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
/* ── Before/after ────────────────────────────────────────────── */
.mod-ba-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:16px 0}
.mod-ba-box{border-radius:8px;overflow:hidden;border:1px solid}
.mod-ba-label{padding:7px 13px;font-size:11px;font-weight:700;letter-spacing:0.05em}
.mod-ba-text{padding:12px 14px;font-size:13px;line-height:1.75;color:#111111}
.mod-ba-bad .mod-ba-label{background:#ffeaea;color:#c62828;border-bottom:1px solid #ef9a9a}
.mod-ba-bad{border-color:#ef9a9a}
.mod-ba-bad .mod-ba-text{background:#fff8f8}
.mod-ba-good .mod-ba-label{background:#e8f5e9;color:#2e7d32;border-bottom:1px solid #a5d6a7}
.mod-ba-good{border-color:#a5d6a7}
.mod-ba-good .mod-ba-text{background:#f5fff6}
/* ── Keyword grid ────────────────────────────────────────────── */
.mod-kw-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:16px 0}
.mod-kw-tag{background:#e3f2fd;border:1px solid #90caf9;border-radius:4px;padding:6px 10px;font-size:12px;font-weight:600;color:#1565C0;text-align:center}
.mod-kw-tag.mod-kw-hot{background:#fff8e1;border-color:#FFB300;color:#e65c00}
/* ── Profile section cards ───────────────────────────────────── */
.mod-profile{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0}
.mod-profile-header{padding:11px 16px;background:#f5f8ff;border-bottom:1px solid #e0e0e0;display:flex;align-items:center;gap:8px}
.mod-profile-icon{font-size:16px}
.mod-profile-title{font-size:14px;font-weight:700;color:#1565C0;margin:0}
.mod-profile-body{padding:14px 16px}
.mod-profile-example{font-size:13px;font-family:monospace,sans-serif;background:#f5f5f4;border-radius:5px;padding:12px 14px;color:#333;line-height:1.75;white-space:pre-wrap;border-left:3px solid #1565C0;margin:8px 0}
.mod-profile-note{font-size:12px;color:#666;line-height:1.5;font-style:italic;margin-top:6px}
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
.mod-pb-orange .mod-prompt-label{background:#fff8e1;color:#e65c00;border-bottom:1px solid #FFB300}
.mod-pb-orange{border-color:#FFB300}
.mod-pb-orange .mod-prompt-text{background:#fffdf0}
.mod-pb-orange .mod-prompt-note{border-color:#fff8e1}
/* ── Checklist ───────────────────────────────────────────────── */
.mod-checklist{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0}
.mod-checklist-header{background:#1565C0;padding:11px 16px;font-size:12px;font-weight:700;letter-spacing:0.05em;color:#fff}
.mod-check-section{padding:4px 0}
.mod-check-section-title{font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;padding:10px 16px 4px}
.mod-check-item{display:flex;align-items:flex-start;gap:10px;padding:8px 16px;border-bottom:1px solid #f5f5f5}
.mod-check-item:last-child{border-bottom:none}
.mod-check-box{width:16px;height:16px;border-radius:3px;border:1.5px solid #b0bec5;flex-shrink:0;margin-top:2px;background:#fff}
.mod-check-text{font-size:13px;color:#111111;line-height:1.5;flex:1}
.mod-check-text em{font-size:11px;color:#888;font-style:normal;display:block;margin-top:1px}
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
@media(max-width:520px){.mod-ba-grid{grid-template-columns:1fr}.mod-kw-grid{grid-template-columns:1fr 1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:85%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">17 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit done" href="/courses/genai/#module-1">Module 1 ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-2">Module 2 ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-3">Module 3 ✓</a>
    <a class="mod-progress-unit done" href="/courses/genai/#module-4">Module 4 ✓</a>
    <a class="mod-progress-unit current" href="/courses/genai/#module-5">Module 5 — current</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 5 &nbsp;›&nbsp; MODULE 2 OF 4</span>
    <h1 class="mod-title-inline">Resume, LinkedIn, and Naukri — Showcasing Your AI Skills</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Action-ready</span>
  </div>
</div>

You have now completed 17 of 20 modules. You have built prompt engineering skills, applied them to real developer, analyst, and manager tasks, understood RAG and agents, made smart certification choices, and built at least one portfolio project. This module is about making all of that visible to recruiters — in exactly the right language, in exactly the right places.

Most students undersell their AI skills on their profiles. Not because the skills are weak — but because they do not know the specific keywords, formats, and framing that Indian IT recruiters and ATS systems look for in 2026.

---

## The stakes — what Indian recruiters see in 8 seconds

<function_calls>
<invoke name="bash_tool">
<parameter name="command">cat >> /mnt/user-data/outputs/module-5-2-resume-linkedin-naukri.md << 'ENDOFFILE2'

According to Naukri's 2025 hiring report, 68% of fresher resumes are rejected within 8 seconds — not for lack of skills, but poor formatting and keyword gaps. LinkedIn keyword optimisation delivers a 70% boost in profile views. Profiles with AI skills listed are receiving 2x the recruiter responses compared to profiles without them, according to the 2026 Naukri JobSpeak analysis.

<div class="mod-keypoint">
<strong>The three-part visibility formula for Indian IT in 2026:</strong> Right keywords (so ATS systems surface your profile) + Right framing (so recruiters see impact, not just activity) + Right platform priority (Naukri for volume, LinkedIn for quality, both for maximum reach). Missing any one of these three halves your effective visibility.
</div>

---

## Part 1 — Resume: the AI skills section

### The keywords that actually appear in Indian IT job descriptions

These are the AI-related terms extracted from real 2026 job descriptions at TCS, Infosys, Wipro, HCL, and product companies in India. Add the ones that match your actual skills — never list skills you cannot discuss in an interview.

<div class="mod-kw-grid">
  <div class="mod-kw-tag mod-kw-hot">Prompt Engineering</div>
  <div class="mod-kw-tag mod-kw-hot">Generative AI</div>
  <div class="mod-kw-tag mod-kw-hot">Large Language Models (LLMs)</div>
  <div class="mod-kw-tag mod-kw-hot">ChatGPT</div>
  <div class="mod-kw-tag mod-kw-hot">RAG</div>
  <div class="mod-kw-tag mod-kw-hot">AI Agents</div>
  <div class="mod-kw-tag">LangChain</div>
  <div class="mod-kw-tag">GitHub Copilot</div>
  <div class="mod-kw-tag">Microsoft Copilot</div>
  <div class="mod-kw-tag">Claude API</div>
  <div class="mod-kw-tag">OpenAI API</div>
  <div class="mod-kw-tag">Vector Databases</div>
  <div class="mod-kw-tag">Fine-tuning</div>
  <div class="mod-kw-tag">Workflow Automation</div>
  <div class="mod-kw-tag">n8n</div>
  <div class="mod-kw-tag">Agentic AI</div>
  <div class="mod-kw-tag">AI-assisted Development</div>
  <div class="mod-kw-tag">Chain-of-Thought</div>
</div>

<p style="font-size:12px;color:#888;margin-top:4px">Orange = highest frequency in 2026 Indian IT JDs. Add these first.</p>

### Writing AI skills bullets that convert

The difference between a weak and strong resume bullet is specificity and outcome. Generic bullets fail ATS filters and fail to impress recruiters who read past them.

<div class="mod-ba-grid">
  <div class="mod-ba-box mod-ba-bad">
    <div class="mod-ba-label">✗ WEAK — generic, no outcome</div>
    <div class="mod-ba-text">• Knowledge of AI tools like ChatGPT and Claude
• Used AI for coding tasks
• Familiar with prompt engineering</div>
  </div>
  <div class="mod-ba-box mod-ba-good">
    <div class="mod-ba-label">✓ STRONG — specific, outcome-focused</div>
    <div class="mod-ba-text">• Applied prompt engineering (zero-shot, few-shot, CoT) to reduce code review time by 40% in a team of 5 during final-year project
• Built a RAG-based Q&amp;A system over 200-page product documentation using LangChain and ChromaDB — deployed as internal tool
• Automated weekly status report generation using n8n + OpenAI API, saving 2 hours per week</div>
  </div>
</div>

The formula for every AI skills bullet: **[Technique/tool] + [specific task] + [quantified outcome or context]**

### Where to place AI skills on a fresher resume

<div class="mod-profile">
<div class="mod-profile-header">
  <span class="mod-profile-icon">&#128196;</span>
  <div class="mod-profile-title">Fresher Resume — Recommended section order for Indian IT</div>
</div>
<div class="mod-profile-body">
  <p style="font-size:13px;color:#333;margin:0 0 10px">Reverse-chronological format is universally preferred by Indian ATS systems including Naukri's RMS and TCS iRecruit. This is the section order that maximises ATS scoring and recruiter engagement for freshers:</p>
  <div class="mod-profile-example">1. Name + Contact (phone, email, LinkedIn URL, GitHub URL)
2. Professional Summary — 2–3 sentences, include "Generative AI" and your target role
3. Technical Skills — list AI tools prominently at the TOP of this section
4. Projects — list your best AI project first with quantified outcome
5. Education — degree, branch, CGPA, institution, passing year
6. Certifications — Google AI Essentials, DeepLearning.AI, etc.
7. Achievements / Extra-curricular (optional)</div>
  <div class="mod-profile-note">AI skills go in Technical Skills AND in Projects. Two placements increase ATS keyword match score significantly. Do not bury AI tools at the bottom of a long skills list.</div>
</div>
</div>

### Professional summary — use AI to write it right

The professional summary is the most under-optimised section on most Indian fresher resumes. Here is a prompt that produces a strong summary:

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">PROMPT — Write your professional summary</div>
  <div class="mod-prompt-text">You are a professional resume writer specialising in Indian IT fresher resumes.

Write a 3-sentence professional summary for my resume. Use strong action language. Include the exact keywords: "Generative AI", "prompt engineering", and my target role title.

My details:
- Degree: [B.Tech / BCA / BSc] in [branch] from [college name], [year]
- Target role: [Software Developer / Data Analyst / Business Analyst] at [TCS / Infosys / product company / etc.]
- Key skills: [list your 4–5 strongest technical skills]
- Best achievement: [one specific thing — project, rank, hackathon, internship]
- AI skills from this course: Prompt engineering (zero-shot, few-shot, CoT), RAG, AI agents, no-code automation

Format: 3 sentences. No fluff. Starts with role title, not "I am".
Length: Under 60 words.</div>
  <div class="mod-prompt-note"><strong>Starts with role title, not "I am"</strong> — Indian ATS systems parse the first word of the summary as a role signal. Starting with your target role title ("Software Developer with..." or "Data Analyst specialising in...") improves ATS classification accuracy.</div>
</div>

---

## Part 2 — LinkedIn: getting found by Indian IT recruiters

LinkedIn delivers 70% more profile views with keyword-optimised profiles. For Indian IT students, the four highest-impact sections are Headline, About, Skills, and Featured.

<div class="mod-profile">
<div class="mod-profile-header">
  <span class="mod-profile-icon">&#128101;</span>
  <div class="mod-profile-title">LinkedIn Headline — the most important 220 characters you will write</div>
</div>
<div class="mod-profile-body">
  <p style="font-size:13px;color:#333;margin:0 0 10px">Your headline appears in every search result, every connection request, every recruiter browse. Most freshers write "Student at XYZ College" — which is invisible to recruiters. Write your aspirational role + your differentiating skills instead.</p>
  <div class="mod-ba-grid">
    <div class="mod-ba-box mod-ba-bad">
      <div class="mod-ba-label">✗ INVISIBLE HEADLINE</div>
      <div class="mod-ba-text">B.Tech Student at ABC Engineering College | Looking for Opportunities</div>
    </div>
    <div class="mod-ba-box mod-ba-good">
      <div class="mod-ba-label">✓ SEARCHABLE HEADLINE</div>
      <div class="mod-ba-text">Software Developer | Generative AI &amp; Prompt Engineering | Python | RAG | Open to SDE Roles at Product &amp; IT Companies</div>
    </div>
  </div>
  <div class="mod-profile-note">Include: your target role, "Generative AI", one or two technical skills, and "Open to [role type] roles" — this signals active job search to LinkedIn's recruiter tool filters.</div>
</div>
</div>

<div class="mod-profile">
<div class="mod-profile-header">
  <span class="mod-profile-icon">&#128221;</span>
  <div class="mod-profile-title">LinkedIn About section — your 2,000-character career story</div>
</div>
<div class="mod-profile-body">
  <div class="mod-prompt-box mod-pb-orange" style="margin:0">
    <div class="mod-prompt-label">PROMPT — Write your LinkedIn About section</div>
    <div class="mod-prompt-text">You are a LinkedIn profile writer specialising in Indian IT professionals.

Write my LinkedIn About section. Use first-person. 150–200 words. Include these keywords naturally: Generative AI, prompt engineering, [my target role], [my top 2 technical skills].

Structure:
- Opening hook: one specific thing I have built or achieved (not "I am passionate about...")
- What I do and what makes my approach different (mention GenAI skills here)
- What I am looking for and what I bring to a team
- One call to action (connect / reach out / view my projects)

My background: [paste your key details — degree, skills, projects, target role]

Tone: Professional but human. Sounds like a person, not a press release. No buzzwords like "passionate", "results-driven", "synergy".</div>
  </div>
  <div class="mod-profile-note" style="margin-top:8px">The hook instruction ("one specific thing I have built") is critical — most About sections start with "I am a passionate developer" which every recruiter skips. A concrete opening gets read.</div>
</div>
</div>

<div class="mod-profile">
<div class="mod-profile-header">
  <span class="mod-profile-icon">&#127919;</span>
  <div class="mod-profile-title">LinkedIn Skills section — the AI keywords to add immediately</div>
</div>
<div class="mod-profile-body">
  <p style="font-size:13px;color:#333;margin:0 0 8px">LinkedIn allows 50 skills. Add these AI-specific skills to your profile today — they are searchable by Indian IT recruiters and appear in "Skills" endorsement sections that recruiters specifically filter on:</p>
  <div class="mod-kw-grid">
    <div class="mod-kw-tag mod-kw-hot">Prompt Engineering</div>
    <div class="mod-kw-tag mod-kw-hot">Generative AI</div>
    <div class="mod-kw-tag mod-kw-hot">Large Language Models</div>
    <div class="mod-kw-tag">ChatGPT</div>
    <div class="mod-kw-tag">Retrieval-Augmented Generation</div>
    <div class="mod-kw-tag">AI Automation</div>
    <div class="mod-kw-tag">GitHub Copilot</div>
    <div class="mod-kw-tag">LangChain</div>
    <div class="mod-kw-tag">n8n</div>
  </div>
  <div class="mod-profile-note">Add skills you can genuinely discuss — not every skill on this list. Having 5 skills you can defend in an interview is more valuable than 20 you cannot.</div>
</div>
</div>

<div class="mod-profile">
<div class="mod-profile-header">
  <span class="mod-profile-icon">&#11088;</span>
  <div class="mod-profile-title">LinkedIn Featured section — show your work, not just your words</div>
</div>
<div class="mod-profile-body">
  <p style="font-size:13px;color:#333;margin:0 0 8px">The Featured section is a portfolio right on your LinkedIn profile. Most Indian freshers leave it empty. Add these in order of impact:</p>
  <div class="mod-profile-example">1. GitHub repository — your best AI project (n8n workflow, RAG system, or prompt library)
2. This course completion — link to courses.chandrashaker.in/courses/genai/
3. Certification — your Google AI Essentials or DeepLearning.AI certificate
4. LinkedIn post — your best AI-related post if it got engagement
5. Google Drive PDF — your "Company AI Research" document from Assignment 1.3</div>
  <div class="mod-profile-note">Recruiters who click through to your Featured section are already interested. Give them something concrete to see — a GitHub repo with a real README converts better than any number of skills badges.</div>
</div>
</div>

---

## Part 3 — Naukri: India's highest-volume job platform

Naukri has 7.83 crore resumes and dominates 70% of Indian job search traffic. The platform has its own keyword matching algorithm — different from LinkedIn — that scores your profile against JDs. Here is how to optimise for it.

<div class="mod-profile">
<div class="mod-profile-header">
  <span class="mod-profile-icon">&#128269;</span>
  <div class="mod-profile-title">Naukri profile — the five elements that determine search visibility</div>
</div>
<div class="mod-profile-body">
  <div class="mod-profile-example">1. KEY SKILLS field — add all AI keywords here explicitly
   → Prompt Engineering, Generative AI, LLM, ChatGPT, RAG, Python, etc.
   Naukri's algorithm heavily weights this field for search ranking.

2. RESUME HEADLINE — same logic as LinkedIn, include role + AI skills
   → "Software Developer | Generative AI | Python | Prompt Engineering"

3. PROFILE SUMMARY — same as resume summary; paste it here
   → Include "Generative AI" in the first sentence

4. IT SKILLS section — Naukri-specific field; list AI tools explicitly
   → ChatGPT, Claude, Gemini, GitHub Copilot, LangChain, n8n

5. PROJECTS section — add your best AI project with tech stack
   → Include RAG, LangChain, OpenAI API, n8n in the tech stack field</div>
  <div class="mod-profile-note">Naukri's RMS (Resume Management System) parses skills differently from its public search. Recruiters at TCS, Infosys, Wipro, and HCL use the internal RMS to filter candidates — the Key Skills field is the most important for this internal filter.</div>
</div>
</div>

### Using AI to tailor your Naukri application for each JD

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">PROMPT — Tailor your resume to a specific JD</div>
  <div class="mod-prompt-text">You are a professional resume consultant specialising in Indian IT job applications.

I will give you a job description and my current resume. Your task:
1. Identify the top 8 keywords in the JD that are missing from my resume
2. Suggest specific bullet point rewrites that add these keywords naturally
3. Flag any skills in the JD I have but have not mentioned
4. Suggest one addition to my Professional Summary to better match this role

Job Description:
[paste the full JD from Naukri or LinkedIn]

My current resume:
[paste your resume text]

Be specific. Show the before and after for each suggested change.</div>
  <div class="mod-prompt-note"><strong>This prompt alone will meaningfully increase your interview call rate.</strong> Most candidates send the same resume to every application. Tailoring to the specific JD keywords — especially at Indian IT companies that use ATS filters — moves your profile from "reviewed" to "shortlisted". Run this for every application you genuinely want.</div>
</div>

---

## The complete pre-application checklist

<div class="mod-checklist">
<div class="mod-checklist-header">AI SKILLS VISIBILITY CHECKLIST — RUN BEFORE EACH APPLICATION</div>
<div class="mod-check-section">
<div class="mod-check-section-title">RESUME</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">"Generative AI" appears in your Professional Summary<em>ATS parsers look for this exact phrase</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">AI skills listed at the top of Technical Skills — not buried at the bottom<em>Recruiter's eye goes top-left on skills sections</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">At least one AI project bullet with a quantified outcome<em>Formula: Tool + Task + Result</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Certification listed with issuer name — not just "AI Certificate"<em>"Google AI Essentials — Google, 2026" vs "AI course"</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">GitHub link in header if you have an AI project repository</div></div>
</div>
<div class="mod-check-section">
<div class="mod-check-section-title">LINKEDIN</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Headline includes "Generative AI" and your target role title<em>This is the most searched combination in Indian IT recruiter filters right now</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">About section has a concrete opening — not "I am passionate about..."</div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Prompt Engineering, Generative AI, Large Language Models added to Skills<em>These three are the highest-searched AI skills on LinkedIn India in 2026</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Featured section has at least one item — GitHub link or certificate</div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">"Open to work" is set if actively job hunting — visible to recruiters</div></div>
</div>
<div class="mod-check-section">
<div class="mod-check-section-title">NAUKRI</div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Key Skills field includes: Prompt Engineering, Generative AI, LLM, ChatGPT<em>Naukri's search algorithm weights this field most heavily</em></div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">IT Skills field lists AI tools — ChatGPT, Claude, GitHub Copilot, LangChain, n8n</div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Profile completeness score is 80%+ (Naukri shows this on your dashboard)</div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Resume uploaded as PDF — not Word — for clean ATS parsing on Naukri</div></div>
<div class="mod-check-item"><div class="mod-check-box"></div><div class="mod-check-text">Job alerts set for "Generative AI", "Prompt Engineering", "AI Developer" keywords</div></div>
</div>
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 5.2</div>
  <ol>
    <li><strong>Keywords before content — ATS never sees what it cannot find</strong> — "Generative AI", "Prompt Engineering", and "Large Language Models" must appear in your LinkedIn headline, Naukri Key Skills field, and resume Professional Summary. Without these exact phrases, your profile is invisible to the recruiter filters at TCS, Infosys, Wipro, and HCL's AI CoE hiring teams.</li>
    <li><strong>Outcomes beat activity in every bullet point</strong> — "Used AI for coding tasks" tells a recruiter nothing. "Reduced code review time by 40% using Claude for automated pre-review checks" tells them exactly what you can do and what value you bring. Apply the formula Tool + Task + Result to every skills bullet you write.</li>
    <li><strong>Tailor every application with one prompt</strong> — the JD tailoring prompt in this module takes 5 minutes per application and meaningfully increases your shortlisting rate. The same resume sent to 50 jobs performs worse than a tailored resume sent to 10 well-matched jobs. Quality beats volume on Indian ATS systems.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-52">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 5.2 — Update Your Resume, LinkedIn, and Naukri with AI Skills</h3>
  </div>
  <p>This is the most directly career-impactful assignment in the course. Block 2 hours and complete all three updates today.</p>
  <ol>
    <li><strong>Resume:</strong>
      <ul>
        <li>Run the Professional Summary prompt with your actual details</li>
        <li>Add AI skills to the top of your Technical Skills section using the keyword list from this module</li>
        <li>Rewrite your best project bullet using the Tool + Task + Result formula</li>
        <li>List your certification (or planned certification) in the Certifications section</li>
      </ul>
    </li>
    <li><strong>LinkedIn:</strong>
      <ul>
        <li>Rewrite your headline — include "Generative AI" and your target role</li>
        <li>Run the About section prompt and update with the output (edited for your voice)</li>
        <li>Add Prompt Engineering, Generative AI, and Large Language Models to your Skills section</li>
        <li>Add one item to the Featured section — GitHub project link or certification</li>
      </ul>
    </li>
    <li><strong>Naukri:</strong>
      <ul>
        <li>Update Key Skills: add Prompt Engineering, Generative AI, LLM, ChatGPT</li>
        <li>Update IT Skills: add ChatGPT, Claude, GitHub Copilot, LangChain</li>
        <li>Upload your updated resume PDF</li>
        <li>Set job alerts for "Generative AI" and "Prompt Engineering" roles in your target city</li>
      </ul>
    </li>
    <li><strong>Run the JD tailoring prompt</strong> on one real job description from Naukri or LinkedIn that you want to apply to. Note what the model finds missing and update your resume accordingly.</li>
  </ol>
  <p>After completing this assignment, you will have an AI-optimised profile on all three platforms — ready for the placement drives and direct applications that Module 5.3 and 5.4 will build on.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit5/module-5-1-genai-certifications/">&#8592; Module 5.1: Certifications Worth Getting</a>
  <a class="mod-nav-next" href="/courses/genai/unit5/module-5-3-ai-freelancing-india/">Module 5.3: Freelancing with AI &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>68% of fresher resumes rejected within 8 seconds — formatting and keyword gaps</td><td>Naukri 2025 hiring report, cited in careerskraft.com April 2026</td></tr>
      <tr><td>LinkedIn keyword optimisation delivers 70% boost in profile views</td><td>bestjobsearchapps.com India Job Sites 2026, June 2026</td></tr>
      <tr><td>Profiles with AI skills receive 2x recruiter responses</td><td>Naukri JobSpeak 2026 analysis; bestjobsearchapps.com June 2026</td></tr>
      <tr><td>Naukri has 7.83 crore resume database, 70% job search traffic share in India</td><td>bestjobsearchapps.com India Job Sites 2026; bestjobsearchapps.com ranked portals 2026</td></tr>
      <tr><td>Reverse-chronological format universally preferred by Indian ATS systems</td><td>careerskraft.com Resume Formats for Freshers India April 2026</td></tr>
      <tr><td>80% employers prioritise skills over degrees; AI skills top demand 2026</td><td>bestjobsearchapps.com; Naukri JobSpeak Index 2026</td></tr>
    </tbody>
  </table>
</details>

</div>
ENDOFFILE2
echo "Done — $(wc -l < /mnt/user-data/outputs/module-5-2-resume-linkedin-naukri.md) lines"