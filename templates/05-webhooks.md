<!-- Example values use Northwind Pay, a fictional company. -->
# Webhooks

## Events
| Event | Sent when | Final? |
|---|---|---|
| {{payment.succeeded}} | {{...}} | {{yes}} |

## Verifying the signature
{{Header name. Exactly what is signed (timestamp + raw body?). Algorithm. Which secret.}}

> *Guidance:* Warn about raw bodies. Most frameworks parse JSON before your handler runs, and the re-serialised body won't match the signature. Show the fix for at least one framework.

{{code sample}}

## Responding
{{Status code to return, time limit, what counts as a failure.}}

## Retries, duplicates and order
- **Retries:** {{schedule and how long you keep trying.}}
- **Duplicates:** {{the same event can arrive more than once. Tell readers to dedupe on event ID.}}
- **Order:** {{whether events can arrive out of order, and what to do about it.}}

## Testing locally
{{Tunnel tool or CLI, and how to resend an event from the dashboard.}}

---
### Northwind Pay example (fictional)
Header `NWP-Signature`: hex HMAC-SHA256 of the raw request body, keyed with your `whsec_` secret. Use `express.raw()` on that route, not `express.json()`. Reply `200` within 10 seconds. Failed deliveries are retried for 3 days, so dedupe on `event.id`.
