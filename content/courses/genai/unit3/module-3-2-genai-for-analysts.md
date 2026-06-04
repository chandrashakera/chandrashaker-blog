---
title: "Module 3.2: GenAI for Analysts — Data Summarisation, Reports, and Insights"
description: "Practical guide to using GenAI for data analysis, report writing, SQL generation, and business insights — with real examples for Indian data analysts and freshers."
weight: 2
sidebar: false
mainroad_aside: false
tags: ["data-analysis", "sql", "python", "report-writing", "india", "analysts", "generative-ai"]
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
    <div class="mod-progress-fill" style="width:45%"></div>
  </div>
  <div style="font-size:12px;color:#FF8C00;font-weight:600;margin-bottom:10px">9 of 20 modules complete</div>
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
    <span class="mod-breadcrumb">GENERATIVE AI: ZERO TO JOB-READY &nbsp;›&nbsp; UNIT 3 &nbsp;›&nbsp; MODULE 2 OF 4</span>
    <h1 class="mod-title-inline">GenAI for Analysts — Data Summarisation, Reports, and Insights</h1>
  </div>
  <div class="mod-meta">
    <span class="mod-meta-item">⏱ 14 min read</span>
    <span class="mod-meta-item">📝 Assignment inside</span>
    <span class="mod-meta-item">Hands-on examples</span>
  </div>
</div>

In Module 3.1 you saw how developers use GenAI for code generation and debugging. This module is for the other half of every Indian IT team — the analysts, business analysts, and data analysts who work with data, reports, dashboards, and stakeholder communication every day.

If you are in a data analyst, business analyst, or reporting role — or planning to enter one — this module shows you exactly where AI saves the most time and produces the highest quality output.

---

## Why analysts are the biggest beneficiaries of GenAI

<div class="mod-stat-grid">
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">50%+</div>
    <div class="mod-stat-card-label">of standard financial reports will be AI-generated within two years — Deloitte 2026 State of AI</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">40–60%</div>
    <div class="mod-stat-card-label">productivity boost for analysts using GenAI for information retrieval and summarisation — BCG</div>
  </div>
  <div class="mod-stat-card">
    <div class="mod-stat-card-num">18%</div>
    <div class="mod-stat-card-label">annual growth in data analytics roles in India in 2026, with ₹4–8 LPA entry-level salaries</div>
  </div>
</div>

The analyst role is shifting fast. Natural language querying, automated insight generation, analytics code generation, and RAG-based internal data search are the highest-ROI GenAI use cases in data analytics in 2025. The analysts who learn to use these tools effectively are completing in 30 minutes what used to take a full day.

<div class="mod-keypoint">
<strong>The shift in the analyst role:</strong> GenAI does not replace analysts — it replaces the mechanical parts of the job: writing SQL from scratch, formatting reports, summarising long documents, drafting routine stakeholder emails. What it cannot replace is business judgement — knowing which insight matters, why a number looks wrong, and what a stakeholder actually needs to hear. That judgement is where your value now sits.
</div>

---

## Use case 1 — SQL generation from plain English

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128202;</span>
  <div class="mod-usecase-title">Writing SQL queries using natural language</div>
</div>
<div class="mod-usecase-body">

<p>For analysts who are not SQL experts — or who write SQL but spend time on complex joins and window functions — AI dramatically accelerates query writing. Give the model your table schema and what you want to know, and it generates correct SQL in seconds.</p>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — Sales analysis query for Indian retail data</div>
  <div class="mod-prompt-text">You are a senior data analyst writing SQL for a MySQL database.

I have these tables:
- orders (order_id, customer_id, order_date, city, state, total_amount, status)
- order_items (item_id, order_id, product_id, quantity, unit_price, category)
- customers (customer_id, name, tier, registration_date, city)

Write a query that shows:
1. Top 5 product categories by revenue in Q4 FY2025 (Oct 2024 – Mar 2025)
2. Month-over-month revenue growth % for each category
3. Only include completed orders (status = 'delivered')
4. Show results sorted by Q4 total revenue descending

