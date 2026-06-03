---
title: "Module 1.2: ChatGPT vs Claude vs Gemini — Which to Use When"
description: "A practical comparison of ChatGPT, Claude, and Gemini for Indian students and IT professionals — free tiers, India pricing, strengths, and which tool to use for what task."
weight: 2
sidebar: false
tags: ["chatgpt", "claude", "gemini", "ai-tools", "india", "comparison", "generative-ai"]
---

<style>
/* ── Module header bar ───────────────────────────────────────── */
.mod-header{background:#1565C0;border-radius:6px;padding:14px 18px;margin-bottom:24px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px}
.mod-header-left{display:flex;flex-direction:column;gap:4px}
.mod-breadcrumb{font-size:11px;color:rgba(255,255,255,0.75);letter-spacing:0.03em}
.mod-title-inline{font-size:15px;font-weight:600;color:#fff;margin:0}
.mod-meta{display:flex;gap:10px;flex-wrap:wrap}
.mod-meta-item{font-size:11px;color:rgba(255,255,255,0.85);background:rgba(255,255,255,0.15);padding:3px 10px;border-radius:20px}
/* ── Section callout boxes ───────────────────────────────────── */
.mod-keypoint{background:#fff8e1;border-left:4px solid #FF8C00;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0;font-size:14px;color:#4a3000;line-height:1.6}
.mod-keypoint strong{color:#FF8C00}
.mod-remember{background:#e8f0fe;border-left:4px solid #1565C0;border-radius:0 6px 6px 0;padding:12px 16px;margin:20px 0}
.mod-remember-title{font-size:11px;font-weight:700;color:#1565C0;letter-spacing:0.06em;margin-bottom:8px}
.mod-remember ol{margin:0;padding-left:18px}
.mod-remember li{font-size:14px;color:#1a1a1a;line-height:1.7;margin-bottom:4px}
/* ── Tool profile cards ──────────────────────────────────────── */
.mod-tool-card{border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:24px 0}
.mod-tool-header{padding:14px 18px;display:flex;align-items:center;gap:12px}
.mod-tool-badge{width:40px;height:40px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0;font-weight:700;color:#fff}
.mod-tool-name{font-size:16px;font-weight:700;color:#fff;margin:0}
.mod-tool-tagline{font-size:12px;color:rgba(255,255,255,0.85);margin:2px 0 0}
.mod-tool-body{padding:16px 18px;background:#fff}
.mod-tool-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:14px}
.mod-tool-section-title{font-size:11px;font-weight:700;letter-spacing:0.06em;color:#888;margin-bottom:6px}
.mod-tool-list{margin:0;padding-left:16px}
.mod-tool-list li{font-size:13px;color:#333;line-height:1.7}
.mod-tool-india{background:#f9f9f9;border-top:1px solid #f0f0f0;padding:12px 18px;display:flex;align-items:center;gap:8px}
.mod-tool-india-label{font-size:11px;font-weight:700;color:#888;letter-spacing:0.05em;flex-shrink:0}
.mod-tool-india-text{font-size:13px;color:#333;line-height:1.5}
/* ── Comparison table ────────────────────────────────────────── */
.mod-table-wrap{overflow-x:auto;margin:20px 0}
.mod-table{width:100%;border-collapse:collapse;font-size:13px}
.mod-table th{background:#1565C0;color:#fff;padding:10px 13px;text-align:left;font-weight:600;font-size:12px}
.mod-table td{padding:10px 13px;border-bottom:1px solid #f0f0f0;color:#333;vertical-align:top}
.mod-table tr:last-child td{border-bottom:none}
.mod-table tr:nth-child(even) td{background:#fafafa}
.mod-table td:first-child{font-weight:600;color:#1565C0;white-space:nowrap}
.badge-best{display:inline-block;font-size:10px;font-weight:700;padding:2px 7px;border-radius:10px;background:#e8f5e9;color:#2e7d32;border:1px solid #a5d6a7;margin-left:4px}
/* ── Use case decision box ───────────────────────────────────── */
.mod-usecase{background:#fff;border:1px solid #e0e0e0;border-radius:8px;overflow:hidden;margin:20px 0}
.mod-usecase-header{background:#f5f5f4;padding:10px 16px;font-size:12px;font-weight:700;color:#555;letter-spacing:0.05em;border-bottom:1px solid #e0e0e0}
.mod-usecase-row{display:flex;align-items:flex-start;gap:12px;padding:11px 16px;border-bottom:1px solid #f5f5f5}
.mod-usecase-row:last-child{border-bottom:none}
.mod-usecase-task{font-size:13px;color:#333;font-weight:500;flex:1.2}
.mod-usecase-pick{font-size:13px;font-weight:700;flex:0.8}
.mod-usecase-why{font-size:12px;color:#666;flex:2;line-height:1.5}
/* ── Assignment box ──────────────────────────────────────────── */
.mod-assignment{background:#fff8e1;border:1px solid #FFB300;border-radius:6px;padding:16px 18px;margin:28px 0}
.mod-assignment-header{display:flex;align-items:center;gap:8px;margin-bottom:10px}
.mod-assignment-icon{font-size:16px;color:#FF8C00}
.mod-assignment-title{font-size:14px;font-weight:700;color:#5d4037;margin:0}
.mod-assignment p,.mod-assignment li{font-size:14px;color:#4a3000;line-height:1.7}
.mod-assignment ol,.mod-assignment ul{padding-left:20px;margin:8px 0}
/* ── Navigation footer ───────────────────────────────────────── */
.mod-nav{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px;margin-top:32px;padding-top:18px;border-top:1px solid #e0e0e0}
.mod-nav-back{font-size:13px;color:#1565C0;text-decoration:none;display:flex;align-items:center;gap:5px}
.mod-nav-back:hover{color:#0d47a1;text-decoration:underline}
.mod-nav-next{display:inline-flex;align-items:center;gap:6px;font-size:13px;font-weight:600;padding:9px 18px;border-radius:4px;background:#FF8C00;color:#fff !important;text-decoration:none}
.mod-nav-next:hover{background:#e65c00;color:#fff !important;text-decoration:none}
/* ── Blog links footer ───────────────────────────────────────── */
.mod-blog-links{background:#f9f9f9;border:1px solid #e0e0e0;border-radius:6px;padding:14px 18px;margin-top:20px}
.mod-blog-title{font-size:11px;font-weight:700;color:#888;letter-spacing:0.06em;margin-bottom:8px}
.mod-blog-links a{display:block;font-size:13px;color:#1565C0;text-decoration:none;padding:3px 0;border-bottom:1px solid #f0f0f0}
.mod-blog-links a:last-child{border-bottom:none}
.mod-blog-links a:hover{color:#FF8C00;text-decoration:underline}
/* ── Body text readability ───────────────────────────────────── */
.mod-wrap p,.mod-wrap li,.mod-wrap td{font-size:16px !important;color:#111111 !important;line-height:1.85 !important;font-weight:450}
.mod-wrap p{margin-bottom:1.1em}
@media(max-width:600px){
.mod-wrap p,.mod-wrap li,.mod-wrap td{font-size:16px !important;line-height:1.9 !important}
}
.mod-wrap h2{font-size:20px;color:#111;margin-top:32px;margin-bottom:12px}
.mod-wrap h3{font-size:17px;color:#111;margin-top:24px;margin-bottom:8px}
.mod-wrap strong{color:#111;font-weight:600}
.mod-wrap em{color:#333}
.mod-wrap code{font-size:14px;background:#f0f0f0;padding:2px 6px;border-radius:3px;color:#c62828}
/* ── Image credit table ──────────────────────────────────────── */
.mod-credits{font-size:12px;color:#888;margin-top:32px;padding-top:12px;border-top:1px solid #e0e0e0}
.mod-credits summary{cursor:pointer;font-size:12px;color:#aaa;list-style:none}
.mod-credits summary:hover{color:#888}
/* ── Centre-align all diagrams ───────────────────────────────── */
.img-center{display:flex;justify-content:center;margin:20px 0}
.img-center svg{max-width:100%;height:auto}
.img-center>div{max-width:680px;width:100%}
@media(max-width:520px){.mod-tool-grid{grid-template-columns:1fr}.mod-usecase-row{flex-direction:column;gap:4px}}
</style>

<div class="mod-wrap">
<div class="mod-header">
  <div class="mod-header-left">
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 1 &nbsp;›&nbsp; MODULE 2 OF 4</span>
    <h1 class="mod-title-inline">ChatGPT vs Claude vs Gemini — Which to Use When</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Requires Module 1.1</span>
  </div>
</div>

In Module 1.1 you learned that all three tools — ChatGPT, Claude, and Gemini — are built on Large Language Models that predict the next word. So if they all work the same way under the hood, why does it matter which one you use?

It matters a lot. Each tool has genuinely different strengths, free tier limits, and India-specific pricing. Choosing the wrong tool for a task does not just give you worse output — it can cost you time, money, and credibility when the output is wrong.

By the end of this module you will know exactly which tool to open for which task — and why.

---

## The three tools at a glance

Before going deep, here is the honest one-line summary for each:

<div class="mod-keypoint">
<strong>ChatGPT</strong> — the most versatile all-rounder. Best for everyday tasks, voice, and India-friendly pricing.<br>
<strong>Claude</strong> — the best for coding, long documents, and nuanced writing. Harder to access from India.<br>
<strong>Gemini</strong> — the best for research, live information, and Google Workspace integration.
</div>

Now let us go deeper on each one.

---

## ChatGPT (OpenAI)

<div class="mod-tool-card">
<div class="mod-tool-header" style="background:#10a37f">
  <div class="mod-tool-badge" style="background:rgba(255,255,255,0.2)">G</div>
  <div>
    <div class="mod-tool-name">ChatGPT</div>
    <div class="mod-tool-tagline">by OpenAI &nbsp;·&nbsp; Best all-rounder for Indian users</div>
  </div>
</div>
<div class="mod-tool-body">
  <div class="mod-tool-grid">
    <div>
      <div class="mod-tool-section-title">STRENGTHS</div>
      <ul class="mod-tool-list">
        <li>Most versatile — handles text, images, code, voice, and data</li>
        <li>Largest ecosystem — plugins, GPTs, integrations</li>
        <li>Voice mode is natural and fast</li>
        <li>Web browsing built in (free and paid)</li>
        <li>Best for quick everyday tasks — emails, summaries, drafts</li>
        <li>64.5% global AI traffic share — most tutorials use it</li>
      </ul>
    </div>
    <div>
      <div class="mod-tool-section-title">LIMITATIONS</div>
      <ul class="mod-tool-list">
        <li>Free tier has daily usage caps</li>
        <li>Can be overconfident — hallucinates more than Claude</li>
        <li>Long document analysis weaker than Claude</li>
        <li>Coding quality good but behind Claude for complex tasks</li>
      </ul>
    </div>
  </div>
  <div class="mod-tool-section-title">INDIA PRICING</div>
  <div class="mod-tool-list" style="margin-bottom:12px">
    <ul class="mod-tool-list">
      <li><strong>Free tier:</strong> Available — GPT-4o with daily limits, web browsing included</li>
      <li><strong>ChatGPT Go:</strong> ₹399/month — free until December 2026 for new users</li>
      <li><strong>ChatGPT Plus:</strong> ₹1,999/month — full GPT-4o access, higher limits</li>
      <li><strong>Payment:</strong> UPI accepted, INR billing, no forex charges</li>
    </ul>
  </div>
</div>
<div class="mod-tool-india">
  <span class="mod-tool-india-label">FOR STUDENTS:</span>
  <span class="mod-tool-india-text">The ₹399 Go plan (currently free) makes ChatGPT the most accessible paid option for Indian students. Start here if you are new to AI tools.</span>
</div>
</div>

---

## Claude (Anthropic)

<div class="mod-tool-card">
<div class="mod-tool-header" style="background:#c97c5d">
  <div class="mod-tool-badge" style="background:rgba(255,255,255,0.2)">C</div>
  <div>
    <div class="mod-tool-name">Claude</div>
    <div class="mod-tool-tagline">by Anthropic &nbsp;·&nbsp; Best for coding and long documents</div>
  </div>
</div>
<div class="mod-tool-body">
  <div class="mod-tool-grid">
    <div>
      <div class="mod-tool-section-title">STRENGTHS</div>
      <ul class="mod-tool-list">
        <li>Best-in-class for complex coding and large codebase understanding</li>
        <li>200,000 token context window — can process entire codebases or long reports</li>
        <li>Writes in a natural, human-like tone — less "AI-sounding"</li>
        <li>Excellent at nuanced reasoning and multi-step problems</li>
        <li>Least likely to hallucinate among the three</li>
        <li>Claude Code is the leading agentic coding tool in 2026</li>
      </ul>
    </div>
    <div>
      <div class="mod-tool-section-title">LIMITATIONS</div>
      <ul class="mod-tool-list">
        <li>Free tier hits message limits quickly during peak hours</li>
        <li>No UPI — must pay in USD with international card</li>
        <li>No built-in voice mode</li>
        <li>Less ecosystem integrations than ChatGPT</li>
        <li>18% GST + forex buffer makes it the most expensive for Indian users</li>
      </ul>
    </div>
  </div>
  <div class="mod-tool-section-title">INDIA PRICING</div>
  <div class="mod-tool-list" style="margin-bottom:12px">
    <ul class="mod-tool-list">
      <li><strong>Free tier:</strong> Available but message-limited, especially during peak hours</li>
      <li><strong>Claude Pro:</strong> $20/month ≈ ₹2,240/month (USD billing + 18% GST + forex)</li>
      <li><strong>Payment:</strong> No UPI, no INR billing — international credit/debit card only</li>
    </ul>
  </div>
</div>
<div class="mod-tool-india">
  <span class="mod-tool-india-label">FOR STUDENTS:</span>
  <span class="mod-tool-india-text">Use the free tier for coding help and document analysis. The payment barrier makes the paid plan less accessible — prioritise when you need serious coding or long-document work.</span>
</div>
</div>

---

## Gemini (Google)

<div class="mod-tool-card">
<div class="mod-tool-header" style="background:#1a73e8">
  <div class="mod-tool-badge" style="background:rgba(255,255,255,0.2)">G</div>
  <div>
    <div class="mod-tool-name">Gemini</div>
    <div class="mod-tool-tagline">by Google &nbsp;·&nbsp; Best for research and Google Workspace</div>
  </div>
</div>
<div class="mod-tool-body">
  <div class="mod-tool-grid">
    <div>
      <div class="mod-tool-section-title">STRENGTHS</div>
      <ul class="mod-tool-list">
        <li>Native Google Search grounding — real-time information by default</li>
        <li>Best for research, current events, and fact-checking</li>
        <li>Deep Google Workspace integration — works inside Gmail, Docs, Sheets</li>
        <li>1 million token context window in Pro tier</li>
        <li>Most generous free tier among the three</li>
        <li>Cheapest API rates — relevant if you start building</li>
      </ul>
    </div>
    <div>
      <div class="mod-tool-section-title">LIMITATIONS</div>
      <ul class="mod-tool-list">
        <li>Writing quality slightly less polished than Claude</li>
        <li>Coding not as strong as Claude for complex tasks</li>
        <li>Can feel inconsistent across different query types</li>
        <li>Ultra tier (₹24,999/month) is overkill for most students</li>
      </ul>
    </div>
  </div>
  <div class="mod-tool-section-title">INDIA PRICING</div>
  <div class="mod-tool-list" style="margin-bottom:12px">
    <ul class="mod-tool-list">
      <li><strong>Free tier:</strong> Most generous — Gemini 2.0 Flash access, no daily hard cap</li>
      <li><strong>Gemini AI Plus:</strong> ₹399/month — competitive with ChatGPT Go</li>
      <li><strong>Gemini AI Pro:</strong> ₹1,950/month — 50% off first year for new subscribers (≈ ₹975/month effective)</li>
      <li><strong>Payment:</strong> UPI accepted, INR billing, GST included in displayed price</li>
    </ul>
  </div>
</div>
<div class="mod-tool-india">
  <span class="mod-tool-india-label">FOR STUDENTS:</span>
  <span class="mod-tool-india-text">If you use Gmail, Google Docs, or Google Drive daily, Gemini is the most frictionless choice. The 50% first-year discount on AI Pro makes it the best value paid plan right now.</span>
</div>
</div>

---

## Side-by-side comparison

<div class="mod-table-wrap">
<table class="mod-table">
<thead>
  <tr>
    <th>Feature</th>
    <th>ChatGPT</th>
    <th>Claude</th>
    <th>Gemini</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Best for</td>
    <td>Everyday tasks, voice, versatility</td>
    <td>Coding, long docs, nuanced writing</td>
    <td>Research, live info, Google tools</td>
  </tr>
  <tr>
    <td>Free tier</td>
    <td>Yes — daily limited</td>
    <td>Yes — message limited</td>
    <td>Yes — most generous <span class="badge-best">BEST</span></td>
  </tr>
  <tr>
    <td>Paid plan (India)</td>
    <td>₹399 Go (free till Dec 2026) / ₹1,999 Plus</td>
    <td>≈ ₹2,240/mo (USD only)</td>
    <td>₹399 Plus / ₹1,950 Pro <span class="badge-best">BEST VALUE</span></td>
  </tr>
  <tr>
    <td>UPI / INR billing</td>
    <td>Yes ✓</td>
    <td>No ✗</td>
    <td>Yes ✓</td>
  </tr>
  <tr>
    <td>Coding quality</td>
    <td>Good</td>
    <td>Excellent <span class="badge-best">BEST</span></td>
    <td>Good</td>
  </tr>
  <tr>
    <td>Context window</td>
    <td>128K tokens</td>
    <td>200K tokens <span class="badge-best">BEST</span></td>
    <td>1M tokens (Pro)</td>
  </tr>
  <tr>
    <td>Live web search</td>
    <td>Yes (free + paid)</td>
    <td>Limited</td>
    <td>Yes — native <span class="badge-best">BEST</span></td>
  </tr>
  <tr>
    <td>Voice mode</td>
    <td>Yes — natural</td>
    <td>No</td>
    <td>Basic</td>
  </tr>
  <tr>
    <td>Google Workspace</td>
    <td>No</td>
    <td>No</td>
    <td>Yes — deep integration <span class="badge-best">BEST</span></td>
  </tr>
  <tr>
    <td>Hallucination rate</td>
    <td>Moderate</td>
    <td>Lowest <span class="badge-best">BEST</span></td>
    <td>Moderate</td>
  </tr>
</tbody>
</table>
</div>

---

## Which tool for which task?

This is the section that will save you the most time. Stop debating which is "better" — they are all excellent. Ask instead: *what am I trying to do right now?*

<div class="mod-usecase">
<div class="mod-usecase-header">TASK &nbsp;→&nbsp; BEST TOOL &nbsp;→&nbsp; REASON</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Write or debug code</span>
  <span class="mod-usecase-pick" style="color:#c97c5d">Claude</span>
  <span class="mod-usecase-why">Best code understanding, lowest hallucination, handles large codebases in one context</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Research a topic or current event</span>
  <span class="mod-usecase-pick" style="color:#1a73e8">Gemini</span>
  <span class="mod-usecase-why">Native Google Search grounding — answers are tied to live sources, not training data</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Draft an email or report</span>
  <span class="mod-usecase-pick" style="color:#10a37f">ChatGPT</span>
  <span class="mod-usecase-why">Most versatile writer, vast prompt library in the ecosystem, voice input for quick drafts</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Summarise a long PDF or report</span>
  <span class="mod-usecase-pick" style="color:#c97c5d">Claude</span>
  <span class="mod-usecase-why">200K token context — can process entire documents in one go without chunking</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Work in Gmail or Google Docs</span>
  <span class="mod-usecase-pick" style="color:#1a73e8">Gemini</span>
  <span class="mod-usecase-why">Integrated natively — no copy-paste needed, works inside the apps you already have</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Quick question or lookup</span>
  <span class="mod-usecase-pick" style="color:#10a37f">ChatGPT</span>
  <span class="mod-usecase-why">Fastest and most familiar; the ecosystem of tutorials means help is always one search away</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Explain a complex concept clearly</span>
  <span class="mod-usecase-pick" style="color:#c97c5d">Claude</span>
  <span class="mod-usecase-why">Writes in the most natural, least "AI-sounding" style — explanations feel genuinely clear</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Interview preparation</span>
  <span class="mod-usecase-pick" style="color:#10a37f">ChatGPT</span>
  <span class="mod-usecase-why">Huge library of role-specific prompts in the community; voice mode lets you practice spoken answers</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Fact-check an important claim</span>
  <span class="mod-usecase-pick" style="color:#1a73e8">Gemini</span>
  <span class="mod-usecase-why">Search grounding means you get citations. Never rely on ChatGPT or Claude alone for fact-checking</span>
</div>
<div class="mod-usecase-row">
  <span class="mod-usecase-task">Prepare for campus placements</span>
  <span class="mod-usecase-pick" style="color:#10a37f">ChatGPT</span>
  <span class="mod-usecase-why">Most placement prep content online is built around ChatGPT prompts — easier to follow guides</span>
</div>
</div>

---

## A practical setup for Indian students

You do not need to pay for any of these tools to get significant value. Here is the free setup that covers most use cases:

<div class="img-center"><svg width="680" viewBox="0 0 680 200" style="display:block;width:100%;height:auto" role="img" xmlns="http://www.w3.org/2000/svg">
<title>Recommended free tool setup for Indian students: ChatGPT for everyday tasks, Claude for coding and long docs, Gemini for research and Google tools</title>
<rect x="0" y="0" width="680" height="200" rx="8" fill="#f9f9f9" stroke="#e0e0e0" stroke-width="1"/>
<text x="340" y="26" text-anchor="middle" font-size="12" font-weight="700" fill="#555" font-family="sans-serif">RECOMMENDED FREE SETUP FOR INDIAN STUDENTS</text>
<!-- ChatGPT card -->
<rect x="20" y="44" width="198" height="140" rx="8" fill="#fff" stroke="#10a37f" stroke-width="1.5"/>
<rect x="20" y="44" width="198" height="38" rx="8" fill="#10a37f"/>
<rect x="20" y="68" width="198" height="14" fill="#10a37f"/>
<text x="119" y="68" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" font-family="sans-serif">ChatGPT (Free)</text>
<text x="119" y="100" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Everyday writing tasks</text>
<text x="119" y="118" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Email and report drafts</text>
<text x="119" y="136" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Interview prep (voice mode)</text>
<text x="119" y="154" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Quick questions and lookups</text>
<text x="119" y="176" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">chat.openai.com</text>
<!-- Claude card -->
<rect x="241" y="44" width="198" height="140" rx="8" fill="#fff" stroke="#c97c5d" stroke-width="1.5"/>
<rect x="241" y="44" width="198" height="38" rx="8" fill="#c97c5d"/>
<rect x="241" y="68" width="198" height="14" fill="#c97c5d"/>
<text x="340" y="68" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" font-family="sans-serif">Claude (Free)</text>
<text x="340" y="100" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Coding help and debugging</text>
<text x="340" y="118" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Long PDF summarisation</text>
<text x="340" y="136" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Complex explanations</text>
<text x="340" y="154" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Nuanced writing and editing</text>
<text x="340" y="176" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">claude.ai</text>
<!-- Gemini card -->
<rect x="462" y="44" width="198" height="140" rx="8" fill="#fff" stroke="#1a73e8" stroke-width="1.5"/>
<rect x="462" y="44" width="198" height="38" rx="8" fill="#1a73e8"/>
<rect x="462" y="68" width="198" height="14" fill="#1a73e8"/>
<text x="561" y="68" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" font-family="sans-serif">Gemini (Free)</text>
<text x="561" y="100" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Research and fact-checking</text>
<text x="561" y="118" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Current events and news</text>
<text x="561" y="136" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Gmail and Google Docs tasks</text>
<text x="561" y="154" text-anchor="middle" font-size="11" fill="#444" font-family="sans-serif">Most generous free limits</text>
<text x="561" y="176" text-anchor="middle" font-size="10" fill="#888" font-family="sans-serif">gemini.google.com</text>
</svg></div>

All three have free tiers. Open accounts on all three today — the assignment will ask you to use them. As your usage grows, the first paid upgrade worth considering for most Indian students is the **ChatGPT Go plan at ₹399/month** (currently free), or the **Gemini AI Pro first-year discount at ≈ ₹975/month**.

---

## One important warning about all three

<div class="mod-keypoint">
<strong>None of these tools are reliable for factual claims without verification.</strong> ChatGPT hallucinates most frequently. Claude hallucinates least but still does. Gemini is the safest for current facts because it uses live search — but even then, always check the cited source directly. Never submit AI-generated content to your college or employer without verifying every specific fact, date, statistic, or name it mentions.
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 1.2</div>
  <ol>
    <li><strong>ChatGPT for everyday tasks</strong> — the most versatile all-rounder, best India pricing via UPI, best for placement prep and quick work.</li>
    <li><strong>Claude for code and long documents</strong> — lowest hallucination rate, best for serious coding tasks, handles 200K tokens in one go.</li>
    <li><strong>Gemini for research and Google tools</strong> — native search grounding gives live information, most generous free tier, best if you live in the Google ecosystem.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-12">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 1.2 — Try All Three on the Same Task</h3>
  </div>
  <p>This is a hands-on comparison exercise. You will use all three tools on the same prompt and observe the differences yourself.</p>
  <ol>
    <li><strong>Open all three tools</strong> — chat.openai.com, claude.ai, and gemini.google.com. All have free tiers.</li>
    <li><strong>Type this exact prompt into all three:</strong>
      <ul>
        <li><em>"Explain what a REST API is, give me a simple real-world analogy, and show me a 5-line Python example."</em></li>
      </ul>
    </li>
    <li><strong>Compare the outputs</strong> on these four dimensions:
      <ul>
        <li>Which explanation was clearest and easiest to understand?</li>
        <li>Which analogy felt most relatable?</li>
        <li>Which Python code was cleanest and most correct?</li>
        <li>Which response felt most natural — least "AI-sounding"?</li>
      </ul>
    </li>
    <li><strong>Write down your observations</strong> — 2–3 sentences per tool. Save this. You will notice your preferences shift as you use these tools more over the course.</li>
  </ol>
  <p>There is no right answer. The goal is to develop your own calibrated sense of what each tool is good at.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit1/module-1-1-what-is-generative-ai/">&#8592; Module 1.1: What is Generative AI</a>
  <a class="mod-nav-next" href="/courses/genai/unit1/module-1-3-how-indian-companies-use-genai/">Module 1.3: How Indian Companies Use GenAI &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Image credits and licences</summary>
  <table>
    <thead><tr><th>Visual</th><th>Type</th><th>Licence</th><th>Attribution</th></tr></thead>
    <tbody>
      <tr><td>Free tool setup diagram</td><td>Inline SVG — original</td><td>CC0</td><td>No</td></tr>
      <tr><td>Pricing data</td><td>Sourced from public pricing pages</td><td>Factual data</td><td>Cite respective companies</td></tr>
    </tbody>
  </table>
</details>

</div>
