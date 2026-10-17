<!-- Example values use Northwind Pay, a fictional company. -->
# {{METHOD}} {{/v1/path}}

{{One sentence: what this does, in the reader's terms.}}

**Idempotent:** {{yes, send `Idempotency-Key` / no}} · **Rate limit:** {{N per second}} · **Test mode:** {{differences, if any}}

## Request
| Field | Type | Required | Description |
|---|---|---|---|
| {{amount}} | {{integer}} | {{yes}} | {{Minor units. Range. Example.}} |
| {{currency}} | {{string}} | {{yes}} | {{ISO 4217 code. Supported list.}} |

> *Guidance:* For every money field, state units. For every enum, list every value. For every optional field, say what the default is.

```http
{{full example request}}
```

## Response
```json
{{full example response}}
```
| Field | Description |
|---|---|
| {{status}} | {{Every possible value, and which one is final.}} |

## Errors
{{The 3 to 5 errors this endpoint most often returns, linked to the errors page.}}

---
### Northwind Pay example (fictional)
`POST /v1/payments` creates a payment and returns a hosted `checkout_url`. Idempotent with `Idempotency-Key` (kept for 24 hours). `status` starts as `pending` and ends as `succeeded` or `failed`. Only a signed `payment.succeeded` webhook means money moved.
