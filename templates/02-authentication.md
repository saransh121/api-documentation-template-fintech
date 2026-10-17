# Authentication

Which key goes where. That's the whole page, really. Lead with it.

## Keys and environments

| Key | Looks like | Used from | Keep secret? |
|---|---|---|---|
| Secret key | {{sk_test_ / sk_live_}} | Your server | Yes |
| Publishable key | {{pk_test_ / pk_live_}} | Browser or app | No |
| Webhook secret | {{whsec_}} | Webhook handler | Yes |

> *Guidance:* Test key, live URL. Everybody does it once. Say what error they'll get, word for word.

## Sending the key

Header name. Format. One curl that runs as pasted. Done.

## Rotating and revoking

Rolling a key: zero downtime, or a gap? Grace period on the old one, in hours? Leaked key: which button, how fast?

## Please don't

Secret keys in front-end code, a mobile bundle, a public repo. No. Full keys in logs? Also no. Last four characters, max.

---

### Northwind Pay example (fictional)

`Authorization: Bearer sk_test_51Hx...`

Test key against live? `401 key_invalid`. Rolled keys keep working 24 hours, so deploy the new one in that window. Webhooks use the `whsec_` secret instead of your API key.

Northwind Pay is made up. So are its keys and URLs.
