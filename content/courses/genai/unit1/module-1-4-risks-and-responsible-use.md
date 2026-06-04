---
title: "Module 1.4: Risks, Hallucinations, and Responsible Use of GenAI"
description: "Understand AI hallucinations, bias, data privacy risks, and India's AI governance framework — practical responsible use guidelines for Indian students and IT professionals."
weight: 4
sidebar: false
mainroad_aside: false
tags: ["ai-risks", "hallucinations", "responsible-ai", "dpdp-act", "india", "generative-ai", "ai-ethics"]
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
.mod-warning{background:#ffeaea;border-left:4px solid #c62828;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a0000;line-height:1.6}
.mod-warning strong{color:#c62828}
.mod-remember{background:#e8f0fe;border-left:4px solid #1565C0;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0}
.mod-remember-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.06em;margin-bottom:8px}
.mod-remember ol{margin:0;padding-left:18px}
.mod-remember li{font-size:14px;color:#1a1a1a;line-height:1.7;margin-bottom:4px}
/* ── Risk cards ──────────────────────────────────────────────── */
.mod-risk-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-risk-card{border-radius:8px;padding:16px;border:1px solid}
.mod-risk-card h3{font-size:14px;font-weight:700;margin:0 0 8px}
.mod-risk-card p{font-size:13px;margin:0;line-height:1.6}
/* ── Case study box ──────────────────────────────────────────── */
.mod-case{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0}
.mod-case-header{padding:11px 16px;font-size:12px;font-weight:700;letter-spacing:0.05em;color:#fff}
.mod-case-body{padding:14px 16px}
.mod-case-body p{font-size:13px;color:#333;line-height:1.7;margin:0 0 8px}
.mod-case-body p:last-child{margin:0}
.mod-case-lesson{background:#f9f9f9;border-top:1px solid #f0f0f0;padding:10px 16px;font-size:12px;color:#555;display:flex;gap:6px;align-items:flex-start}
.mod-case-lesson strong{color:#1565C0;flex-shrink:0}
/* ── Dos and don'ts ──────────────────────────────────────────── */
.mod-dos-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:20px 0}
.mod-dos-col{border-radius:8px;overflow:hidden;border:1px solid}
.mod-dos-header{padding:10px 14px;font-size:12px;font-weight:700;letter-spacing:0.05em}
.mod-dos-list{padding:10px 14px;margin:0;list-style:none}
.mod-dos-list li{font-size:13px;padding:6px 0 6px 20px;border-bottom:1px solid rgba(0,0,0,0.05);position:relative;line-height:1.5;color:#333}
.mod-dos-list li:last-child{border-bottom:none}
.mod-dos-list li::before{position:absolute;left:2px;font-weight:700}
.mod-do li::before{content:"✓";color:#2e7d32}
.mod-dont li::before{content:"✗";color:#c62828}
/* ── India law box ───────────────────────────────────────────── */
.mod-law{background:#e8f0fe;border:1px solid #90caf9;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-law-title{font-size:12px;font-weight:700;color:#1565C0;letter-spacing:0.05em;margin-bottom:12px}
.mod-law-item{display:flex;gap:10px;margin-bottom:10px;align-items:flex-start}
.mod-law-item:last-child{margin-bottom:0}
.mod-law-badge{font-size:10px;font-weight:700;background:#1565C0;color:#fff;padding:3px 8px;border-radius:4px;flex-shrink:0;margin-top:2px;white-space:nowrap}
.mod-law-text{font-size:13px;color:#333;line-height:1.6}
/* ── Checklist ───────────────────────────────────────────────── */
.mod-checklist{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:8px;padding:16px 18px;margin:20px 0}
.mod-checklist-title{font-size:12px;font-weight:700;color:#555;letter-spacing:0.05em;margin-bottom:12px}
.mod-checklist-item{display:flex;align-items:flex-start;gap:10px;padding:7px 0;border-bottom:1px solid #f0f0f0}
.mod-checklist-item:last-child{border-bottom:none}
.mod-checklist-num{width:22px;height:22px;border-radius:50%;background:#1565C0;color:#fff;font-size:11px;font-weight:700;display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px}
.mod-checklist-text{font-size:13px;color:#333;line-height:1.5}
.mod-checklist-text strong{color:#111}
/* ── Stat grid ───────────────────────────────────────────────── */
.mod-stat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin:20px 0}
.mod-stat-card{background:#fff;border:1px solid #e0e0e0;border-radius:8px;padding:14px 16px;text-align:center}
.mod-stat-card-num{font-size:24px;font-weight:700;color:#c62828;margin-bottom:4px}
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
@media(max-width:520px){.mod-risk-grid,.mod-dos-grid,.mod-stat-grid{grid-template-columns:1fr}}
</style>

<div class="mod-wrap">

<div class="mod-progress-wrap">
  <div class="mod-progress-header">
    <span class="mod-progress-title">YOUR PROGRESS — GENERATIVE AI: ZERO TO JOB-READY</span>
    <a href="/courses/genai/" style="font-size:12px;color:#1565C0;text-decoration:none;font-weight:600">&#8592; Course home</a>
  </div>
  <div class="mod-progress-bg">
    <div class="mod-progress-fill" style="width:15%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">3 of 20 modules complete</div>
  <div class="mod-progress-units">
    <a class="mod-progress-unit current" href="/courses/genai/#module-1">Module 1 — current</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-2">Module 2</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-3">Module 3</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-4">Module 4</a>
    <a class="mod-progress-unit upcoming" href="/courses/genai/#module-5">Module 5</a>
  </div>
</div>

<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 1 &nbsp;›&nbsp; MODULE 4 OF 4</span>
    <h1 class="mod-title-inline">Risks, Hallucinations, and Responsible Use of GenAI</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 13 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Unit 1 Finale</span>
  </div>
</div>

This is the final module of Unit 1 — and arguably the most important one for your professional reputation.

Every module so far has focused on what GenAI can do. This one focuses on what it gets wrong, and why that matters more than people realise. The engineers and analysts who get ahead in Indian IT are not the ones who use AI most — they are the ones who use it most *responsibly*. Knowing the failure modes makes you the person who catches the mistakes before they reach a client.

---

## How big is the problem?

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">51%</div>
    <div class="mod-stat-card-label">of organisations using AI have experienced at least one negative consequence (McKinsey 2025)</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">1,450+</div>
    <div class="mod-stat-card-label">legal cases worldwide involving AI hallucinations identified in court records as of 2026</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">0.7%–25%</div>
    <div class="mod-stat-card-label">hallucination rate range across current models — best is Gemini Flash at 0.7%, worst exceed 25%</div>
  </div>
</div>

These are not edge cases. They are the normal operational reality of AI tools in 2026. Knowing this is not a reason to avoid AI — it is a reason to use it with a clear understanding of where it fails.

---

## Risk 1: Hallucination

Hallucination is the most misunderstood AI failure mode. It is not a bug in the traditional sense — it is a structural consequence of how LLMs work.

Recall from Module 1.1: LLMs predict the next word based on patterns in training data. When asked about something outside their training data, or something they were not trained on reliably, they do not say "I don't know." They predict the most statistically plausible next words — which can result in a fluent, confident, completely false response.

<div class="mod-warning">
<strong>Critical to understand:</strong> An AI hallucination does not look like a mistake. It looks like a correct answer. The model uses perfect grammar, cites plausible-sounding sources, and states false information with full confidence. This is what makes it dangerous.
</div>

### Real-world hallucination cases

<div class="mod-case">
<div class="mod-case-header" style="background:#c62828">CASE 1 — The Lawyer Who Cited Fake Cases (USA, 2023–ongoing)</div>
<div class="mod-case-body">
<p>A New York attorney used ChatGPT to research legal precedents for a court filing. The AI generated citations to six legal cases — complete with realistic case names, court names, dates, and legal reasoning. None of the cases existed. When the opposing side challenged the citations, the lawyer claimed he did not know ChatGPT was a generative tool rather than a legal database.</p>
<p>A federal judge issued a standing order requiring all attorneys appearing before the court to certify that AI was not used to draft filings, or to flag any AI-drafted language for accuracy review. As of 2026, over 1,450 similar cases have been identified in court records worldwide.</p>
</div>
<div class="mod-case-lesson"><strong>Lesson for you:</strong> Never cite a source you found via AI without independently verifying that source exists and says what the AI claims it says.</div>
</div>

<div class="mod-case">
<div class="mod-case-header" style="background:#c62828">CASE 2 — The Fake Reading List (Chicago Sun-Times, 2025)</div>
<div class="mod-case-body">
<p>A publisher used AI to generate a "Summer Reading List for 2025" that was syndicated to the Chicago Sun-Times. Readers discovered that 10 out of 15 recommended books were entirely fabricated — non-existent titles attributed to real, well-known authors. The titles sounded plausible, the author attributions were correct, but the books did not exist.</p>
<p>The newspaper removed the list from its online edition, but readers who had already received the printed version had paid for content that was largely fiction presented as fact.</p>
</div>
<div class="mod-case-lesson"><strong>Lesson for you:</strong> When AI recommends specific books, papers, tools, or resources by name — verify they exist before sharing or citing them.</div>
</div>

<div class="mod-case">
<div class="mod-case-header" style="background:#e65c00">CASE 3 — Stanford Legal AI Study (2025)</div>
<div class="mod-case-body">
<p>Stanford researchers asked multiple LLMs about legal precedents in a controlled study. The models collectively invented over 120 non-existent court cases — complete with convincingly realistic names, dates, courts, and detailed (but entirely fabricated) legal reasoning. Notably, even purpose-built legal AI tools designed specifically for legal research still hallucinated on 17% to 34% of challenging queries.</p>
</div>
<div class="mod-case-lesson"><strong>Lesson for you:</strong> Domain-specific AI tools are better but not reliable enough to trust without verification. This applies equally to code, medical information, financial data, and technical specifications.</div>
</div>

### Why hallucination rates vary

<div class="img-center"><svg width="680" viewBox="0 0 680 160" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Hallucination rates vary by model and use case — best models are around 0.7 percent, worst exceed 25 percent</title>
<rect x="0" y="0" width="680" height="160" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="340" y="22" text-anchor="middle" font-size="11" font-weight="700" fill="#555" font-family="sans-serif">HALLUCINATION RATES BY MODEL — lower is better (Vectara benchmark 2025)</text>
<!-- Labels -->
<text x="16" y="52" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">Gemini 2.0 Flash</text>
<text x="16" y="80" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">Claude Sonnet</text>
<text x="16" y="108" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">GPT-4o</text>
<text x="16" y="136" font-size="11" font-weight="600" fill="#333" font-family="sans-serif">Weaker models</text>
<!-- Bars -->
<rect x="160" y="40" width="9" height="20" rx="3" fill="#2e7d32"/>
<text x="174" y="53" font-size="11" fill="#2e7d32" font-weight="700" font-family="sans-serif">0.7%</text>
<rect x="160" y="68" width="30" height="20" rx="3" fill="#FF8C00"/>
<text x="195" y="81" font-size="11" fill="#FF8C00" font-weight="700" font-family="sans-serif">~3%</text>
<rect x="160" y="96" width="50" height="20" rx="3" fill="#FF8C00"/>
<text x="215" y="109" font-size="11" fill="#FF8C00" font-weight="700" font-family="sans-serif">~5–10%</text>
<rect x="160" y="124" width="250" height="20" rx="3" fill="#c62828"/>
<text x="415" y="137" font-size="11" fill="#c62828" font-weight="700" font-family="sans-serif">up to 25%+</text>
<!-- Note -->
<text x="340" y="152" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">A 5% rate means 1 in 20 responses contains a fabricated or incorrect claim</text>
</svg></div>

Even the best models hallucinate. Gemini Flash's 0.7% rate means roughly 1 in 143 responses contains a fabricated element. In a 50-response work session, you can statistically expect at least one hallucination — and you will not know which one unless you verify.

---

## Risk 2: AI Bias

AI bias occurs when a model produces outputs that systematically favour or disadvantage certain groups — based on imbalances, stereotypes, or gaps in its training data.

<div class="mod-risk-grid">
  <div class="mod-risk-card" style="background:#fff8e1;border-color:#ffe082">
    <h3 style="color:#f57f17">What causes bias in AI?</h3>
    <p>Training data reflects the real world — including its inequalities. If training data contains more examples of men as engineers or certain groups in negative contexts, the model learns those patterns. It is not intentional — it is statistical inheritance from historical data.</p>
  </div>
  <div class="mod-risk-card" style="background:#fff8e1;border-color:#ffe082">
    <h3 style="color:#f57f17">Where does it show up in Indian IT work?</h3>
    <p>CV screening tools that favour certain name patterns or universities. Code generation that defaults to Western libraries or approaches. Customer service AI that performs differently across languages. Resume feedback that differs based on implicit demographic signals in writing style.</p>
  </div>
  <div class="mod-risk-card" style="background:#ffeaea;border-color:#ef9a9a">
    <h3 style="color:#c62828">Why it matters in India specifically</h3>
    <p>India's AI Governance Guidelines 2025 explicitly address algorithmic bias. The Constitution's equality provisions apply — biased AI outputs affecting Indian citizens can trigger regulatory scrutiny under the Consumer Protection Act, 2019 and the DPDP Act, 2023.</p>
  </div>
  <div class="mod-risk-card" style="background:#ffeaea;border-color:#ef9a9a">
    <h3 style="color:#c62828">What you should do</h3>
    <p>Do not rely on AI outputs in hiring, performance review, or access decisions without human review. If you are building AI tools as a developer, test outputs across diverse inputs. Flag unexpected patterns to your team lead — this is increasingly a compliance issue, not just an ethics one.</p>
  </div>
</div>

---

## Risk 3: Data Privacy

This is the risk most Indian IT professionals underestimate — and it has direct legal consequences under India's new data protection law.

<div class="mod-warning">
<strong>Never paste client data, personal information, or confidential company information into a public AI tool.</strong> When you type into ChatGPT, Claude, or Gemini on their consumer tiers, your input may be used to improve the model. A message containing a client's Aadhar number, medical record, salary information, or trade secret could become part of training data accessible to others.
</div>

<div class="mod-law">
<div class="mod-law-title">INDIA'S AI GOVERNANCE — WHAT YOU NEED TO KNOW AS AN IT PROFESSIONAL</div>
<div class="mod-law-item">
  <span class="mod-law-badge">DPDP 2023</span>
  <span class="mod-law-text"><strong>Digital Personal Data Protection Act, 2023</strong> — India's primary data protection law. Requires consent for processing personal data. Using someone's personal data as AI input without their consent may violate this Act. Your employer's data handling policies are built around this law.</span>
</div>
<div class="mod-law-item">
  <span class="mod-law-badge">AI GOV 2025</span>
  <span class="mod-law-text"><strong>India's AI Governance Guidelines 2025</strong> — Require AI systems used in India to avoid bias, label AI-generated content, and maintain accountability for AI outputs. Platform obligations are now defined — companies deploying AI tools are responsible for their outputs.</span>
</div>
<div class="mod-law-item">
  <span class="mod-law-badge">COPYRIGHT</span>
  <span class="mod-law-text"><strong>Copyright Act + AI</strong> — DPIIT set up an expert committee in April 2025 to examine whether training AI on copyrighted works requires licensing. Until India's AI Bill is passed, the legal status of AI-generated content and training data remains evolving. Do not assume AI-generated code or content is automatically copyright-free for commercial use.</span>
</div>
<div class="mod-law-item">
  <span class="mod-law-badge">ERASURE</span>
  <span class="mod-law-text"><strong>Right to Erasure challenge</strong> — Under the DPDP Act's right to erasure, if a user revokes data consent, you may be legally required to remove their data from an AI model — a technically complex "machine unlearning" problem that is already creating compliance challenges for Indian fintech and SaaS companies.</span>
</div>
</div>

---

## Risk 4: Copyright and Intellectual Property

<div class="mod-keypoint">
<strong>The key question:</strong> When an AI generates code, an image, or a document — who owns it? In India in 2026, the honest answer is: nobody is completely sure yet.
</div>

Here is what is known and what remains unsettled:

**AI-generated code** — if you use GitHub Copilot or Claude to generate code at work, your employer likely owns that code under your employment agreement. However, if the generated code reproduces a segment from an open-source library with an incompatible licence (which Copilot has been found to do), your company could face a licence violation.

**AI-generated written content** — India's Copyright Act 1957 protects works created by human authors. Content generated entirely by AI currently has uncertain copyright status in India. DPIIT's April 2025 expert committee concluded that no existing international approach perfectly balances creators' rights with AI innovation.

**The practical rule for freshers** — when using AI to generate work product for a client or employer, always disclose that AI was used, always review the output for licence-incompatible code, and always follow your company's AI usage policy. Most major Indian IT companies have published internal AI usage guidelines in 2025–2026.

---

## Responsible use — the practical checklist

<div class="mod-checklist">
<div class="mod-checklist-title">BEFORE SUBMITTING ANY AI-ASSISTED WORK</div>
<div class="mod-checklist-item">
  <div class="mod-checklist-num">1</div>
  <div class="mod-checklist-text"><strong>Verify every specific fact, number, name, date, or citation</strong> independently. Do not assume AI is correct because it sounds confident. Look it up.</div>
</div>
<div class="mod-checklist-item">
  <div class="mod-checklist-num">2</div>
  <div class="mod-checklist-text"><strong>Never paste confidential client data, personal information, or trade secrets</strong> into a consumer AI tool. Use your company's approved enterprise AI tool if one is available.</div>
</div>
<div class="mod-checklist-item">
  <div class="mod-checklist-num">3</div>
  <div class="mod-checklist-text"><strong>Disclose AI use</strong> when submitting work to clients, managers, or academic institutions. Many now have explicit policies — follow them.</div>
</div>
<div class="mod-checklist-item">
  <div class="mod-checklist-num">4</div>
  <div class="mod-checklist-text"><strong>Review AI-generated code for licence compatibility</strong> before committing to a client repository. A hallucinated open-source library or an incompatible licence can create legal exposure.</div>
</div>
<div class="mod-checklist-item">
  <div class="mod-checklist-num">5</div>
  <div class="mod-checklist-text"><strong>Check outputs for bias</strong> when AI is used in any decision-affecting context — screening, summarising, or categorising information about people.</div>
</div>
<div class="mod-checklist-item">
  <div class="mod-checklist-num">6</div>
  <div class="mod-checklist-text"><strong>Know your company's AI policy</strong> — TCS, Infosys, Wipro, and HCL all have internal guidelines on approved tools, data handling, and disclosure requirements. Read yours on Day 1.</div>
</div>
</div>

---

## Dos and don'ts for Indian IT freshers

<div class="mod-dos-grid">
<div class="mod-dos-col" style="border-color:#a5d6a7">
  <div class="mod-dos-header" style="background:#e8f5e9;color:#2e7d32">✓ DO THESE</div>
  <ul class="mod-dos-list mod-do">
    <li>Use AI to speed up first drafts — then edit carefully</li>
    <li>Verify every fact, citation, and statistic independently</li>
    <li>Disclose AI use when your employer or institution requires it</li>
    <li>Use Gemini with search grounding when you need current facts</li>
    <li>Read your company's AI usage policy on Day 1</li>
    <li>Use enterprise-approved AI tools for client work</li>
    <li>Flag AI-generated content that seems biased or inconsistent</li>
    <li>Keep learning — AI tools change fast and so do the rules</li>
  </ul>
</div>
<div class="mod-dos-col" style="border-color:#ef9a9a">
  <div class="mod-dos-header" style="background:#ffeaea;color:#c62828">✗ NEVER DO THESE</div>
  <ul class="mod-dos-list mod-dont">
    <li>Paste client data or personal information into consumer AI tools</li>
    <li>Submit AI output without reviewing it for factual accuracy</li>
    <li>Cite AI-generated sources without verifying they exist</li>
    <li>Assume AI-generated code is licence-compatible without checking</li>
    <li>Use AI output in hiring or access decisions without human review</li>
    <li>Claim AI-generated work as entirely your own when disclosure is required</li>
    <li>Rely on AI for medical, legal, or financial advice without expert verification</li>
    <li>Assume the same rules apply globally — India's laws are evolving fast</li>
  </ul>
</div>
</div>

---

## Why responsible use is a career advantage, not a burden

Here is the counterintuitive truth: being the person on your team who understands AI risks makes you *more* valuable — not less.

Indian IT companies deploying GenAI at scale are desperately looking for people who can serve as "responsible AI practitioners" — developers and analysts who understand both the capability and the failure modes. TCS's agentic AI solutions and Wipro's AI-powered operating model both require humans in the loop to review, validate, and govern AI outputs. That human-in-the-loop role is a well-paid, high-trust position.

<div class="mod-keypoint">
<strong>The career opportunity:</strong> Being the fresher who asks "did we verify this AI output?" and "does this comply with our data policy?" is not being cautious — it is demonstrating exactly the professional judgement that companies are struggling to find. Responsible AI use is not the opposite of being AI-savvy. It is the next level of it.
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 1.4</div>
  <ol>
    <li><strong>Hallucination is structural, not a bug</strong> — all LLMs fabricate facts at some rate (0.7% to 25%+). Confident delivery does not mean correct content. Always verify specific facts, citations, names, and data independently before using AI output in professional work.</li>
    <li><strong>Data privacy has legal teeth in India</strong> — the DPDP Act 2023 and India's AI Governance Guidelines 2025 create real compliance obligations. Never paste confidential or personal data into consumer AI tools. Know your company's AI policy before using any AI tool on client work.</li>
    <li><strong>Responsible use is a career advantage</strong> — the most valued AI practitioners are not the ones who use AI most, but the ones who combine AI capability with the judgement to catch its failures. That human-in-the-loop role is what Indian IT companies are actively hiring for right now.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-14">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 1.4 — Catch an AI Hallucination</h3>
  </div>
  <p>The best way to understand hallucination is to experience it firsthand. This assignment takes 15–20 minutes.</p>
  <ol>
    <li><strong>Open any AI tool</strong> — ChatGPT, Claude, or Gemini (free tier is fine).</li>
    <li><strong>Ask it a specific factual question</strong> in your area of study or interest. Examples:
      <ul>
        <li>"What are the top 5 research papers on [your specialisation] published in the last 2 years? Give me titles, authors, and journal names."</li>
        <li>"What are the exact eligibility criteria for [a specific government scheme or exam you know about]?"</li>
        <li>"Who won the [specific recent award or competition in your field] in 2025?"</li>
      </ul>
    </li>
    <li><strong>Verify every specific claim</strong> the AI makes — look up each paper title, check each author name, confirm each statistic independently online.</li>
    <li><strong>Document what you find</strong> — how many of the AI's specific claims were correct? How many were partially correct? How many were completely fabricated?</li>
    <li><strong>Write 3 sentences</strong> describing what you found and what it tells you about how to use AI responsibly in your work going forward.</li>
  </ol>
  <p>This assignment completes Unit 1. You now have a foundational understanding of what GenAI is, which tools to use, how Indian companies are using it, and how to use it responsibly. Unit 2 builds on all of this — you will start writing prompts that actually work.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit1/module-1-3-how-indian-companies-use-genai/">&#8592; Module 1.3: How Indian Companies Use GenAI</a>
  <a class="mod-nav-next" href="/courses/genai/unit2/module-2-1-anatomy-of-a-good-prompt/">Unit 2: Prompt Engineering Basics &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>51% of organisations experienced AI negative consequences</td><td>McKinsey 2025 Global Survey on AI</td></tr>
      <tr><td>1,450+ legal hallucination cases in court records</td><td>Damien Charlotin AI Hallucination Cases database, 2026</td></tr>
      <tr><td>Hallucination rates 0.7%–25%+</td><td>Vectara hallucination benchmark; allaboutai.com 2025</td></tr>
      <tr><td>Gemini 2.0 Flash 0.7% hallucination rate</td><td>Vectara benchmark, April 2025</td></tr>
      <tr><td>Mata v. Avianca lawyer/fake cases incident</td><td>MIT Sloan; multiple legal publications 2023–2025</td></tr>
      <tr><td>Chicago Sun-Times fake reading list</td><td>evidentlyai.com AI hallucination examples 2025</td></tr>
      <tr><td>Stanford 120+ invented court cases study</td><td>Stanford HAI; allaboutai.com 2025</td></tr>
      <tr><td>Legal AI hallucination 17%–34% rate</td><td>Stanford HAI 2025 legal AI study</td></tr>
      <tr><td>India DPDP Act 2023 and AI Governance Guidelines 2025</td><td>indialaw.in AI governance analysis November 2025</td></tr>
      <tr><td>DPIIT copyright expert committee April 2025</td><td>The Regulatory Review, February 2026</td></tr>
      <tr><td>India AI Bill expected to codify guidelines</td><td>indialaw.in AI governance analysis November 2025</td></tr>
    </tbody>
  </table>
</details>

</div>
