# CRE Leasing Skills

Open-source Claude/agent skills for commercial real estate leasing operations.

## Skills

### `leasing-inquiry-triage/`
Triage inbound prospective-tenant leasing inquiries (email, web form, LoopNet/
Crexi message, or call transcript). Extracts deal facts, scores urgency and
fit, drafts a broker-ready first response, and outputs a structured record
for CRM logging. Human-approval-gated: it prepares the draft and the
recommendation, it does not send anything or write to a CRM automatically.

## Why this exists

Most published CRE AI tooling covers deal analysis after paperwork exists,
rent rolls, offering memos, financial statements. Nothing published covers
the moment before that: when a prospective tenant's inquiry arrives and
someone has to respond fast or lose them to a faster-moving broker. This
repo starts filling that gap.

## License

Apache 2.0. Free to use, modify, and redistribute.

## Contributing

Issues and PRs welcome, especially from working CRE brokers and ops teams
who can point out where the triage logic gets something wrong in practice.