Use window functions for the month-over-month calculation.
Format the revenue columns as integers (no decimals).</div>
  <div class="mod-prompt-note"><strong>Key elements:</strong> Full schema provided, exact date range defined (Q4 FY2025 = Oct–Mar in Indian fiscal year), filter condition specified, window function explicitly requested, output format defined. Without the schema, the model generates plausible column names that may not match your actual database.</div>
</div>

<div class="mod-prompt-box mod-pb-blue">
  <div class="mod-prompt-label">EXAMPLE — Explaining an existing complex query</div>
  <div class="mod-prompt-text">Explain what this SQL query does, step by step. Use plain language — the explanation is for a non-technical product manager.

SELECT
  c.tier,
  COUNT(DISTINCT o.customer_id) AS active_customers,
  SUM(o.total_amount) AS total_revenue,
  AVG(o.total_amount) AS avg_order_value,
  SUM(o.total_amount) / COUNT(DISTINCT o.customer_id) AS revenue_per_customer,
  RANK() OVER (ORDER BY SUM(o.total_amount) DESC) AS revenue_rank
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
WHERE o.order_date >= DATE_SUB(CURDATE(), INTERVAL 90 DAY)
  AND o.status = 'delivered'
GROUP BY c.tier
HAVING COUNT(DISTINCT o.customer_id) > 10
ORDER BY total_revenue DESC;</div>
  <div class="mod-prompt-note"><strong>Why this matters for Indian IT analysts:</strong> At TCS, Infosys, and Wipro client deliveries, analysts frequently need to explain queries to non-technical stakeholders or document them for handover. AI generates clear explanations in seconds — saving 20–30 minutes of documentation per query.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">ChatGPT — best SQL generation, widest dialect support</span>
  <span class="mod-tool-badge mod-tool-good">Claude — better for long schema analysis</span>
  <span class="mod-tool-badge mod-tool-good">GitHub Copilot — best inline in SQL editors</span>
</div>

</div>
</div>

---

## Use case 2 — Data summarisation and insight generation

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128200;</span>
  <div class="mod-usecase-title">Turning raw numbers into business insights</div>
</div>
<div class="mod-usecase-body">

<p>This is where most analysts underuse AI. They use it to format tables but not to interpret them. AI is excellent at identifying patterns, anomalies, and business implications in data — if you give it the right context about what the data represents and who will read the summary.</p>

<div class="mod-prompt-box mod-pb-green">
  <div class="mod-prompt-label">EXAMPLE — Monthly sales summary for Indian FMCG client</div>
  <div class="mod-prompt-text">You are a senior business analyst preparing a monthly performance summary for the India operations head of an FMCG company.

Here is the sales data for March 2026:

Region | Revenue (₹ Cr) | vs Feb | vs Mar 2025 | Units Sold | Returns %
North  |     142.3      |  +8.2% |   +23.1%   |   48,200   |   2.1%
South  |     118.7      |  -3.4% |   +11.4%   |   39,800   |   1.8%
West   |     167.9      |  +12.1%|   +31.2%   |   54,100   |   3.7%
East   |      89.2      |  -7.8% |    +4.2%   |   31,900   |   4.2%
Total  |     518.1      |  +3.6% |   +18.9%   |  174,000   |   2.8%

Write a 3-paragraph executive summary. Paragraph 1: overall performance vs targets. Paragraph 2: key highlights and concerns by region. Paragraph 3: 2 specific recommendations.

Tone: direct and factual. No fluff. The reader has 2 minutes for this.</div>
  <div class="mod-prompt-note"><strong>Why the tone instruction matters:</strong> Without "direct and factual, no fluff", AI defaults to corporate language full of phrases like "it is encouraging to note" and "moving forward". Indian operations heads and managers want direct numbers and recommendations — the role instruction and tone constraint together produce a genuinely useful summary.</div>
