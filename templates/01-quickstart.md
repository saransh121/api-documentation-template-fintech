# Quickstart: {{your first successful call}}

> *Guidance:* Pick one goal and phrase it as something the reader will actually see happen. "You'll charge a test card 49.00 AED and watch `paid` show up in your logs" beats "Learn how payments work". Then tell them what to bring and roughly how long it'll take. Delete this note once you're done.

**Bring:** a test account, your runtime and version, and about {{N}} minutes.

## Grab your test keys

Point to the exact dashboard screen. Then say which key is the secret one, and spell out where it must never end up: browser code, a mobile bundle, a public repo.

## Send one request

Keep it to the required fields and make it copy-pasteable. Nobody wants to assemble a request from three paragraphs.

> *Guidance:* Put the money format right beside the amount. If it's minor units, show the maths once: `4900` is 49.00 AED.

## Check that it worked

Show what success looks like from the reader's side. A response body, a row in the dashboard, a webhook landing.

> *Guidance:* Is the real confirmation a webhook? Say so here and link to the webhooks page. A redirect or a bare `200` should never look like "paid".

## Break it on purpose

Give one test card or account that fails, and show what the reader gets back. People trust a quickstart more once they've seen it fail cleanly.

## Where to go next

Authentication, webhooks, errors. Link all three.

---

### Northwind Pay example (fictional)

You need a free test account, Node 18 or newer, and about fifteen minutes.

First, copy `sk_test_...` from **Developers → API keys**. It stays on your server.

Next, call `POST /v1/payments` with `amount: 4900`, `currency: "AED"` and a `return_url`. We count in fils, so `4900` is 49.00 AED, not 4,900 dirhams.

Open the `checkout_url` you get back and pay with `4000 0000 0000 0077`. A `payment.succeeded` webhook hits your endpoint a second or two later. That event is what means paid. The redirect isn't.

Last, try `4000 0000 0000 0002`. It's declined every time: you'll get `payment.failed`, and the order stays unpaid.

Northwind Pay is made up. So are its keys, cards and URLs.
