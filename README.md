# 🎓 Course Enrollment & Certification Automation (n8n)

An end-to-end, 12-level workflow automation built in **n8n** that handles the entire
lifecycle of a student's journey — from course purchase to AI-graded certification —
with zero manual intervention.

Built as part of my journey learning AI automation engineering, this project combines
**Google Sheets, Gmail, Slack, AI Agents (LangChain), and conditional logic** to
create a fully autonomous course enrollment and certification pipeline.

---

## 📌 What This Automation Does

When a student purchases a course, this system automatically:

1. Saves their enrollment data to Google Sheets
2. Sends a welcome email
3. Notifies the internal team on Slack
4. Shares the course community group link
5. Starts a 30-day learning period timer
6. Sends the certification exam link once the period is complete
7. Sends a reminder 5 days before the exam window closes
8. Captures and stores exam responses
9. Uses an **AI Agent** to grade the exam and calculate Pass/Fail
10. Auto-generates and emails a certificate on Pass
11. Sends a retry email with feedback and a new exam date on Fail
12. Loops back to offer the next course to successful students

---

## 🧭 Workflow Breakdown (12 Levels)

| Level | Stage | Description |
|-------|-------|-------------|
| 1 | Purchase Capture | Student data saved to Google Sheet on form/purchase submission |
| 2 | Welcome Email | Auto-generated HTML welcome email sent immediately |
| 3 | Slack Notification | Internal team notified of new enrollment in real time |
| 4 | Community Access | WhatsApp/course group link auto-sent to the student |
| 5 | Enrollment Timer | 30-day wait period begins from enrollment date |
| 6 | Exam Access | Certification exam link auto-sent after 30 days |
| 7 | Reminder | Reminder email sent on Day 25 — 5 days left to attempt |
| 8 | Response Capture | Exam submission stored via Google Forms → Sheets |
| 9 | AI Grading | AI Agent evaluates answers and calculates Pass/Fail |
| 10 | Certificate Delivery | On Pass, a certificate is generated and emailed |
| 11 | Retry Flow | On Fail, feedback + retry email with new exam date is sent |
| 12 | Upsell Loop | Successful students are looped into the next course offer |

---

## 🛠️ Tech Stack & Tools

- **n8n** (self-hosted, v2.31.7) — core automation engine
- **LangChain AI Agent Node** — for automated exam grading with structured JSON output
- **Google Sheets** — student data storage and response tracking
- **Google Forms** — exam delivery and response collection
- **Gmail API** — transactional emails (welcome, reminder, results, certificate)
- **Slack API** — internal team notifications
- **n8n Code Nodes (JavaScript)** — date calculations, eligibility logic, data
  transformation, and HTML email generation
- **Execute Workflow (Sub-workflows)** — modular certificate generation flow

---

## 📂 Repository Structure

```
├── Student_enrollment_to_googlesheet_automation.json   # Levels 1–4: enrollment, welcome email, Slack alert, group link
├── My_workflow.json                                    # Levels 5–9: timer, exam delivery, reminders, AI grading
├── generatte_certificate.json                          # Level 10–11: certificate generation & result email (sub-workflow)
├── screenshots/                                        # Workflow canvas screenshots
└── README.md
```

---

## ⚙️ How the AI Grading Works

A dedicated **AI Agent node** is used to evaluate free-text exam answers against a
strict rubric (5 questions, 5 marks each, 60% pass threshold). The agent is
constrained with a detailed system prompt to:

- Grade purely on technical accuracy, ignoring grammar/spelling
- Award 0 marks for blank, gibberish, or irrelevant answers
- Always return a structured JSON result (`q1_score` → `feedback`)
- Never throw errors on missing input — always returns a valid, gradeable result

The AI's raw output is then parsed and merged with the student's original
enrollment data (Name, Email) using a Code node, ensuring accurate personalization
in every follow-up email.

---

## 🚀 Key Features

- ✅ Fully automated 30-day enrollment-to-certification lifecycle
- ✅ AI-powered, rubric-based exam grading (no manual checking)
- ✅ Dynamic HTML emails for every stage (welcome, reminder, pass, fail)
- ✅ Conditional branching for Pass/Fail outcomes
- ✅ Modular sub-workflow for certificate generation
- ✅ Real-time internal team notifications via Slack

---

## 📸 Workflow Screenshots

### Project Overview — 12-Level Automation Plan
![Project Overview](screenshots/01_project_overview.png)

### Enrollment → Notification Workflow (Slack, Sheets, Emails)
![Enrollment Notification Workflow](screenshots/02_enrollment_notification_workflow.png)

### Full Automation Canvas (Timer → AI Grading → Certificate/Retry)
![Full Workflow Canvas](screenshots/03_full_workflow_canvas.png)

### Certificate Generation Sub-Workflow
![Certificate Generation Sub-workflow](screenshots/04_certificate_generation_subworkflow.png)

---

## 🙋‍♀️ About This Project

Built by **Amara Tariq** — Data Science student and aspiring AI Automation
Engineer, as a hands-on project to learn n8n workflow design, AI agent
integration, and end-to-end automation architecture.

🔗 [GitHub](https://github.com/Amara-ch) · [LinkedIn](https://linkedin.com/in/amara-tariq-2762ab331)
