# SEG3125 Lab 10 – Team 16 (Elite Cuts chatbot workspace)

**Lab 10** is the **Dialogflow CX** chatbot assignment (**due April 5, 2026, 11:59 PM**, 3%). It is **not** graded on this HTML/JS code; the deliverable is the **agent in Google Dialogflow CX** plus **video** (under 10 minutes) and **screenshots**.

This repository folder is set up as a **workspace** that includes:

1. **`lab10/`** – Implementation spec for your CX agent (**start here**): build guide, entities, parameters, training phrases, video checklist, and `elite-cuts-data.json`.
2. **Root files (`index.html`, `js/`, `css/`)** – A **clone of [Lab 5 – Elite Cuts](https://github.com/SEG3125-2026/seg3125-lab-5-team-16)** so you have the same services, stylists, hours, and booking rules while you design conversations.

**Lab 5 (reference only):** https://seg3125-2026.github.io/seg3125-lab-5-team-16/

---

## Quick start (Team 16)

1. Open **`lab10/DIALOGFLOW_CX_BUILD_GUIDE.md`** and create the agent in the Dialogflow CX console.
2. Use **`lab10/elite-cuts-data.json`** for exact service names, prices, staff, and contact info in fulfillments.
3. Follow **`lab10/VIDEO_AND_SUBMISSION_CHECKLIST.md`** before recording.

---

## Git / new GitHub repository (recommended)

This folder may still have `origin` pointing at **Lab 5** after a fresh clone. For Lab 10 submission, create a **new** repo (e.g. `seg3125-lab-10-team-16`) and push:

```bash
cd /path/to/seg3125-lab10-team-16
git remote remove origin   # only if it still points to lab 5
git remote add origin https://github.com/SEG3125-2026/YOUR-LAB10-REPO.git
git add -A
git commit -m "Lab 10: Dialogflow spec + Lab 5 reference for Elite Cuts"
git push -u origin main
```

Adjust branch name if your course uses `master`.

---

## Original Lab 5 README (website reference)

The single-page salon site was described in the upstream Lab 5 README. Summary: **Bootstrap 5**, **one-pager**, **regex validation**, **calendar constraints**, **payment section**. See `js/app.js` for services and staff arrays.

---

**Course:** SEG 3125 – Analysis and Design of User Interfaces  
**Group 16:** Pierre Georges, Eknoor Goraya, Ziad Tariq
