<!-- Example values use Northwind Pay, a fictional company. -->
# Authentication

## Keys and environments
| Key | Prefix | Where it's used | Secret? |
|---|---|---|---|
| {{secret key}} | {{sk_test_ / sk_live_}} | {{server}} | {{yes}} |
| {{public key}} | {{pk_}} | {{browser/app}} | {{no}} |
| {{webhook secret}} | {{whsec_}} | {{webhook verification}} | {{yes}} |

> *Guidance:* Say plainly what happens if a test key hits the live URL, or the other way round.

## Sending the key
{{Header name and format, with one curl example.}}

## Rotating and revoking
{{How to roll a key without downtime. Whether old keys keep working for a grace period, and how long.}}

## Never do this
- {{Put secret keys in front-end code, mobile bundles or public repos.}}
- {{Log full keys. Log the last 4 characters at most.}}

---
### Northwind Pay example (fictional)
`Authorization: Bearer sk_test_51Hx...`. A test key on the live base URL returns `401 key_invalid`. Rolled keys keep working for 24 hours so you can deploy the new one.
