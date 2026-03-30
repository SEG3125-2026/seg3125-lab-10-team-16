# Dialogflow CX – Parameters & entities (Elite Cuts)

## Session parameters to collect (booking)

| Parameter | Type | Notes |
|-----------|------|--------|
| `service` | Custom: `salon_service` | Required before confirm |
| `stylist` | Custom: `stylist` | Include “Any Stylist” |
| `appointment_date` | `@sys.date` | Ask only if missing |
| `appointment_time` | `@sys.time` or free slot + validation | 30-min slots in Lab 5; bot can summarize “3 PM” |
| `customer_name` | text / `@sys.person` | Letters/spaces like Lab 5 |
| `phone` | `@sys.phone-number` | Optional if email captured |
| `email` | `@sys.email` | Optional if phone captured |

**Rule for video:** Show the bot asking only for **missing** fields after a rich utterance.

## Custom entities

### `salon_service`

- Men's Haircut  
- Women's Haircut  
- Beard Trim  
- Hair Color  
- Wash & Style  
- Haircut + Beard  

**Synonyms (examples):** “beard” → Beard Trim; “color/colour” → Hair Color; “blowout” → Wash & Style; “combo” → Haircut + Beard.

### `stylist`

- Sarah Johnson  
- Michael Chen  
- Emma Rodriguez  
- James Wilson  
- Any Stylist  

**Synonyms:** first names only; “anyone” / “no preference” → Any Stylist.

## Built-in entities (use explicitly)

Enable routes that use: **date**, **time**, **email**, **phone-number** (exact resource names depend on CX version—use the entity picker in console).

## Confirmation

- Final step must echo **all** collected parameters and ask for explicit confirmation (yes/no intent or `@sys.confirmation` pattern).
