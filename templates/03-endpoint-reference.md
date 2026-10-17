# {{METHOD}} {{/v1/path}}

One line. What does it do, in the reader's words? "Charge a card", not "instantiate a payment intent".

Idempotent? {{yes, `Idempotency-Key` / no}}  
Rate limit: {{N}}/sec  
Sandbox quirks: {{none, or list}}

## Request

| Field | Type | Required | Notes |
|---|---|---|---|
| `amount` | integer | yes | {{Minor units. Min, max, example.}} |
| `currency` | string | yes | {{ISO 4217. Which ones you support.}} |
| `{{field}}` | {{type}} | no | {{Default if left out.}} |

> *Guidance:* Money field? Units. Enum? Every value. Optional? The default. Skip any of those three and you'll answer it in support tickets instead.

```http
{{full request, copy-pasteable}}
```

## Response

```json
{{full response, real-looking IDs}}
```

Then `status`. Every value. Which one's final? Star it. People build their whole order flow on that one word.

## Errors

The three to five this endpoint actually throws. Link the rest to the errors page.

---

### Northwind Pay example (fictional)

`POST /v1/payments`. Makes a payment, gives you a hosted `checkout_url`.

Idempotency key? Yes please, kept 24 hours. Retry with it, you get the original payment back, no double charge. Fils, not dirhams: `4900` means 49.00 AED.

`status` starts at `pending`, then `succeeded` or `failed`. Only a signed `payment.succeeded` webhook means money moved.

Northwind Pay is made up. So are its endpoints and IDs.
