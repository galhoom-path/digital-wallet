# Decisions log

Record lasting engineering decisions here. Never edit an accepted entry — add a new entry that supersedes it.

Format per entry:

```text
## D-XXX — Title
Date:
Status: ACCEPTED | SUPERSEDED by D-YYY
Context:
Options considered:
Decision:
Why:
Consequences / trade-offs:
Related: requirement IDs, assumption IDs, lessons
```

## Seeded decisions (from curriculum analysis — refine in lessons)

### D-000 — Framework and PHP

- **Status:** ACCEPTED (owner lock, 2026-11-17)
- **Decision:** Implement the deliverable with **Laravel 13.x** (`^13.0`) on **PHP 8.5**.
- **Why:** Owner requirement; PHP 8.5 is the highest version in Laravel 13’s official support table ([releases](https://laravel.com/docs/13.x/releases): 8.3–8.5). PHP 8.6 is rejected (not listed / not GA-safe for this submission).
- **Consequences:** First commit (SB-01) must be a pristine Laravel 13 skeleton. Local/CI runtime should be PHP 8.5.x. Do not use Laravel 11/12 or PHP 8.6.
- **Related:** SB-01, [`stack.md`](stack.md)

### D-001 — Transaction identity

- **Status:** PROPOSED (locked in Lesson 001)
- **Decision:** Unique key = `(bank, reference)` enforced by a composite unique index.
- **Why:** Cross-bank reference collision in samples; DB constraint is race-safe.
- **Related:** DI-01, AMB-04

### D-002 — Receive vs process

- **Status:** PROPOSED (Lesson 003 / AMB-08)
- **Decision:** HTTP always durably stores the raw webhook (2xx = recorded). Parsing/import runs asynchronously. Pause affects workers only.
- **Why:** DI-02 no-data-loss; framework `queue:pause` / `queue:continue`.
- **Related:** FR-01, DI-02, AMB-08

### D-003 — Client association

- **Status:** PROPOSED (AMB-01)
- **Decision:** Client identified by route parameter on a client-specific webhook URL.
- **Related:** FR-07, AMB-01

### D-004 — Money representation

- **Status:** OPEN (decide in Lessons 016–017)
- **Options:** integer minor units vs `DECIMAL(p,s)`. Never floats.
- **Related:** AMB-06, FR-06

### D-005 — Parser design

- **Status:** OPEN (decide in Lesson 033)
- **Likely direction:** one parser class per bank behind a shared interface (Strategy).
- **Related:** FR-03, AMB-02

### D-006 — XML generation

- **Status:** OPEN (decide in Lessons 082 / AMB-10)
- **Likely direction:** pure PHP generator from a typed input object; no HTTP endpoint.
- **Related:** FR-08–FR-11, SC-03

### D-007 — Idempotent writes

- **Status:** OPEN (decide in Lesson 060)
- **Constraint:** must cooperate with the unique index under concurrency.
- **Related:** DI-01

### D-008 — Queue driver

- **Status:** OPEN (decide in Lesson 056)
- **Related:** DI-02, PF-01

## Rule

Dispatch queue jobs that load a newly inserted row **after** the DB commit (`afterCommit`). See `docs/learning-from-mistakes/`.


## D-WALLET-PHP86 — Language org vs Laravel stack (2026-11-21)

- **Decision:** Galhoom Path **language** curricula target **PHP 8.6**. This wallet deliverable stays on **PHP 8.5** while [Laravel 13 releases](https://laravel.com/docs/13.x/releases) list official support as **8.3–8.5**.
- **Why:** Claiming Laravel 13 + PHP 8.6 before the framework documents it would lower professionalism.
- **Consequences:** Revisit this ADR when Laravel's support table includes 8.6; then bump `docs/stack.md` + CI in the same change.
