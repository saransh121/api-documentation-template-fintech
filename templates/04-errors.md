<!-- Example values use Northwind Pay, a fictional company. -->
# Errors

## Error object
```json
{{ "error": { "code": "...", "message": "...", "param": "...", "request_id": "..." } }}
```
> *Guidance:* Tell readers which fields are stable (safe to code against) and which are human text that may change.

## Codes
| HTTP | `code` | What happened | Retry? |
|---|---|---|---|
| {{400}} | {{...}} | {{...}} | {{no, fix the request}} |

> *Guidance:* The Retry? column is the point of this page. For each code, say: never retry / retry with the same idempotency key / retry after a wait.

## Retrying safely
{{Backoff advice, max attempts, and the rule that retries must reuse the same idempotency key.}}

## Getting help
{{What to send support. Usually the request_id.}}

---
### Northwind Pay example (fictional)
| HTTP | `code` | What happened | Retry? |
|---|---|---|---|
| 400 | `amount_invalid` | Zero, negative, or not in minor units | No, fix it |
| 401 | `key_invalid` | Missing, revoked, or test key on live | No |
| 402 | `card_declined` | Issuing bank said no | Not with that card |
| 409 | `idempotency_conflict` | Same key, different body | No, new key |
| 429 | `rate_limited` | Too many requests | Yes, after `Retry-After` |
| 503 | `server_error` | Our side | Yes, same idempotency key |
