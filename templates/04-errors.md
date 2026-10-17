# Errors

Two jobs for this page. Tell people what broke. Tell them whether to try again.

## The error object

```json
{
  "error": {
    "code": "{{stable_machine_code}}",
    "message": "{{human text, may change}}",
    "param": "{{field that caused it, if any}}",
    "request_id": "{{req_...}}"
  }
}
```

> *Guidance:* Which fields can people code against? Usually `code`. Which are just words for humans and might change next month? Usually `message`. Say so, or someone will `if (message == ...)` their way into an outage.

## Codes

| HTTP | `code` | What happened | Retry? |
|---|---|---|---|
| {{4xx}} | `{{code}}` | {{plain words}} | {{never / same key / after a wait}} |

That last column. Don't skip it. Three possible answers, pick one per row: never, retry with the same idempotency key, or wait then retry.

## Retrying safely

Backoff: how long, how many tries? And the rule people forget: a retry reuses the *same* idempotency key. New key = new charge.

## Getting help

What should they paste into a support ticket? Normally just the `request_id`. Tell them where to find it.

---

### Northwind Pay example (fictional)

```text
HTTP  code                  what happened                         retry?
400   amount_invalid        zero, negative, or not in minor units no, fix it
401   key_invalid           missing, revoked, or test key on live no
402   card_declined         issuing bank said no                  not with that card
409   idempotency_conflict  same key, different body              no, new key
429   rate_limited          too many requests                     yes, after Retry-After
503   server_error          our side                              yes, same idempotency key
```

Northwind Pay is made up. So are its error codes.
