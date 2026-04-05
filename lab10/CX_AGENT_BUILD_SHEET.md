# Lab 10 - Dialogflow CX Build Sheet (Team 16)

Use this file as your copy/paste reference while building the agent in Dialogflow CX.

## Agent setup

- Agent name: `EliteCuts-Team16-Lab10`
- Language: `English`
- Time zone: `America/Toronto`

## Required entities

### Custom entity: `salon_service`

Values and synonyms:

- Men's Haircut: men's cut, mens haircut, haircut men, male haircut, cut
- Women's Haircut: women's cut, womens haircut, haircut women, female haircut
- Beard Trim: beard, beard shaping, trim beard
- Hair Color: color, colour, dye, hair colouring
- Wash & Style: wash and style, blowout, shampoo style
- Haircut + Beard: combo, haircut beard combo, cut and beard

### Custom entity: `stylist`

Values and synonyms:

- Sarah Johnson: sarah
- Michael Chen: michael, mike
- Emma Rodriguez: emma
- James Wilson: james
- Any Stylist: any, anyone, no preference

## Required parameters

- `service` -> `@salon_service` (required)
- `stylist` -> `@stylist` (required)
- `appointment_date` -> `@sys.date` (required)
- `appointment_time` -> `@sys.time` (required)
- `customer_name` -> text or `@sys.person` (required)
- `phone` -> `@sys.phone-number` (optional if email present)
- `email` -> `@sys.email` (optional if phone present)

Rule: at least one of `phone` or `email` must be captured before confirmation.

## Flow structure

Create these flows:

1. `Default Start Flow`
2. `Booking Flow`
3. `Support Flow`

## Default Start Flow

### Start Page fulfillment

Welcome message:

"Welcome to Elite Cuts, premium hair salon and barbershop on Main Street in Ottawa. I can help you book an appointment or answer services, hours, and location questions. What would you like to do?"

### Start routes

- Route to `Booking Flow` when user asks to book/reserve/appointment
- Route to `Support Flow` when user asks services/prices/hours/location/contact

## Booking Flow pages

Create pages in this order:

1. `Service`
2. `Stylist`
3. `Date`
4. `Time`
5. `Contact`
6. `Confirmation`
7. `Complete`

### Page: Service

- Form parameter: `service`
- Prompt: "Which service would you like? We offer men's haircut, women's haircut, beard trim, hair color, wash and style, and haircut plus beard."
- Transition: when `service` is set -> `Stylist`

### Page: Stylist

- Form parameter: `stylist`
- Prompt: "Do you have a preferred stylist: Sarah, Michael, Emma, James, or any stylist?"
- Transition: when `stylist` is set -> `Date`

### Page: Date

- Form parameter: `appointment_date`
- Prompt: "What date would you like your appointment?"
- Transition: when `appointment_date` is set -> `Time`

### Page: Time

- Form parameter: `appointment_time`
- Prompt: "What time works best for you?"
- Transition: when `appointment_time` is set -> `Contact`

### Page: Contact

Parameters:

- `customer_name` (required)
- `phone` (optional)
- `email` (optional)

Prompt strategy:

- Ask name first if missing.
- If both phone and email are missing, ask: "Please share a phone number or email for confirmation."

Conditional routes:

- If `customer_name` is set AND (`phone` is set OR `email` is set) -> `Confirmation`

### Page: Confirmation

Response:

"Here is your booking: $session.params.service with $session.params.stylist on $session.params.appointment_date at $session.params.appointment_time for $session.params.customer_name. Contact: $session.params.phone $session.params.email. Should I confirm this appointment?"

Routes:

- On yes/confirm -> `Complete`
- On no/change -> route back to `Service` (or ask which field to change and route accordingly)

### Page: Complete

Response:

"Great, your appointment is confirmed at Elite Cuts. Your reference is EC-1024. We look forward to seeing you."

## Support Flow pages

Create two pages:

1. `Services Info`
2. `Hours Location`

### Services Info fulfillment

"Here are our services: Men's Haircut $35 (30 min), Women's Haircut $55 (45 min), Beard Trim $25 (20 min), Hair Color $85 (90 min), Wash and Style $40 (30 min), Haircut plus Beard $50 (45 min)."

### Hours Location fulfillment

"We're located at 123 Main Street, Ottawa. Phone: (613) 555-0123. Email: info@elitecuts.ca. Hours are Monday to Friday 9 AM to 7 PM, Saturday 8 AM to 6 PM, and Sunday 10 AM to 4 PM."

## No-match / fallback

Add no-match responses at flow level:

1. "Sorry, I didn't catch that. You can say book appointment, services, or hours."
2. "I can help with booking, service information, and opening hours. What would you like?"

## Training phrase minimums

- Booking start intent: at least 10
- Services intent: at least 10
- Hours/location intent: at least 8
- Confirmation yes/no: at least 6 each

Use `TRAINING_PHRASES.md` as your phrase bank.
