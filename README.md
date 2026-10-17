> **Free to use. Written by Saransh Rayguru.** Northwind Pay, used in the examples, is a made-up payment company. There's no such API.

# API documentation template for fintech and payment APIs

Six Markdown files. Quickstart, auth, endpoint reference, errors, webhooks, changelog. Copy them in and go. Each has the headings, the questions that page must answer, and a filled-in Northwind Pay version underneath so you can see roughly what finished looks like.

I made this because generic API templates are fine until money's involved. They'll give you a nice slot for "Parameters" and never ask whether `amount` is 49 or 4900. Or what a client should do when the request times out halfway. Or which event means the customer actually paid, as opposed to "got redirected back and we hope". Leave those out of a weather API's docs and someone files a bug. Skip them in payments docs and, sooner or later, a customer pays twice.

## Files

```
templates/
  01-quickstart.md          first working call, fifteen minutes or less
  02-authentication.md      keys, test vs live, rotation, what never ships to a browser
  03-endpoint-reference.md  one endpoint, every field, real request and response
  04-errors.md              the error object, a codes table, which ones are safe to retry
  05-webhooks.md            events, signature check, retries, duplicates, ordering
  06-changelog.md           dated entries, breaking changes, deprecation notices
checklist.md                yes/no checks to run before you publish
```

Copy `templates/` into whatever you use. Docusaurus? MkDocs? Bare GitHub? All fine. Fill the `{{curly braces}}`. Answer each *Guidance* note, then bin it.

My one strong opinion: quickstart first. A gorgeous 40-endpoint reference is no use if nobody outside your team can get one test payment through. Get a stranger to one working call and the rest gets easier to write, because now you know where they trip.

## The stuff generic templates skip

Every template has a spot for these, because each one is a support ticket waiting to happen.

Money format comes first. Minor units or decimals, and how many places per currency? Yen has none. Kuwaiti dinar? Three. Bahraini too. Idempotency next. Which endpoints take a key? For how long do you remember it? Retry with that key, get what back? And the final state. One status, or one event, that says the money moved. Not the redirect. Not `pending`.

Webhooks get their own file for a reason. Signature recipe. Which secret. A loud warning to hash raw bytes, because JSON middleware will quietly rewrite the body and break the check. Retry window. And yes, the same event can land twice, so tell people.

The rest is shorter but still bites. Test cards or accounts for every failure you document, not just the happy one. What's different between sandbox and live, written down before launch day instead of discovered on it. Rate limits as actual numbers. What you store, mask or never return when it comes to card data and ID documents. And how much notice you give before deprecating something.

## A taste: the errors page

Here's part of `04-errors.md`, filled in for Northwind Pay. The column people forget is the last one.

```text
HTTP  code                  meaning                               retry?
400   amount_invalid        zero, negative, or not in minor units no, fix it
402   card_declined         issuing bank said no                  not with that card
409   idempotency_conflict  same key, different body              no, new key
429   rate_limited          slow down                             yes, after Retry-After
503   server_error          our fault                             yes, same idempotency key
```

Leave that column out and each client team guesses. Some of them guess "retry the decline".

## Need docs like this for your own API?

I take on API docs, quickstarts and help-centre work for fintech and SaaS teams. Five-plus years of building banking software taught me to go looking for the awkward cases first.

Fiverr: [I will write clear technical documentation and user guides](https://www.fiverr.com/your_solution_/write-clear-technical-documentation-and-user-guides) · Contra: [contra.com/saransh_rayguru_bcplkfab](https://contra.com/saransh_rayguru_bcplkfab) · Longer sample: [payment-api-integration-nodejs-guide](https://github.com/saransh121/payment-api-integration-nodejs-guide)

MIT licence. Use it in commercial docs, change whatever you like. A star's appreciated but not required.
