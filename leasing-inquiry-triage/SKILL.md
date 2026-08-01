---
name: cre-leasing-inquiry-triage
description: Triage inbound commercial real estate (CRE) leasing inquiries from prospective tenants, arriving by email, web form, phone transcript, or DM. Extracts key deal facts, scores urgency and fit, drafts a broker-ready response, and outputs a structured record for CRM logging. Use this whenever a leasing broker, property manager, or brokerage ops team needs to process a new prospective-tenant inquiry quickly, flag which inquiries deserve immediate attention versus which are low-fit or low-intent, or reduce response time on inbound leasing leads (LoopNet, Crexi, website forms, walk-in calls). Always trigger this skill for tasks involving "leasing inquiry," "tenant inquiry," "space inquiry," "prospective tenant," or "inbound lead" in a CRE/brokerage context, even if the user doesn't explicitly ask for "triage."
---

# CRE Leasing Inquiry Triage

A skill for processing inbound prospective-tenant leasing inquiries: extracting the
deal facts, scoring the lead, drafting a response, and preparing a clean record for
CRM entry. Built for the gap between "inquiry arrives" and "broker has time to
respond," which is where brokerages lose deals to slower-moving competitors.

This skill assumes a human approval step before anything is sent. It prepares the
draft and the recommendation; a person decides whether to send it, edit it, or
handle the inquiry personally. It does not send messages or write to a CRM directly.

## When to use this

- A leasing broker or brokerage ops person has a new inbound inquiry (email, LoopNet/
  Crexi message, website contact form, or a call/voicemail transcript) about an
  available space and wants it processed quickly.
- Someone wants a batch of inquiries prioritized (which ones need same-day attention).
- Someone wants a consistent, professional first-response draft rather than an ad hoc
  reply.

## Step 1: Extract the deal facts

From the raw inquiry text (email body, form submission, or call transcript), pull out:

- **Contact info**: name, company, email, phone (note if any are missing, that's a
  quality signal, see Step 2)
- **Space requirement**: square footage needed, use type (office/retail/industrial/
  flex), any stated must-haves (loading dock, parking ratio, ceiling height, etc.)
- **Timeline**: when they need to move in / sign, if stated. Flag "ASAP" or a specific
  near-term date as high urgency.
- **Budget signal**: any rent range or budget mentioned, even implicitly
- **Which listing/property they're asking about**, if identifiable
- **Stated reason or context**: expansion, relocation, new business, renewal shopping,
  etc., if mentioned

If a field isn't present in the inquiry, mark it as "not stated," don't guess or
fabricate a plausible-sounding value.

## Step 2: Score the inquiry

Rate the inquiry on two axes, each High/Medium/Low, with a one-line justification:

**Urgency**: based on stated timeline, tone, and specificity. A generic "please send
info" with no timeline is Low. A specific move-in date within 90 days, or language
indicating an active/competitive search, is High.

**Fit**: based on how well the stated requirement matches the property/listing being
asked about (if known). A requirement wildly mismatched in size or use type (e.g., a
50,000 sqft industrial request against a 2,000 sqft retail listing) is Low fit even if
urgency is high.

Also flag likely **low-quality/spam signals** explicitly, since inbound platform leads
(LoopNet, Crexi, general contact forms) commonly include these:
- No contact info beyond a name, or an obviously generic/throwaway email
- Vague, copy-paste-style requests with no specifics about the space or their business
- Requests that read as data-harvesting rather than a real search (e.g., asking only
  for pricing with zero context)

Do not discard low-quality-flagged inquiries. Flag them clearly so the broker can
deprioritize or spot-check, but the human decides, not the skill.

## Step 3: Draft the response

Write a short, professional first-response draft (3-6 sentences) that:

- Thanks them for the inquiry and confirms which property/listing it's regarding
- Answers the most obvious immediate question if it's answerable from known listing
  facts (e.g., availability, general size range), otherwise says this will be confirmed
- Asks 1-2 specific qualifying questions the intake was missing (timeline, exact
  headcount/footage needed, intended use), rather than a generic "tell me more"
- Proposes a clear, low-friction next step (a call, a tour time, or "reply with X and
  I'll send over the full spec sheet")
- Matches a professional but warm brokerage tone, not overly salesy, not stiff legalese

Do not include pricing commitments, lease terms, or anything that could be read as a
binding offer. Flag explicitly if the inquiry is asking a question that requires the
broker's direct input (e.g., specific rent negotiation) rather than a templated answer.

## Step 4: Prepare the CRM-ready record

Output a structured summary in this format, ready for a human to copy into whatever
CRM the brokerage uses:

```
Contact: [name, company, email, phone]
Property/Listing: [identified property or "unclear, ask"]
Requirement: [sqft, use type, must-haves]
Timeline: [stated or "not stated"]
Budget signal: [stated or "not stated"]
Urgency: [High/Medium/Low] — [one-line reason]
Fit: [High/Medium/Low] — [one-line reason]
Quality flag: [none / possible spam — reason]
Recommended next action: [e.g., "same-day call," "send spec sheet," "low priority, batch reply"]
Draft response: [the drafted message from Step 3]
```

## Batch processing

If given multiple inquiries at once, run Steps 1-4 for each, then present a sorted
summary table (highest urgency + fit first) so the broker can see at a glance which
inquiries need attention first, before reading every draft in full.

## What this skill does not do

- It does not send emails, messages, or make CRM entries automatically. Every output
  requires human review before anything reaches a prospective tenant.
- It does not fabricate listing details, pricing, or availability it wasn't given.
  If listing facts aren't provided alongside the inquiry, it says so rather than
  inventing plausible numbers.
- It is not a lead-generation tool. It processes inquiries that have already arrived,
  it doesn't find new prospects (see adjacent tools like outbound prospecting skills
  for that side of the workflow).
