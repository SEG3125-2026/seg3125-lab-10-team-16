# Lab 10 Submission

**Course:** SEG 3125 — Analysis and Design of User Interfaces  
**Lab:** 10  
**Date:** April 5, 2026  

**Group Number:** 16  

## Group Members

| Name | Email | Student Number |
|------|--------|----------------|
| Pierre Georges | pgeor012@uottawa.ca | 300283706 |
| Eknoor Goraya | egora090@uottawa.ca | 300278785 |
| Ziad Tariq | ztari098@uottawa.ca | 300443993 |

## GitHub Repository

***(Replace with your team’s new Lab 10 repo URL after it is created.)***

`https://github.com/SEG3125-2026/seg3125-lab-10-team-16`

The repository contains the Lab 10 workspace: Dialogflow CX **agent export** (`lab10/dialogflow-export/`), build guides, entity/training-phrase specs, Elite Cuts reference data (`lab10/elite-cuts-data.json`), and the Lab 5 website clone **for reference only** (services, stylists, hours, contact).

## Deployed Application

Lab 10 is **not** graded on a hosted web app. The deliverable is the **Dialogflow CX agent** in Google Cloud, plus **video**, **screenshots**, and **sharing the agent with the TAs** as specified in the course instructions.

**Reference (same business as Lab 5):**  
[Lab 5 Elite Cuts site](https://seg3125-2026.github.io/seg3125-lab-5-team-16/) — used only to keep services, stylists, and salon facts consistent with the chatbot.

---

## 5. Individual Member Contributions

***(Adjust percentages and bullets to match what each person actually did before you submit.)***

- **Pierre Georges — 33%**  
  Contributed to Dialogflow CX flow design and booking conversation structure; supported testing and alignment with Lab 5 business rules.

- **Eknoor Goraya — 34%**  
  Set up Google Cloud / Dialogflow CX agent, custom entities (`salon_service`, `stylist`), Booking Flow pages through **Stylist** (parameter `stylist`, `@stylist`, routing toward date/time/contact); coordinated repo packaging including agent JSON export under `lab10/dialogflow-export/`.

- **Ziad Tariq — 33%**  
  Contributed to support flow content, training phrases, final submission materials, screenshots, and video preparation per the Lab 10 checklist.

---

## 6. Implementation Overview

This lab implements a **Dialogflow CX** conversational agent for **Elite Cuts**, the same hair salon as Labs 4–5. The agent supports **booking** (collecting structured slots) and **support** questions (services, hours, location), with **required parameters**, **custom** and **system** entities, **partial input** handling, **confirmation**, and **fallback / no-match** behavior as required by the Lab 10 slides.

**Main elements implemented or specified in the repository:**

- **Custom entity types:** `salon_service`, `stylist` (with synonyms), aligned with `lab10/elite-cuts-data.json`
- **System entities** (where used in the agent): e.g. `@sys.date`, `@sys.time`, `@sys.email`, `@sys.phone-number` for booking and contact capture
- **Flows:** at minimum **Default Start Flow** and **Booking Flow**; **Support Flow** should be completed in the console before final demo if required by the rubric
- **Booking Flow pages (progress note):** work progressed through **Service** and **Stylist** (including parameter `stylist` and transition planning toward the date step). Remaining pages (**Date**, **Time**, **Contact**, **Confirmation**, **Complete**) and full **Start Flow** routing to Booking/Support should be finished before recording
- **Agent backup for the repo:** JSON package export of the agent is stored under `lab10/dialogflow-export/` (plus `.zip`) so the team can version and submit the configuration alongside the video and screenshots

No React or Heritage Archive code is part of the Lab 10 graded deliverable; the root `index.html` / `js/app.js` site is **reference only**.

---

## 7. Application Functionality

The conversational agent is intended to let users:

- **Start** with a clear **welcome** and short explanation of what the bot can do (book vs. ask about the salon)
- **Book an appointment** by collecting **service**, **stylist**, **date**, **time**, and **contact** (name plus phone or email), then **confirm** the summary
- **Handle partial information** so that if the user states several slots in one message (e.g. service + stylist + date + time), the agent **only asks for missing** fields
- **Answer support questions** about **services and prices**, **hours**, and **location/contact** (once the Support Flow is fully wired and populated from `elite-cuts-data.json`)
- **Recover from errors** using **no-match / fallback** responses that steer the user back to valid options

**Video (required):** Under **10 minutes**, showing welcome, booking, partial handling, missing-field prompts, confirmation, at least one fallback, and **console views** of **flows/pages** and **parameters/entities**.

---

## 8. Use of Dialogflow CX Concepts

The design follows core **Dialogflow CX** ideas described in the course:

- **Agent** — single Elite Cuts assistant in a Google Cloud project  
- **Flows** — separate major paths (e.g. default start, booking, support)  
- **Pages** — steps inside a flow (e.g. service selection, stylist, date, time, contact, confirmation)  
- **Parameters / form filling** — structured capture instead of relying only on free text  
- **Entities** — **custom** lists (services, stylists) and **built-in** types for date, time, email, phone  
- **Routes** — transitions when intents match, parameters are filled, or the user confirms  
- **Fulfillment** — bot responses, prompts, and summaries  
- **Webhook** — optional for this lab; fulfillments only are sufficient unless the TA requires persistence  

---

## 9. Human Interactive Processes

The chatbot supports typical **human–computer dialogue** patterns:

- **Orienting** — greeting and menu of options (book vs. information)  
- **Task execution** — completing a booking through a **guided sequence** with clear prompts  
- **Efficiency** — **partial answers** reduce repetition when the user gives multiple details at once  
- **Verification** — **confirmation** step before the bot treats the booking as final  
- **Error recovery** — **fallback** messaging when input is unclear or out of scope  

These match the Lab 10 goal of an alternative to a traditional form UI for the same salon domain.

---

## 10. Summary

Lab 10 delivers a **Dialogflow CX** experience for **Elite Cuts** that mirrors the business context of Labs 4–5 while emphasizing **structured dialogue**, **entities**, and **robust conversation design**. The GitHub repository preserves **documentation**, **data**, and an **exported agent** for reproducibility; **grading** relies on the **live agent**, **shared access for TAs**, and the **submitted video and screenshots** per Brightspace instructions.

**Screenshots** (flows/pages, parameters/entities) and the **Lab 10 recording contact sheet** should be attached or embedded in the final PDF submission as required by the instructor.

---

## Appendix — Pre–final submission checklist (for the team)

Before the deadline, confirm:

- [ ] **Date**, **Time**, **Contact**, **Confirmation**, **Complete** pages in **Booking Flow** are built and linked  
- [ ] **Default Start Flow** welcomes the user and **routes** to **Booking** and **Support**  
- [ ] **Support Flow** answers services/prices and hours/location using `elite-cuts-data.json`  
- [ ] **Fallback / no-match** paths are tested  
- [ ] **Test Agent** runs: happy path, **partial** utterance, **garbage** utterance  
- [ ] Video recorded (**&lt; 10 min**) using `VIDEO_DEMO_SCRIPT.md`  
- [ ] Screenshots captured; **TA emails** added as **Reviewer** (or as specified)  
- [ ] New **Lab 10** GitHub repo created; `origin` updated; all commits pushed  
- [ ] Re-**export** agent to `lab10/dialogflow-export/` if the console changed after this report  

---

*End of Lab 10 submission report (draft for Group 16).*
