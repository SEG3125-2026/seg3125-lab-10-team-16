# Lab 10 - Video Demo Script (Under 10 Minutes)

Use this exact sequence while recording.

## 0) Opening (20-30s)

Say:

"This is Team 16's Dialogflow CX agent for Elite Cuts. I will show welcome, booking, partial input handling, fallback handling, and the flow/entity setup in the console."

## 1) Welcome (30s)

User:

"Hi"

Expected bot behavior:

- Greets user
- Mentions booking/support options

## 2) Booking happy path (2-3 min)

User:

"I want to book an appointment"

Then provide requested fields one-by-one when prompted:

- Service: "Women's haircut"
- Stylist: "Sarah"
- Date: "Tomorrow"
- Time: "3 PM"
- Name: "Eknoor Goraya"
- Contact: "eknoor@example.com"
- Confirm: "Yes"

Expected bot behavior:

- Collects all required slots
- Summarizes booking
- Confirms with a reference code

## 3) Partial-information handling (1-2 min)

User:

"Men's haircut with Michael next Friday at 10 AM"

Expected bot behavior:

- Auto-fills service/stylist/date/time
- Asks only missing information (name + phone/email)

Provide:

- Name: "Pierre Georges"
- Contact: "(613) 555-2222"
- Confirm: "Yes"

## 4) Fallback case (45s)

User:

"I want a spaceship haircut on Mars"

Expected bot behavior:

- No-match/fallback response
- Guidance back to valid options

## 5) Support questions (1 min)

User:

- "What services do you offer?"
- "What are your hours?"
- "Where are you located?"

Expected bot behavior:

- Lists services/prices
- Gives hours
- Gives address/contact info

## 6) Console evidence (2 min)

In Dialogflow CX console, show:

1. Flows list (Default Start, Booking, Support)
2. Booking pages and route chain
3. Parameters on booking pages
4. Custom entities (`salon_service`, `stylist`)
5. Built-in entities in parameter types (`@sys.date`, `@sys.time`, `@sys.email`, `@sys.phone-number`)

## 7) Close (10-15s)

Say:

"This completes all required Lab 10 features: welcome, booking, partial handling, missing field prompts, confirmation, fallback, and flow/entity configuration."
