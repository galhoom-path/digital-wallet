# Start here

Welcome. This workspace turns the Digital Wallet Coding Challenge into a mentored training track.

## How sessions work

1. Say **Start the current lesson** (or continue from where you left off).
2. The mentor delivers one Pareto lesson (What/Why → concepts → decision → your task → verification).
3. **You** write the code / run the commands.
4. Paste output or point to files for review.
5. The mentor updates progress with evidence, then names the next lesson.

No quizzes. No waiting for "do you understand?" You can always ask for clarification.

## What you will build

A **Laravel 13** + **PHP 8.5** backend ([releases](https://laravel.com/docs/13.x/releases)) that completes the brief **exactly**:

- Receives bank webhooks (PayTech + Acme formats)
- Imports transactions, attaches them to clients, rejects duplicates
- Can stop ingestion processing without dropping webhooks
- Generates payment-request XML with conditional `Notes` / `PaymentType` / `ChargeDetails`
- Automated tests + clean Git history + styling (mandatory brief quality bars)
- README with design decisions (encouraged → required in this mentored track)

**100% = all MANDATORY IDs (+ DC-01) PASS** in [`docs/requirements.md`](../docs/requirements.md).  
Assumptions fill brief gaps ([`docs/assumptions.md`](../docs/assumptions.md)); they are not extra features.  
Security extras (SC-*) are outside brief 100%.

## Before Lesson 011

A `solution/` placeholder folder exists. Do **not** install Laravel into it yet — that is Lesson 011. Early lessons lock acceptance criteria and decisions so you do not rebuild later.

## Files to know

| File | Purpose |
| --- | --- |
| [`progress.md`](progress.md) | Current lesson and status |
| [`plan.md`](plan.md) | Full 106-lesson curriculum |
| [`../docs/requirements.md`](../docs/requirements.md) | Traceability matrix |
| [`../docs/assumptions.md`](../docs/assumptions.md) | Documented ASSUMPTIONs |
| [`../docs/decisions.md`](../docs/decisions.md) | Engineering decisions log |
| [`../docs/samples.md`](../docs/samples.md) | Bank lines + XML sample |

## Ready?

Open chat and say: **Start the current lesson**
