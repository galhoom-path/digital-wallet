# Requirements — Digital Wallet Coding Challenge

**Source of truth for what “done” means.**  
IDs below map 1:1 to the original challenge brief. Nothing here invents product scope.

| Legend | Meaning |
| --- | --- |
| **MANDATORY** | Must be implemented and verified for **100% challenge completion** |
| **ENCOURAGED** | Brief asks for it strongly; include for a complete submission |
| **OPTIONAL** | Brief allows it; not required for 100% |
| **NOT IN BRIEF** | Engineering quality only — **does not** count toward challenge 100% |

Status: `TODO` / `IN PROGRESS` / `DONE` · Verification: `NOT VERIFIED` / `PASS` / `FAIL`

Stack for implementation: **Laravel 13** — see [`stack.md`](stack.md).

---

## A. Receiving money (brief)

| ID | Priority | Brief requirement (exact intent) | Acceptance (must prove) | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- |
| FR-01 | MANDATORY | Receive bank notifications via webhook | HTTP endpoint accepts the bank payload | TODO | NOT VERIFIED |
| FR-02 | MANDATORY | One webhook may contain multiple transactions (one per line) | N lines → N parsed transactions | TODO | NOT VERIFIED |
| FR-03 | MANDATORY | Body format is controlled by each bank | PayTech and Acme each use their own parser/rules | TODO | NOT VERIFIED |
| FR-04 | MANDATORY | Parse PayTech: Date, Amount, `#`, Reference, `#`, key/value pairs | Exact sample line → correct fields ([`samples.md`](samples.md)) | TODO | NOT VERIFIED |
| FR-05 | MANDATORY | Parse Acme: Amount `//` Reference `//` Date | Exact sample line → correct fields ([`samples.md`](samples.md)) | TODO | NOT VERIFIED |
| FR-06 | MANDATORY | Import parsed transactions into the database | Rows stored with correct values | TODO | NOT VERIFIED |
| FR-07 | MANDATORY | Attach each transaction to a client | Every imported transaction is associated with a client | TODO | NOT VERIFIED |
| DI-01 | MANDATORY | Duplicate bank reports must not change the client’s final transaction list | Same transaction reported 2+ times → stored once | TODO | NOT VERIFIED |
| DI-02 | MANDATORY | Ingestion can be stopped without dropping incoming webhooks | While paused, webhooks are kept durably and processed after resume | TODO | NOT VERIFIED |

---

## B. Sending money (brief)

| ID | Priority | Brief requirement (exact intent) | Acceptance (must prove) | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- |
| FR-08 | MANDATORY | Build the payment-request XML from request details | Output matches the brief’s prescribed XML structure | TODO | NOT VERIFIED |
| FR-09 | MANDATORY | Omit `Notes` when there are no notes | No `<Notes>` element when empty | TODO | NOT VERIFIED |
| FR-10 | MANDATORY | Include `PaymentType` only when value != 99 | Absent for 99; present otherwise | TODO | NOT VERIFIED |
| FR-11 | MANDATORY | Include `ChargeDetails` only when value != SHA | Absent for SHA; present otherwise | TODO | NOT VERIFIED |

Brief scope note (AMB-10): for sending money, **only XML generation** is required — not a send API, not persistence of transfers.

---

## C. Quality & submission (brief)

| ID | Priority | Brief requirement (exact intent) | Acceptance (must prove) | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- |
| PF-01 | MANDATORY | Consider efficiency and scaling (e.g. a 1,000-transaction webhook) | Deterministic 1,000-line test exists; methodology documented; **no invented latency SLA** | TODO | NOT VERIFIED |
| TS-01 | MANDATORY | Solution covered with automated tests | Every **MANDATORY** FR/DI/PF item has at least one passing automated test | TODO | NOT VERIFIED |
| DC-01 | ENCOURAGED | README documentation incl. design decisions | README accurately describes the system, setup, decisions, assumptions | TODO | NOT VERIFIED |
| DC-02 | OPTIONAL | Reviewer-oriented comments where beneficial | Comments only for non-obvious decisions (or none) | TODO | NOT VERIFIED |
| SB-01 | MANDATORY | Separate commit containing framework init files | First Git commit in `solution/` = pristine **Laravel 13** skeleton | TODO | NOT VERIFIED |
| SB-02 | MANDATORY | Work organized in subsequent commits | Later commits are logical and scoped | TODO | NOT VERIFIED |
| SB-03 | MANDATORY | Clean code, standard styling, consistent indentation | Laravel Pint passes on the codebase | TODO | NOT VERIFIED |
| SB-04 | MANDATORY | No commented-out code; no `dd()` / `dump()` | Search finds none in submitted code | TODO | NOT VERIFIED |

---

## D. 100% challenge completion definition

Challenge is **100% complete** when **all of the following are true**:

1. Every row marked **MANDATORY** above has `Impl. = DONE` and `Verif. = PASS` with evidence (tests / commands / review).
2. **ENCOURAGED** DC-01 is Done (treat as required for a professional submission in this mentored track).
3. Stack is **Laravel 13.x** on **PHP 8.5** ([`stack.md`](stack.md)).
4. Documented ASSUMPTIONs ([`assumptions.md`](assumptions.md)) are listed in the README — they fill brief gaps; they are **not** extra features.

**Not required for 100%:** OPTIONAL DC-02 · everything in section E · any feature not listed in A–C.

---

## E. Not in the brief (do not treat as challenge scope)

These improve engineering quality. They must **not** invent bank protocols or expand product scope. They are **out of the 100% brief checklist**.

| ID | Note |
| --- | --- |
| SC-01 | Webhook auth protocol is **undefined** in the brief — do not invent one; document the limitation |
| SC-02 | Treat webhook body as untrusted; bound size (good practice) |
| SC-03 | Escape XML special characters (needed for correct FR-08 output under hostile input) |
| SC-04 | No secrets in Git/logs (submission hygiene) |

Ambiguities that the brief does not answer live in [`assumptions.md`](assumptions.md) as labeled **ASSUMPTION**s — not as new requirements.

---

## F. Coverage map

| Area | IDs |
| --- | --- |
| Receiving | FR-01…FR-07, DI-01, DI-02 |
| Sending (XML only) | FR-08…FR-11 |
| Scale consideration | PF-01 |
| Tests | TS-01 |
| Docs | DC-01 (ENCOURAGED), DC-02 (OPTIONAL) |
| Git / style | SB-01…SB-04 |
| Framework | Laravel 13 — [`stack.md`](stack.md) |

Lesson mapping: [`learning/plan.md`](../learning/plan.md) §8.
