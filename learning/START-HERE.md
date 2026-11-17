# Start here

Welcome. This workspace turns the Digital Wallet Coding Challenge into a mentored **Practice build** (Galhoom Path Track 5).

## How sessions work

1. Say **Start the current lesson** (or continue from where you left off).
2. The mentor runs **PLAN → DO → CHECK → ACT** and delivers one Pareto lesson.
3. **You** write the code / run the commands by hand.
4. Paste output or point to files for review (proof before progress).
5. The mentor updates progress, then names the next lesson.

No quizzes. No waiting for "do you understand?" You can always ask for clarification.

Read the method once: [`METHOD.md`](METHOD.md) (ideas adapted from [study-template](https://github.com/galhoom-path/study-template)).

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
| [`READY.md`](READY.md) | Host preflight (PASS before Lesson 001) |
| [`METHOD.md`](METHOD.md) | How we teach (study-template judgment) |
| [`progress.md`](progress.md) | Current lesson and status |
| [`plan.md`](plan.md) | Full 106-lesson curriculum |
| [`visual-maps/`](visual-maps/) | System diagrams (GitHub-clear Mermaid) |
| [`milestones/`](milestones/) | End-of-milestone review checklists |
| [`../docs/requirements.md`](../docs/requirements.md) | Traceability matrix |
| [`../docs/assumptions.md`](../docs/assumptions.md) | Documented ASSUMPTIONs |
| [`../docs/decisions.md`](../docs/decisions.md) | Engineering decisions log |
| [`../docs/samples.md`](../docs/samples.md) | Bank lines + XML sample |

## Ready?

Preflight checklist: [`READY.md`](READY.md) (should be all PASS before Lesson 001).

Open chat and say: **Start the current lesson**
