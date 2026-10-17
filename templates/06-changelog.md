# Changelog

Newest at the top. Date on every entry. YYYY-MM-DD, always. Is 03/04 March or April? Depends who's reading.

> *Guidance:* Breaking change? Make it impossible to miss. Who's hit. What to do. By when. Migration steps live in one place; link there.

**Deprecation policy:** {{notice period}}. Announced in {{where: this page, email, status page}}. Test early via {{header, flag or sandbox}}.

## {{YYYY-MM-DD}}

- **Breaking:** {{what changes, who it hits, deadline, link to migration}}
- **Added:** {{new thing, one line}}
- **Fixed:** {{bug, in the reader's terms}}

Empty sections? Leave them out. A "Fixed: none" line is just noise.

---

### Northwind Pay example (fictional)

## 2026-09-30

- **Deprecated:** `GET /v1/charges` dies 2027-03-31. Use `GET /v1/payments` instead (field mapping: migration guide).
- **Added:** `payment.refunded` webhook event.

Northwind Pay is made up. So is this release.