</div>

<div class="mod-prompt-box mod-pb-green">
  <div class="mod-prompt-label">EXAMPLE — Anomaly detection in data</div>
  <div class="mod-prompt-text">You are a data analyst reviewing weekly transaction data for anomalies.

Here is transaction volume data by day for the past 4 weeks (in thousands):

Week 1: Mon 42, Tue 45, Wed 43, Thu 47, Fri 89, Sat 134, Sun 98
Week 2: Mon 41, Tue 44, Wed 46, Thu 45, Fri 91, Sat 128, Sun 95
Week 3: Mon 43, Tue 46, Wed 44, Thu 48, Fri 87, Sat 131, Sun 97
Week 4: Mon 40, Tue 12, Wed 45, Thu 46, Fri 88, Sat 133, Sun 96

Identify any anomalies. For each anomaly:
1. State what is unusual and by how much it deviates from the pattern
2. List 3 possible business explanations
3. State what additional data you would need to confirm the cause

Think step by step before identifying anomalies.</div>
  <div class="mod-prompt-note"><strong>CoT trigger for analysis:</strong> "Think step by step before identifying" prevents the model from pattern-matching to the most obvious answer. The model will correctly identify Week 4 Tuesday (12K vs ~44K average — a 73% drop) and generate plausible hypotheses: system outage, payment gateway failure, bank holiday. The structured output format makes it directly usable in an incident report.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — best analytical reasoning and writing quality</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT with data analysis — can read CSV/Excel directly</span>
  <span class="mod-tool-badge mod-tool-good">Gemini — good for research-backed context</span>
</div>

</div>
</div>

---

## Use case 3 — Python for data analysis

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128013;</span>
  <div class="mod-usecase-title">Generating Python analysis and visualisation code</div>
</div>
<div class="mod-usecase-body">

<p>For analysts who know what they want to do with data but are not strong Python coders, AI generates working pandas and matplotlib/seaborn code with the same specificity-equals-quality principle from Module 3.1. For experienced analysts, AI accelerates the boilerplate — freeing you to focus on interpretation.</p>

<div class="mod-prompt-box mod-pb-orange">
  <div class="mod-prompt-label">EXAMPLE — Customer churn analysis for Indian telecom data</div>
  <div class="mod-prompt-text">You are a data analyst writing Python for a telecom company's churn analysis.

I have a CSV file 'customers.csv' with these columns:
customer_id, circle (Delhi/Mumbai/Chennai/Kolkata/etc), tenure_months,
monthly_recharge_avg, data_usage_gb, voice_minutes, complaints_last_90d,
last_recharge_days_ago, churned (0/1)

Write Python code that:
1. Loads the data with pandas
2. Creates a summary showing churn rate by circle (bar chart, sorted descending)
3. Shows distribution of tenure_months for churned vs non-churned (overlapping histogram)
4. Prints a correlation table between churned and the numeric features, sorted by absolute correlation

Requirements:
- Use matplotlib for charts, seaborn for the histogram
- Figure size 10x6, title and axis labels on every chart
- Save charts as PNG files: churn_by_circle.png, tenure_distribution.png
- Print all outputs clearly labelled
- Include comments explaining each step</div>
  <div class="mod-prompt-note"><strong>India-specific framing matters:</strong> Using "circle" (telecom regulatory term in India) instead of "region" produces code that matches actual Indian telecom data structures. This saves a round of editing. Always use your actual column names and domain vocabulary — the model generates directly usable code instead of skeleton code you have to rename.</div>
</div>

<div class="mod-prompt-box mod-pb-orange">
  <div class="mod-prompt-label">EXAMPLE — Excel automation with Python</div>
  <div class="mod-prompt-text">Write Python code to automate a weekly sales report that currently takes me 2 hours manually.

