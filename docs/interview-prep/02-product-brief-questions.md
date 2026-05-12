# 02 — Product Brief & One-Pager Questions

## Q: Walk me through a product brief you've written.

I'm building a B2B catalog for my fashion-jewelry business, Panini Jewels. Problem: B2B runs on WhatsApp groups with ~1000 buyers; team hitting two walls — repetitive question volume and no catalog for onboarding. Strategy is hybrid: don't replace WhatsApp, build a catalog layer that makes WhatsApp conversations more efficient. Public pricing, mobile-first, no login to browse. Success measured by onboarding speed, order capture rate, quality. Biggest risk: buyer adoption — buyers love WhatsApp's familiarity — so adoption mechanisms baked into MVP.

The decisions I'm proudest of are *negative* — what we deliberately chose NOT to do. Single-tenant, no MyBillBook integration, no buyer login required to browse. Each was a real conversation with trade-offs.

## Q: Why hybrid model, not pure platform replacement?

Buyers are WhatsApp-native and relationship-driven. WhatsApp wins on familiarity and photo-forwarding to their own customers. Forcing them off destroys what they love and creates adoption risk. Hybrid lets buyers continue using WhatsApp where it works while platform solves operational pain.

**Principle:** When existing alternative is winning on relationship and habit (not just features), don't displace it. Augment it.

## Q: How did you decide what's in scope vs out?

Worked backward from success metrics. Each feature got: does this directly serve onboarding speed, order capture, or quality? Yes → in scope. No → deferred with rationale.

## Q: Tell me about a product decision you changed your mind on.

I proposed "multi-tenant ready" architecture for Panini B2B so we could sell to other manufacturers later. Founder pushed back — other manufacturers' requirements diverge enough that we'd refactor regardless. So we'd be paying complexity now for no future savings. He was right. Changed my mind, documented "single-tenant" as explicit choice.

## Q: How do you keep the brief from becoming stale?

Two mechanisms. Changelog — every meaningful update dated. And brief is referenced (not duplicated) by downstream docs. When downstream contradicts an out-of-scope item, forces upstream update. Brief becomes the rallying point.
