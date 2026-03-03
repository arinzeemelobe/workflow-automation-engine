# ⚙️ Business Workflow Automation Engine

> A modular, production-grade pipeline that connects form submissions to email notifications, Google Sheets logging, and webhook dispatch — eliminating manual data entry and reducing processing time by 30%+.

---

## ✨ Features

| Step | Description |
|---|---|
| ✅ Input Validation | Type-safe form data validation with descriptive error messages |
| 📊 Google Sheets Logging | Auto-appends submissions via Apps Script webhook |
| 📧 Email Notifications | Sends branded HTML confirmation to user + internal alert to admin |
| 🔗 Webhook Dispatch | Fires to Zapier / Make / Slack / any endpoint |
| 💾 Local Fallback | If Sheets is down, saves to `local_logs/submissions.jsonl` |
| 📝 Full Audit Log | All steps logged with timestamps to `automation.log` |

---

## 🚀 Quick Start

```bash
git clone https://github.com/yourprofile/workflow-automation-engine.git
cd workflow-automation-engine
pip install requests

# Configure environment variables:
export SMTP_HOST="smtp.gmail.com"
export SMTP_USER="your@gmail.com"
export SMTP_PASS="your-app-password"
export ADMIN_EMAIL="admin@yourcompany.com"
export SHEETS_WEBHOOK_URL="https://script.google.com/..."  # optional
export WEBHOOK_URLS="https://hooks.zapier.com/...,https://hooks.slack.com/..."  # optional

python pipeline.py
```

> **Demo Mode:** Run without env vars to test the pipeline locally — emails/sheets are soft-skipped and all data is saved to `local_logs/`.

---

## 🔁 Pipeline Flow

```
Form Input
    │
    ▼
[1] Validate → reject bad data early
    │
    ▼
[2] Sheets Log → append to spreadsheet (fallback: local JSON)
    │
    ▼
[3] Confirmation Email → sent to submitter
    │
    ▼
[4] Alert Email → sent to admin
    │
    ▼
[5] Webhooks → fire to all configured endpoints
    │
    ▼
PipelineResult (summary + step report)
```

---

## 📁 Structure

```
workflow-automation-engine/
├── pipeline.py         # Core engine
├── requirements.txt    # Dependencies
├── local_logs/         # Auto-created fallback storage
├── automation.log      # Auto-created audit log
└── README.md
```

---

## 👤 Author

**Arinze Emelobe** — AI Automation & Training Specialist  
[LinkedIn](https://linkedin.com/in/yourprofile) · [GitHub](https://github.com/yourprofile)