Input: 'weekly_sales.xlsx' with sheets: RawData, Targets
- RawData columns: date, salesperson, region, product, units_sold, revenue
- Targets columns: salesperson, weekly_target_revenue

Output: A formatted Excel report 'weekly_report.xlsx' with:
1. Sheet "Summary": pivot table — salesperson vs region showing total revenue, with grand totals
2. Sheet "Performance": each salesperson's actual vs target, % achieved, status (✓ Met / ✗ Missed)
3. Sheet "Top Products": top 10 products by units sold this week

Formatting requirements:
- Header rows: bold, background #1565C0, font white
- Met target rows: light green background (#e8f5e9)
- Missed target rows: light red background (#ffeaea)
- All revenue columns: Indian number format (₹1,23,456)

Use openpyxl. Include error handling for missing files.</div>
  <div class="mod-prompt-note"><strong>This prompt eliminates a 2-hour weekly task.</strong> Indian number formatting (1,23,456 instead of 123,456), specific colour codes matching your theme, and the exact sheet structure mean the output is production-ready. The model knows openpyxl's Indian locale formatting — specifying it explicitly ensures you get it.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — best for complex multi-step Python with clear logic</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — can execute Python directly (Advanced Data Analysis mode)</span>
  <span class="mod-tool-badge mod-tool-ok">GitHub Copilot — good inline for pandas operations</span>
</div>

</div>
</div>

---

## Use case 4 — Report and presentation writing

<div class="mod-usecase">
<div class="mod-usecase-header">
  <span class="mod-usecase-icon">&#128196;</span>
  <div class="mod-usecase-title">Writing reports, dashboards narratives, and presentation content</div>
</div>
<div class="mod-usecase-body">

<p>The highest-value analyst output is not the data itself — it is the narrative that explains what the data means. This is where AI saves the most time and where prompt engineering skill produces the biggest quality difference.</p>

<div class="mod-prompt-box mod-pb-purple">
  <div class="mod-prompt-label">EXAMPLE — Power BI / Tableau dashboard narrative</div>
  <div class="mod-prompt-text">You are a senior analyst writing the narrative text for a Power BI dashboard for a mid-size Indian e-commerce company.

Dashboard context: Q4 FY2026 (Jan–Mar 2026) performance review
Audience: Senior leadership team (CMO, CFO, COO) — non-technical

Key metrics from the data:
- Total GMV: ₹847 Cr (+22% YoY)
- Orders: 2.3 million (+18% YoY)
- Average Order Value: ₹368 (+3% YoY)
- Customer Acquisition Cost: ₹312 (-8% YoY — improvement)
- Return Rate: 14.2% (+1.8pp YoY — deterioration)
- Mobile orders: 78% of total (+6pp YoY)
- Top category: Electronics (31% of GMV)
- Weakest region: East India (-3% YoY)

Write:
1. A 2-sentence headline summary (for the dashboard title area)
2. A 4-sentence performance narrative for the overview section
3. One "watch out" callout (the metric that needs attention)
4. One "opportunity" callout (the metric that suggests upside)

Keep language sharp. Each sentence should contain a number. Avoid passive voice.</div>
  <div class="mod-prompt-note"><strong>"Each sentence should contain a number"</strong> is one of the most effective constraints for analyst writing prompts. It forces the model to anchor every claim in data — exactly what leadership dashboards require. Without this constraint, AI produces hedged language that adds no value over the numbers themselves.</div>
</div>

<div class="mod-prompt-box mod-pb-purple">
  <div class="mod-prompt-label">EXAMPLE — Converting data findings into presentation slides outline</div>
  <div class="mod-prompt-text">Convert these analysis findings into a 5-slide presentation outline for a quarterly business review at an Indian IT services company.

Findings:
- Project delivery on-time rate: 73% (target was 85%)
- Top delay cause: requirement changes mid-project (41% of delayed projects)
- Second delay cause: resource unavailability (28% of delayed projects)
- Client satisfaction score: 7.8/10 (down from 8.3 last quarter)
- Projects using AI-assisted testing: 23% faster delivery, 91% on-time rate
- Headcount utilisation: 84% (industry benchmark: 78%)

For each slide provide:
- Slide title (max 8 words)
- 3 bullet points (one key data point each)
- One "so what" statement — the business implication

Slides: Executive Summary, Problem Analysis, Root Causes, Solution (AI-assisted testing), Next Steps</div>
  <div class="mod-prompt-note"><strong>The "so what" instruction</strong> transforms a data dump into a business argument. This is the difference between an analyst who presents data and one who tells a story with data. The model generates the business implication for each slide — which is exactly what separates a good QBR presentation from a great one.</div>
</div>

<div class="mod-tool-row">
  <span class="mod-tool-badge mod-tool-best">Claude — most natural, least AI-sounding report writing</span>
  <span class="mod-tool-badge mod-tool-good">ChatGPT — strong for structured business writing</span>
</div>

</div>
</div>

---

## The AI-assisted analyst workflow

<div class="mod-workflow">
<div class="mod-workflow-title">RECOMMENDED WORKFLOW — AI-ASSISTED DATA ANALYSIS</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">1</div>
  <div class="mod-workflow-text"><strong>Understand the business question first.</strong> Before writing a single query or prompt, write down in one sentence what decision this analysis will support. AI cannot supply business context it was not given.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">2</div>
  <div class="mod-workflow-text"><strong>Use AI for SQL and Python first drafts.</strong> Provide the full schema, the business question, and any constraints (date ranges, filters, output format). Review every line before running on production data.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">3</div>
  <div class="mod-workflow-text"><strong>Verify the numbers yourself.</strong> AI-generated queries can have subtle logic errors — wrong date filters, incorrect joins, missed NULL handling. Always spot-check the output against known data points before sharing with stakeholders.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">4</div>
  <div class="mod-workflow-text"><strong>Use AI for the narrative, you provide the judgement.</strong> Paste your verified numbers into the report-writing prompts. AI writes the first draft — you add context the model cannot know (why a number is unusual, what changed in the business this quarter).</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">5</div>
  <div class="mod-workflow-text"><strong>Use Gemini for research context.</strong> When you need to contextualise a finding against industry benchmarks or market trends, Gemini's live search grounding is more reliable than ChatGPT or Claude for current figures.</div>
</div>
<div class="mod-workflow-step">
  <div class="mod-workflow-num">6</div>
  <div class="mod-workflow-text"><strong>Never paste raw client data into consumer AI tools.</strong> Aggregate or anonymise data before prompting. A table with 500 customer IDs, names, and transaction values is a DPDP Act compliance violation if pasted into ChatGPT's consumer tier. Use your company's enterprise AI tool for sensitive data.</div>
</div>
</div>

---

<div class="mod-warning">
<strong>The most important analyst-specific risk:</strong> AI-generated SQL queries can produce results that look correct but have subtle logic errors — incorrect date boundary conditions, wrong join types that silently drop or duplicate rows, or aggregations applied at the wrong level. A query that runs without error and returns plausible-looking numbers is not the same as a query that is logically correct. Always verify AI-generated query output against at least one known data point before presenting to a stakeholder.
</div>

---

## The three things to remember

<div class="mod-remember">
  <div class="mod-remember-title">KEY TAKEAWAYS — MODULE 3.2</div>
  <ol>
    <li><strong>Schema and context are everything for SQL and Python generation</strong> — paste your actual table schema, column names, Indian-specific terms (fiscal year, circles, LPA), and exact output requirements. Vague prompts produce skeleton code you have to rewrite. Specific prompts produce production-ready first drafts.</li>
    <li><strong>AI writes the draft, you provide the business judgement</strong> — AI can generate the narrative from numbers but cannot know why a number is surprising, what changed in the business, or what a specific stakeholder needs to hear. Your value as an analyst is that contextual judgement — not the mechanical writing.</li>
    <li><strong>Always verify AI-generated query output before sharing</strong> — a query that runs without error is not necessarily logically correct. Spot-check against known data points. This one habit separates analysts who trust AI appropriately from those who create problems for themselves and their teams.</li>
  </ol>
</div>

---

<div class="mod-assignment" id="assignment-32">
  <div class="mod-assignment-header">
    <span class="mod-assignment-icon">&#9998;</span>
    <h3 class="mod-assignment-title">Assignment 3.2 — Apply AI to a Real Analysis Task</h3>
  </div>
  <p>Three tasks covering the core analyst use cases. Each should take 15–20 minutes.</p>
  <ol>
    <li><strong>SQL generation:</strong> Write a prompt asking AI to generate a SQL query for a real analysis you need to do — or a practice dataset you are working with. Include your full schema, the business question, and any filters or output format requirements. Run the query (if you have access to a database) and note any corrections needed.</li>
    <li><strong>Data summarisation:</strong> Take any table of numbers you have worked with recently — a report, an assignment dataset, or publicly available data (Kaggle India datasets work well). Paste the key numbers into a prompt and ask AI to write an executive summary with specific constraints: two paragraphs, every sentence must contain a number, direct tone. Compare the output to how you would have written it.</li>
    <li><strong>Report narrative:</strong> Take one insight from your analysis — a pattern, an anomaly, or a performance gap — and ask AI to write a "so what" statement explaining the business implication. The model should generate the business argument, not just repeat the number. Note whether the implication is accurate for your domain context.</li>
    <li><strong>Add all three prompts to your AI Learning Journal</strong> under "Module 3.2 — Analyst Prompts." These go into your prompt library in Module 3.4.</li>
  </ol>
  <p>After this assignment you will have a concrete sense of where AI genuinely accelerates analyst work and where your own business judgement is irreplaceable.</p>
</div>

<div class="mod-blog-links">
  <div class="mod-blog-title">FURTHER READING ON THE BLOG</div>
  <a href="/posts/ai-impact-indian-it-jobs/">How AI is Affecting Indian IT Jobs in 2026 — chandrashaker.in</a>
  <a href="/posts/ai-resistant-skills-india/">AI-Resistant Skills: What to Learn to Stay Relevant — chandrashaker.in</a>
</div>

<div class="mod-nav">
  <a class="mod-nav-back" href="/courses/genai/unit3/module-3-1-genai-for-developers/">&#8592; Module 3.1: GenAI for Developers</a>
  <a class="mod-nav-next" href="/courses/genai/unit3/module-3-3-genai-for-managers/">Module 3.3: GenAI for Managers &#9654;</a>
</div>

<details class="mod-credits">
  <summary>Sources and data references</summary>
  <table>
    <thead><tr><th>Claim</th><th>Source</th></tr></thead>
    <tbody>
      <tr><td>50%+ of standard financial reports will be AI-generated within two years</td><td>Deloitte 2026 State of AI in the Enterprise, cited in sranalytics.io March 2026</td></tr>
      <tr><td>40–60% productivity boost for analysts using GenAI for information retrieval</td><td>BCG Stairway to GenAI Impact, cited in sranalytics.io January 2026</td></tr>
      <tr><td>Natural language querying, automated insight generation, analytics code generation are highest-ROI use cases</td><td>LatentView Analytics GenAI in Data Analytics, April 2026</td></tr>
      <tr><td>18% annual growth in data analytics roles in India 2026; ₹4–8 LPA entry salaries</td><td>learninglabb.com Data Job Trends 2026, December 2025</td></tr>
      <tr><td>Data analyst role in India: SQL, Tableau/Power BI, Excel, Python — standard toolkit</td><td>dvanalyticsmds.com Data Science Career Paths India 2026</td></tr>
      <tr><td>Diagrams: original — CC0</td><td>No attribution required</td></tr>
    </tbody>
  </table>
</details>

</div>
