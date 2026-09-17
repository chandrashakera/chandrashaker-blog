---
title: "How I Built a Free Student Certificate Tracker Using Google Sheets (No Firebase)"
slug: "student-achievement-tracker-google-sheets-backend"
date: 2026-09-17
description: "How I built a zero-cost student certificate tracker using Google Sheets, Apps Script, and Gemini's vision API instead of Firebase — full stack breakdown, schema, and the OCR decision that didn't work."
tags: ["app-dev-log", "google-apps-script", "google-sheets", "gemini-api", "edtech"]
categories: ["Dev Logs"]
thumbnail: "/images/student-tracker-workflow.png"
draft: false
---

Every semester, students used to submit their certificates for participation, workshops, courses, extracurricular activities, and competition wins through a Google Form, attaching scans, phone photos, or PDFs of the certificate itself. The form answers were never something I could just trust. Students picked the wrong certificate type, mislabeled the category, or got the event name wrong, so I ended up opening every attachment myself and checking it against what was submitted, certificate by certificate. That manual verification alone used to take 1-2 months each cycle.

That's the part I killed. Meet the **Student Achievement Tracker**, live at [a.chandrashaker.in](https://a.chandrashaker.in) - zero backend cost, zero manual re-typing, zero Firebase.

![Student Achievement Tracker home screen showing the roll number field and Scan Certificate / Upload Certificate buttons](/images/student-tracker-home-screen.jpg "Student Achievement Tracker home screen")

## The stack

Nothing exotic. That was the point.

- **Frontend:** a static, installable PWA, hosted on Cloudflare Pages
- **PDF text:** `pdf.js`, extracted entirely client-side
- **Images:** sent directly to **Gemini's vision API** - no OCR step at all
- **Field structuring:** Gemini free tier, turning raw text or an image straight into structured data
- **Storage:** Google Apps Script writing to Google Sheets, with files archived to Google Drive

No servers. No database to provision. No auth system. Just a Google account most departments already have, doing the job of a backend.

![Workflow diagram: certificate scan or upload flows through Gemini Vision and pdf.js extraction into an editable confirmation screen, then into Google Sheets and Drive](/images/student-tracker-workflow.png "Student Achievement Tracker workflow, from certificate to Google Sheets")

## The OCR decision that didn't survive contact with reality

I didn't start with Gemini vision for images - I started with **Tesseract.js**, the obvious client-side OCR choice. It's a solid engine for one specific case: clean, printed text.

Certificates are not that. Names in cursive fonts, event titles in decorative headers, stamps overlapping text - Tesseract misread enough of it that the "automated" extraction needed almost as much manual correction as typing it by hand would have. So I dropped it and sent images straight to Gemini's vision model instead. It reads the same messy, real-world certificate far more reliably, and it removed a multi-second local OCR wait as a side benefit.

Worth remembering next time you're picking a client-side OCR tool: printed-text engines and real-world documents are not the same problem.

## How a submission actually works

Student scans or uploads a certificate, a manual crop step lets them tighten the frame first, Gemini extracts the fields, an **editable confirmation screen** shows what it read, the student reviews and submits, and a row lands in a 10-column sheet: Roll No., Name, Certificate Type, Certificate Category, Position/Rank, Event/Course/Activity, Issuing Body, Date, File Link, Timestamp.

Two fields got deliberate rules, not just whatever the model felt like returning:

- **Certificate Type** allows free text beyond the fixed set (Participation/Appreciation/Merit) - whatever follows "Certificate of ___" gets stored as written.
- **Position/Rank** is left blank unless a rank is *explicitly printed* on the certificate, never inferred, even when the Type comes back "Merit." A blank field is honest. A confidently wrong "Winner" is a data-integrity bug wearing a UI's clothes.

![Editable confirmation screen showing extracted certificate fields, student name and roll number redacted for privacy](/images/student-tracker-confirmation-screen-redacted.png "Confirmation screen with extracted fields, name and roll number redacted")

That confirmation screen is doing more work than it looks like. Extraction is good, not perfect - the review step is what keeps the sheet trustworthy.

## Why not Firebase

Firebase would have meant a project to provision, security rules to write and keep correct, and a pricing tier to eventually think about. For one department's certificate log, that's infrastructure sized for a problem I didn't actually have.

Google Sheets already *is* the database non-technical staff already know how to open, filter, and export from - no admin panel needed. The trade-off is real: Sheets doesn't scale like a proper database, and Apps Script has hard quota limits. For this scope, that ceiling isn't close to a concern.

![Resulting Google Sheet row after a certificate submission, student name and roll number redacted for privacy](/images/student-tracker-sheet-row-redacted.png "A submitted certificate landing as a row in Google Sheets, name and roll number redacted")

This is what "no manual re-typing" actually looks like: one row, every column filled, no month-long backlog behind it.

---

*Try it: [a.chandrashaker.in](https://a.chandrashaker.in). More dev logs from the [apps.chandrashaker.in](https://apps.chandrashaker.in) app portfolio coming soon, including the Exam Marks Tracker build.*
