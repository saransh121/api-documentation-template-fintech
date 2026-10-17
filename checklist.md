# Pre-publish checklist

Tick every line, or write down why it doesn't apply.

**Quickstart**
- [ ] A new developer can reach one working call without asking anyone.
- [ ] Time estimate and prerequisites are at the top.
- [ ] The success check is the real one (webhook or final status), not a redirect.
- [ ] At least one failure path is shown.

**Money**
- [ ] Every amount field states minor units or decimals.
- [ ] Supported currencies are listed, with decimal places where they differ.
- [ ] The single "money moved" status or event is named.

**Safety**
- [ ] Secret keys are marked server-only everywhere they appear.
- [ ] Idempotency: which endpoints, header name, how long keys are kept.
- [ ] Webhook signature steps include the raw-body warning.
- [ ] Docs say what the API stores, masks or never returns (cards, ID documents, personal data).

**Errors and limits**
- [ ] Every error code has a "retry?" answer.
- [ ] Rate limits are numbers, with the response header and what to do.
- [ ] Timeouts are stated.

**Testing**
- [ ] Test cards/accounts exist for every documented outcome.
- [ ] Sandbox vs live differences are written down.

**Upkeep**
- [ ] Changelog entries are dated; breaking changes have deadlines.
- [ ] Deprecation notice period is stated.
- [ ] Every code sample has been run against the current API.
