# Medical Hub

**Patient records, visits and follow-ups — all in one calm place.**

A patient CRM for small clinics that are outgrowing paper folders and scattered spreadsheets. It's built entirely on Google Workspace: Google Apps Script for the app, Google Sheets as the database, and Google Drive for private file storage.

### 👉 [Try the live demo](https://masystemsolutions.github.io/Medical-Hub/)

Click **Explore the live demo**. No sign-up needed. Everything is fictional sample data, reminder emails are previewed instead of sent, and the demo resets every night.

<!-- Add screenshots here, e.g.
![Today dashboard](screenshots/today.png)
![Patient chart](screenshots/patient-chart.png)
-->

---

## What it does

| Area | What staff can do |
|---|---|
| **Today** | See tomorrow's follow-ups, what needs attention, and recent activity at a glance. Every number is a clickable shortcut. |
| **Patients** | Search, sort and register patients. Each one has a single chart with visits, documents, care plan and history. |
| **Visits & follow-ups** | Log visits, attach files, schedule follow-ups, and email a reminder in one click. |
| **Documents** | Track each patient's intake checklist (ID, insurance card, medical history, consent form). Upload, preview, approve, or ask for a new copy. |
| **Care plans** | Treatment goals with target dates. Overdue steps are flagged automatically. |

New patients automatically get their required-documents checklist and a starter care plan. First-time visitors get a short guided tour.

## Security and reliability

- **Staff-only access:** salted, hashed passwords, expiring sessions, and a lockout after repeated failed logins.
- **Private files:** uploads are never shared publicly. They're only served to signed-in users, and only if they belong to a record in the app.
- **Full audit trail:** every change records who made it and when.
- **Safe input:** all text is escaped before display (prevents XSS) and protected against spreadsheet formula injection.
- **Data integrity:** sequential IDs (no collisions) and locking so two staff saving at once can't overwrite each other.
- **Correct dates:** a fixed clinic time zone (Asia/Manila), so dates never shift by a day.

## Tech stack

Google Apps Script · Google Sheets · Google Drive · MailApp · HTML/CSS/JavaScript · Bootstrap 5 · Bootstrap Icons

## Project structure

```
apps-script/
├── Code.gs       # server: API, auth, validation, emails, demo data
└── index.html    # the whole front end (single page)
index.html        # GitHub Pages wrapper that loads the live app
```

## Run your own copy

1. Create a Google Sheet, then open **Extensions → Apps Script**.
2. Paste `apps-script/Code.gs` into `Code.gs`. Add an HTML file named `index` and paste `apps-script/index.html`.
3. Select the `setup` function and click **Run**, then approve the permissions.
4. **Deploy → New deployment → Web app**, with *Execute as: Me* and *Who has access: Anyone*.
5. For real clinic use: set `DEMO_MODE: false` in `Code.gs`, run `setup` again, and create staff logins with `addStaffAccount`.

---

Built by **MA System Solutions**.
