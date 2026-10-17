<!-- Example values use Northwind Pay, a fictional company. -->
# Changelog

> *Guidance:* Newest first. Every entry dated (YYYY-MM-DD). Mark breaking changes clearly and say what readers must do and by when. Link the deprecation policy.

**Deprecation policy:** {{how much notice, where it's announced, how to test early.}}

## {{YYYY-MM-DD}}
**Breaking** · {{What changes, who's affected, deadline, migration steps.}}
**Added** · {{...}}
**Fixed** · {{...}}

---
### Northwind Pay example (fictional)
## 2026-09-30
**Deprecated** · `GET /v1/charges` will stop working on 2027-03-31. Use `GET /v1/payments`. Field mapping is in the migration guide.
**Added** · `payment.refunded` webhook event.
