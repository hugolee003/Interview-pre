<!-- DECISION-2D1E31F1 -->
## Decision: Use Stripe for all payments; no alternate processor

**Status**: Active  
**Date**: 2026-11-05  
**Severity**: Warning

**Rules**:
```json
{
  "conditions": [
    {
      "type": "file",
      "pattern": "**/*",
      "content_rules": [
        {
          "mode": "string",
          "patterns": [
            "Paddle",
            "LemonSqueezy",
            "Adyen"
          ]
        }
      ]
    }
  ],
  "match_mode": "any"
}
```

### Context

**Decision:** All payment collection in DevRamp must go through Stripe. We selected Stripe for multi-currency, dispute automation, and the existing Stripe Customer/Subscription models in the DB. Do not introduce a new payments vendor (e.g. Paddle, LemonSqueezy, Adyen) for subscription billing. One-off refunds and payouts are out of scope for this decision.
