# Lab 10 – Build Elite Cuts in Dialogflow CX

**Course:** SEG 3125 · **Team 16** · **Due:** April 5, 2026 11:59 PM  
**Reference business:** [Lab 5 site](https://github.com/SEG3125-2026/seg3125-lab-5-team-16) — **Elite Cuts** (same services, stylists, hours).

Dialogflow CX runs in **Google Cloud**. You cannot “compile” the agent from this repo; use this folder as the **spec**. The actual build is in the [Dialogflow CX Console](https://cloud.google.com/dialogflow/cx/docs).

---

## 1. Google Cloud setup (one-time)

1. Create or pick a Google account / GCP project (course may specify project limits).
2. Enable **Dialogflow API** for the project.
3. Open **Dialogflow CX** → Create **Agent**
   - **Display name:** e.g. `EliteCuts-Team16-Lab10`
   - **Location:** per course/TA instructions (often `global` or a regional endpoint).
   - **Default language:** English (add French only if you want—optional for Lab 10).

---

## 2. Flows to create (match Lab 10 slides)

| Flow | Purpose |
|------|--------|
| **Default Start Flow** (enhance) | Welcome, business intro, “what can I do?” |
| **Booking** | Service → date → time → customer name → phone/email → **confirm** → done |
| **Support** | List services, prices, hours, location, contact |
| **Optional: Default Negative** / small flow | Cancel or “start over” if you extend |

Use **separate flows** so your video/screenshots clearly show “all the flows.”

---

## 3. Suggested pages inside **Booking** flow

1. **Start / collect intent** – user wants an appointment.
2. **Service** – parameter `service` (custom entity: salon services).
3. **Stylist** – parameter `stylist` (custom entity).
4. **Date** – `@sys.date` or date parameter.
5. **Time** – `@sys.time` or time period.
6. **Customer** – `customer_name`; `phone` (@sys.phone-number) **or** `email` (@sys.email).
7. **Confirmation** – summarize all slots; yes/no to confirm.
8. **Complete** – “Your booking is reserved” + fake reference e.g. `EC-` + digits (mirror Lab 5).

**Partial input:** If the user says *“Women’s haircut with Sarah tomorrow at 3pm”*, fill whatever the NLU extracts and **only ask route questions** for missing parameters (use **parameter presets** / condition routes in CX).

---

## 4. Entities (requirements: built-in + custom)

### Custom entities (examples)

| Entity | Sample values |
|--------|----------------|
| `salon_service` | Men's Haircut, Women's Haircut, Beard Trim, Hair Color, Wash & Style, Haircut + Beard |
| `stylist` | Sarah Johnson, Michael Chen, Emma Rodriguez, James Wilson, Any Stylist |

Synonyms: e.g. “cut” → Men’s Haircut; “colour” → Hair Color; “MC” → Michael Chen (optional).

### Built-in system entities

Use where possible: **`@sys.date`**, **`@sys.time`** (or time period), **`@sys.email`**, **`@sys.phone-number`**, **`@sys.person` name** if available in your region.

---

## 5. Fulfillment text (templates)

Copy into CX response messages; adjust tone to match Elite Cuts.

- **Welcome:** “Welcome to Elite Cuts — premium salon and barbershop on Main Street in Ottawa. I can help you **book an appointment** or answer **services, hours, and location**. What would you like?”
- **Ask missing service:** “Which service would you like? We offer cuts, beard trim, colour, wash and style, and packages.”
- **Ask missing stylist:** “Do you have a preferred stylist—Sarah, Michael, Emma, James—or should we assign **any available** stylist?”
- **Invalid stylist/day (optional):** “That stylist isn’t available that day. Want another date or a different stylist?”
- **Confirm:** “Here’s your booking: **{service}** with **{stylist}** on **{date}** at **{time}**. Name **{customer_name}**, contact **{phone_or_email}**. Shall I confirm? (yes / no)”
- **Success:** “You’re booked. Reference **EC-{number}**. We’ll see you at Elite Cuts!”

---

## 6. Fallback / no-match

- In **Default Negative** (or each flow’s **No-match**): 2–3 tiers (reprompt → offer menu → “say booking or hours”).
- Video must show **one** error/fallback path (Lab 10 requirement).

---

## 7. Webhooks (optional)

Lab 10 lists webhooks as optional for backend logic. For full marks on “flows + parameters + entities,” **fulfillment messages only** are enough unless your TA requires persistence.

---

## 8. Share agent with TAs

In Dialogflow CX: **Manage** → **Security** / **IAM** (or agent **Share** / **Viewer** per current Google UI) — add TA emails as **Reviewer** or **Dialogflow API Client** as instructed in the official lab handout.

---

## Files in this folder

| File | Contents |
|------|----------|
| `elite-cuts-data.json` | Services, stylists, contact—paste facts into fulfillments |
| `ENTITIES_AND_PARAMETERS.md` | Detailed parameter list |
| `FLOWS_AND_PAGES.md` | Flow diagram + route ideas |
| `TRAINING_PHRASES.md` | Example utterances per intent |
| `VIDEO_AND_SUBMISSION_CHECKLIST.md` | Record ≤10 min + screenshots |

---

## Reference links

- [Dialogflow CX documentation](https://cloud.google.com/dialogflow/cx/docs)
- Lab 5 repo: https://github.com/SEG3125-2026/seg3125-lab-5-team-16  
- Lab 5 deployed: https://seg3125-2026.github.io/seg3125-lab-5-team-16/
