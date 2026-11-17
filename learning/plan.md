plan.md [989L]
# Digital Wallet Coding Challenge — Mentoring Plan
> Private mentoring curriculum and checkpoints.
> Live position: [`progress.md`](progress.md). Requirements: [`../docs/requirements.md`](../docs/requirements.md).
> This file lives outside `solution/` and is never part of the submitted repository.
... [lean-ctx: omitted 1 lines]
## 000. Pareto Principle — High-Impact Microlearning Policy (latest; overrides lesson format and length rules below)
Every lesson teaches the ~20% of concepts that deliver ~80% of the practical value needed **now**. Optimize explanation
... [lean-ctx: omitted 3 lines]
2. **High-Value (20%)** — 1–3 essential concepts; unfamiliar terms defined; only knowledge needed now.
... [lean-ctx: omitted 7 lines]
**Avoid:** long introductions, repetition, excess examples or analogies, extensive comparisons, large code blocks,
academic detail, unrelated edge cases, multiple tasks, quizzes, mandatory questions, conversational gates.
**Internal checklist per lesson:** what must be known to implement correctly · which decision matters most · what can be
... [lean-ctx: omitted 1 lines]
**Never omitted for brevity:** financial data integrity, idempotency, database constraints, concurrency, webhook
durability, security, error handling, automated testing, explicit PDF requirements. These may take several micro-lessons.
... [lean-ctx: omitted 2 lines]
## 00. Teaching Model Policy (overrides every conflicting instruction below; lesson format superseded by Section 000)
**Autonomous teaching, zero mandatory questions.** The mentor teaches proactively; the mentee is never interrogated.
... [lean-ctx: omitted 8 lines]
| Research, analyze requirements, explain concepts, recommend decisions, compare alternatives, explain trade-offs, give implementation instructions, review code, explain fixes, track progress | Write all application code, run commands, apply the techniques, test the application, own and understand the solution |
... [lean-ctx: omitted 5 lines]
4. **Recommended Engineering Decision** (what, why, alternatives, why not, trade-offs)
... [lean-ctx: omitted 1 lines]
6. **Verification** (expected behavior and testing guidance)
7. **Interview Knowledge** (the likely question *and* its correct reasoning, explained directly)
8. **Checkpoint** (status recorded here; learned / implemented / remaining)
... [lean-ctx: omitted 1 lines]
- **Conceptual lessons** are COMPLETED once the explanation is delivered.
- **Implementation lessons** are COMPLETED only with observed evidence (command output, passing tests, reviewed code).
- The mentee may move ahead before an implementation is verified. That lesson then stays `IN PROGRESS` / `NOT VERIFIED`.
... [lean-ctx: omitted 1 lines]
## 0. Engineering Decision-Making Policy (mandatory, overrides earlier instructions)
**Rule: Never assume the mentee already knows the correct answer.**
The mentor investigates, evaluates, recommends, justifies, and teaches. The mentee implements, tests, and owns the solution.
... [lean-ctx: omitted 1 lines]
1. **Investigate** — PDF requirements, official Laravel 13 docs, established practice.
2. **Evaluate** — realistic approaches vs. correctness, simplicity, security, performance, scalability, maintainability.
... [lean-ctx: omitted 4 lines]
7. **Explain the interview reasoning** — the mentor states the likely reviewer question and its correct answer directly.
Decision explanation format (concise, proportionate to importance):
**Decision · Why · Alternatives · Why Not · Trade-offs · Implementation · Interview Knowledge**
... [lean-ctx: omitted 2 lines]
- Missing business requirements: identify the ambiguity, list interpretations, recommend a minimal defensible
... [lean-ctx: omitted 3 lines]
## 1. Environment Baseline
**Locked stack:** Laravel **13.x** on **PHP 8.5** — see [`../docs/stack.md`](../docs/stack.md) and [official releases](https://laravel.com/docs/13.x/releases).
... [lean-ctx: omitted 3 lines]
| PHP | **8.5.x** (confirm with `php -v`; Laravel 13 official range is 8.3–8.5) |
... [lean-ctx: omitted 4 lines]
| Mentoring layout | `docs/`, `learning/`, `AGENTS.md`, `.cursor/rules/` — not submitted |
| Challenge 100% | All **MANDATORY** (+ ENCOURAGED DC-01) IDs in [`../docs/requirements.md`](../docs/requirements.md) PASS — no invented extras |
**Machine preflight (2026-11-17):** PHP 8.5.12, Composer 2.11.2, Git 2.56, required extensions present, Composer diagnose OK with 7-Zip — see [`READY.md`](READY.md).

Still open until later lessons: database engine choice (Lesson 010), Git user identity if unset (Lesson 009).
## 2. Requirements Traceability Baseline
Status legend: `TODO` / `IN PROGRESS` / `DONE`. Verification: `NOT VERIFIED` / `PASS` / `FAIL`.
### Functional
| ID | Requirement | Source (PDF) | Area | Acceptance criteria | Tests | Impl. | Verif. |
... [lean-ctx: omitted 1 lines]
| FR-01 | Receive bank notifications via webhook | p1 "Receiving Money" | HTTP layer | Endpoint accepts bank payloads | TBD | TODO | NOT VERIFIED |
... [lean-ctx: omitted 2 lines]
| FR-04 | Parse PayTech format: Date, Amount, `#`, Reference, `#`, key/value pairs | p1 | Parsing | Sample line parsed into correct fields | TBD | TODO | NOT VERIFIED |
... [lean-ctx: omitted 3 lines]
| FR-08 | Build the payment-request XML from request details | p1-2 "Sending Money" | XML | Output matches prescribed structure | TBD | TODO | NOT VERIFIED |
... [lean-ctx: omitted 1 lines]
| FR-10 | Include `PaymentType` only when value != 99 | p2 | XML | Absent for 99, present otherwise | TBD | TODO | NOT VERIFIED |
| FR-11 | Include `ChargeDetails` only when value != SHA | p2 | XML | Absent for SHA, present otherwise | TBD | TODO | NOT VERIFIED |
### Data Integrity
| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
... [lean-ctx: omitted 1 lines]
| DI-01 | Duplicate bank reports must not change the client's final transaction list | p1 | DB + processing | Same transaction reported 2+ times -> stored once | TBD | TODO | NOT VERIFIED |
| DI-02 | Ingestion can be stopped without dropping incoming webhooks | p1 | Ingestion | While paused, webhooks are durably kept and processed after resuming | TBD | TODO | NOT VERIFIED |
### Performance
| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
... [lean-ctx: omitted 1 lines]
| PF-01 | Consider efficiency and scaling; e.g. parse a 1,000-transaction webhook with acceptable performance | p3 | Parsing + persistence | Test with 1,000 lines; methodology documented | TBD | TODO | NOT VERIFIED |
### Testing
| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
... [lean-ctx: omitted 1 lines]
| TS-01 | Solution covered with automated tests | p3 | `tests/` | Every FR/DI/PF item has a passing test | — | TODO | NOT VERIFIED |
### Documentation
| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
... [lean-ctx: omitted 1 lines]
| DC-01 | README documentation (heavily encouraged) incl. design decisions | p3 | `README.md` | Accurately describes the implemented system | — | TODO | NOT VERIFIED |
| DC-02 | Reviewer-oriented code comments where beneficial (optional) | p3 | Code | Comments explain non-obvious decisions only | — | TODO | NOT VERIFIED |
### Submission
| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
... [lean-ctx: omitted 1 lines]
| SB-01 | Separate commit containing framework init files | p3 | Git | First commit = pristine framework | — | TODO | NOT VERIFIED |
... [lean-ctx: omitted 1 lines]
| SB-03 | Clean code, standard styling, consistent indentation | p3 | Code | Pint passes | — | TODO | NOT VERIFIED |
| SB-04 | No commented-out code, no `dd()` / `dump()` | p3 | Code | Search finds none | — | TODO | NOT VERIFIED |
### Security (no explicit PDF requirement — reasonable engineering considerations)
| ID | Consideration | Status |
... [lean-ctx: omitted 1 lines]
| SC-01 | Webhook authentication (PDF defines no protocol; must not be invented — document as limitation/assumption) | TODO |
| SC-02 | Treat webhook body as untrusted input; validate and bound payload size | TODO |
| SC-03 | Safe XML generation (escaping special characters) | TODO |
... [lean-ctx: omitted 1 lines]
## 3. Open Questions — Classification and Recommendations
Type: **TECH** = technical decision (mentor recommends) · **BIZ** = missing business requirement (documented ASSUMPTION).
... [lean-ctx: omitted 3 lines]
| AMB-01 | How is the client identified? Neither sample format contains a client/account field. | BIZ | ASSUMPTION: the client is identified by the request, not the body — the webhook URL registered with the bank is client-specific (route parameter), resolved to an existing client. | The body cannot identify a client, so the identifier must come from the request context. A route parameter is explicit, testable, and adds no fields to the bank's format. | Parse `internal_reference` from PayTech metadata (Acme has no metadata, so it fails for one bank); a custom header (works but hides the contract); a single hard-coded client (does not satisfy "attaching it to the client"). | Desirable but not blocking. Document the assumption in the README. |
... [lean-ctx: omitted 1 lines]
| AMB-03 | PayTech `20250615156,50` — date and amount have no separator. | BIZ | ASSUMPTION: the date is always the first 8 characters in `YYYYMMDD`; the amount is everything before the first `#` after those 8 characters. Validate as a real calendar date. | The sample's reference also starts with `20250615`, which supports a fixed 8-digit date. A fixed width is the only unambiguous way to split. | Regex guessing (cannot be unambiguous without the fixed-width rule). | No. Document it. |
| AMB-04 | What makes a transaction unique (duplicate detection)? | TECH + BIZ | ASSUMPTION: a reference is unique **per bank**. Identity = (bank, reference), enforced by a composite unique index in the database. | Both samples use the **same** reference `[REDACTED:card]` from different banks, so the reference alone is not safe globally. The database constraint is race-safe; application checks are not. | Reference alone (cross-bank collisions); hashing the whole line (a re-report with different metadata formatting would create a duplicate); including the client in the key (unnecessary, because a bank reference identifies one transaction). | No. |
... [lean-ctx: omitted 3 lines]
| AMB-08 | How is ingestion paused, and how is data loss prevented? | TECH | Two stages: (1) the HTTP endpoint **always** stores the raw webhook body durably in the database, then returns 2xx; (2) a queued job parses and imports it. Pausing stops stage 2 only, using Laravel 13's built-in `queue:pause` / `queue:continue` (verified in the official 13.x docs). Raw webhook rows keep a processing status so they can be audited and reprocessed. | Receiving, durably recording, and processing are separate. Pausing workers never touches reception, so nothing is dropped. Using a framework feature means no custom pause flag. | Synchronous processing (cannot be paused without rejecting webhooks); a custom pause flag in config or the database (reinvents a framework feature); relying only on the queue payload without a raw-webhook table (no audit trail, and a lost job loses the data). | No. |
| AMB-09 | XML date `2025-02-25 06:33:00+03` is not strict ISO 8601. | TECH + BIZ | Reproduce the sample format exactly (`Y-m-d H:i:s` plus an hour-only offset). ASSUMPTION: offsets with minutes (e.g. +05:30) are out of scope, or are rendered with minutes. Finalized in the XML lesson. | The PDF shows the expected output. Matching it is the safest reading. | ISO 8601 `2025-02-25T06:33:00+03:00` (deviates from the sample). | No. |
... [lean-ctx: omitted 1 lines]
| AMB-11 | What happens to a malformed line inside a batch? | BIZ + TECH | ASSUMPTION: import valid lines, record or log invalid lines with the reason, and mark the webhook as partially failed. The raw body is always kept, so failed lines can be reprocessed after a fix. | Rejecting a whole batch would withhold valid credits from clients. Idempotency (AMB-04) makes reprocessing safe. | All-or-nothing (one bad line blocks everyone's money); silently dropping lines (data loss without diagnostics). | Desirable but not blocking. Document it. |
## 4. Workspace and Project Structure (mandatory)
```text
<workspace-root>/                         <- mentoring workspace (NOT the submitted Git repo)
├── README.md                             <- how learning works
├── AGENTS.md                             <- mentor constitution
├── .cursor/rules/                        <- mentor + engineering rules
├── docs/                                 <- requirements, assumptions, decisions, samples
├── learning/
│   ├── START-HERE.md
│   ├── progress.md                       <- current position
│   └── plan.md                           <- this curriculum (never inside solution/)
└── solution/                             <- the deliverable; the only Git repository
    ├── app/  bootstrap/  config/  database/  public/  resources/  routes/  storage/  tests/
    ├── artisan  composer.json  phpunit.xml  .env.example  .gitignore
    └── README.md
```
... [lean-ctx: omitted 9 lines]
## 5. Session Resume Protocol
At the start of every session:
... [lean-ctx: omitted 1 lines]
2. Inspect `solution/` (if it exists): files, `git log`, and test results when relevant.
... [lean-ctx: omitted 1 lines]
4. Compare the recorded progress with the actual project. If they disagree, explain the discrepancy and reconcile using verifiable evidence. A file existing is not proof that a lesson is complete.
5. Resume at the correct checkpoint. Never restart the curriculum unnecessarily.
... [lean-ctx: omitted 1 lines]
## 6. Lesson Workflow and Checkpoint Rules
After every lesson:
... [lean-ctx: omitted 1 lines]
2. Verify the completion criteria using evidence (conceptual lessons: explanation delivered).
... [lean-ctx: omitted 3 lines]
Status values: `NOT STARTED` · `IN PROGRESS` · `BLOCKED` · `COMPLETED`.
Never mark a lesson complete without evidence. Never skip lessons silently. Missing prerequisites are inserted
with suffixed IDs (e.g. `Lesson 038a`) so that existing IDs and progress remain stable.
## 7. Lesson Roadmap — 106 lessons, 12 milestones
Fields per lesson: **Learn** = learning objective · **Build** = implementation objective · **Reqs** = requirement IDs ·
**Done when** = completion criteria · **Tests** · **Evidence** · **Decisions** = engineering decisions learned.
### Milestone 1 — Requirements and Acceptance Criteria (001–007)
- [ ] **Lesson 001 — Transaction Identity and Duplicate Acceptance Criteria**
... [lean-ctx: omitted 1 lines]
  - Learn: acceptance criteria (Given/When/Then), transaction identity, natural keys, idempotency;
... [lean-ctx: omitted 4 lines]
    - AC-01 Given client C has no transactions, when the same PayTech line arrives in two separate webhooks for C,
... [lean-ctx: omitted 3 lines]
    - AC-03 Given no transactions exist, when reference `[REDACTED:card]` arrives once from PayTech and once from Acme,
... [lean-ctx: omitted 1 lines]
  - Key concept: identity = (bank, reference) + unique index = idempotent, race-safe duplicate prevention.
  - Implementation: none required · Verification: N/A (criteria verified by tests in Lesson 062)
... [lean-ctx: omitted 1 lines]
    Decisions: identity = (bank, reference) [ASSUMPTION], enforced by a database unique index; a 2xx response means
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-02, FR-03, FR-04, FR-05, AMB-03, AMB-05, AMB-06
... [lean-ctx: omitted 6 lines]
  - Learn: durability, acknowledgment semantics, why a 2xx response must mean "durably recorded."
  - Build: — (mentor provides the pause/resume no-data-loss criteria)
  - Done when: lesson delivered; criteria (paused reception, resumed processing, crash) recorded in this checkpoint.
... [lean-ctx: omitted 5 lines]
  - Done when: lesson delivered; criteria and ASSUMPTION AMB-01 recorded in this checkpoint.
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-08, FR-09, FR-10, FR-11, AMB-09
... [lean-ctx: omitted 2 lines]
  - Done when: lesson delivered; six criteria (Notes on/off, PaymentType 99/other, ChargeDetails SHA/other) recorded in this checkpoint.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 006 — Non-Functional, Security, and Submission Criteria**
  - Status: NOT STARTED · Reqs: PF-01, TS-01, SB-01–SB-04, SC-01–SC-04
  - Learn: the difference between explicit requirements and engineering considerations; not inventing numeric targets.
... [lean-ctx: omitted 1 lines]
  - Done when: lesson delivered; criteria recorded without fabricated performance thresholds.
... [lean-ctx: omitted 3 lines]
  - Learn: likely reviewer questions on requirements and assumptions, with model reasoning.
... [lean-ctx: omitted 3 lines]
### Milestone 2 — Environment, Project Setup, and Git (008–015)
- [ ] **Lesson 008 — Workspace Layout and the `solution/` Directory**
... [lean-ctx: omitted 1 lines]
  - Learn: separating planning artifacts from the deliverable.
... [lean-ctx: omitted 1 lines]
  - Done when: lesson delivered (why `plan.md` stays outside the repository).
... [lean-ctx: omitted 3 lines]
  - Learn: `php -m`, required extensions (`dom`, `xmlwriter`, `pdo_*`, `mbstring`), Git configuration.
... [lean-ctx: omitted 1 lines]
  - Done when: all required extensions are confirmed present.
... [lean-ctx: omitted 3 lines]
  - Learn: SQLite vs MySQL vs PostgreSQL for development, tests, and concurrency semantics.
... [lean-ctx: omitted 1 lines]
  - Done when: recommendation delivered and recorded, including the concurrency-testing trade-off.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 011 — Creating the Laravel 13 Project in `solution/`**
... [lean-ctx: omitted 1 lines]
  - Learn: `composer create-project`, version constraints, verifying the installed framework version.
... [lean-ctx: omitted 1 lines]
  - Done when: `php artisan --version` shows 13.x inside `solution/`.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 012 — Laravel 13 Directory Structure and Request Lifecycle**
... [lean-ctx: omitted 1 lines]
  - Learn: `bootstrap/app.php`, routes, service container, providers, `.env`.
... [lean-ctx: omitted 1 lines]
  - Done when: lesson delivered (request path from `public/index.php` to a route).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 013 — Git Init, `.gitignore`, and the Framework-Initialization Commit**
... [lean-ctx: omitted 1 lines]
  - Learn: what belongs in the init commit; `.env` vs `.env.example`; `vendor/` exclusion.
... [lean-ctx: omitted 1 lines]
  - Done when: `git log` shows one commit with the pristine skeleton only; no secrets tracked.
... [lean-ctx: omitted 3 lines]
  - Learn: `feat`, `fix`, `test`, `refactor`, `docs`, `chore`; one logical change per commit.
... [lean-ctx: omitted 9 lines]
### Milestone 3 — Domain Fundamentals (016–019)
- [ ] **Lesson 016 — Why Floating-Point Numbers Fail for Money**
... [lean-ctx: omitted 1 lines]
  - Learn: IEEE 754 binary floating point; rounding errors.
  - Build: optional throwaway PHP experiment outside `solution/`.
  - Done when: lesson delivered (why `0.1 + 0.2` breaks money math).
... [lean-ctx: omitted 3 lines]
  - Learn: integer minor units vs `DECIMAL(p,s)`; conversions at the boundaries.
... [lean-ctx: omitted 1 lines]
  - Done when: recommendation delivered in the Decision format and recorded under Decisions.
... [lean-ctx: omitted 3 lines]
  - Learn: `CarbonImmutable`, strict format parsing, invalid dates such as `20250231`.
  - Build: — (concept and small isolated experiment)
... [lean-ctx: omitted 2 lines]
- [ ] **Lesson 019 — Data Transfer Objects and `readonly` Classes**
... [lean-ctx: omitted 1 lines]
  - Learn: DTOs, immutability, typed properties, constructor promotion.
... [lean-ctx: omitted 3 lines]
### Milestone 4 — Data Modeling (020–031)
- [ ] **Lesson 020 — Identifying Entities and Drawing the ERD**
  - Status: NOT STARTED · Reqs: FR-06, FR-07, DI-02
  - Learn: entities, relationships, cardinality.
  - Build: — (mentor provides the recommended ERD: clients, webhooks, transactions)
  - Done when: ERD delivered with every relationship justified.
... [lean-ctx: omitted 3 lines]
  - Learn: minimal columns, public identifiers vs internal IDs.
  - Build: — (mentor provides the recommended columns and types; implemented in Lessons 025–027)
  - Done when: recommended design delivered and recorded.
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: DI-02, AMB-08, AMB-11
  - Learn: storing raw payloads, status columns, timestamps for auditing.
  - Build: — (mentor provides the recommended columns and types; implemented in Lessons 025–027)
  - Done when: recommended design delivered and recorded.
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-06, DI-01, AMB-04, AMB-05
  - Learn: storing amount, date, reference, bank, metadata (JSON column trade-offs).
  - Build: — (mentor provides the recommended columns and types; implemented in Lessons 025–027)
  - Done when: recommended design delivered and recorded.
... [lean-ctx: omitted 3 lines]
  - Learn: referential integrity, composite unique index on (bank, reference), index selection.
  - Build: — (mentor provides the recommended constraints and indexes)
... [lean-ctx: omitted 6 lines]
  - Done when: `php artisan migrate` succeeds (observed).
... [lean-ctx: omitted 9 lines]
  - Learn: foreign keys and composite unique indexes in migrations.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 028 — Eloquent Models, Relationships, and Casts**
... [lean-ctx: omitted 1 lines]
  - Learn: `belongsTo`, `hasMany`, attribute casts, mass-assignment protection.
... [lean-ctx: omitted 9 lines]
- [ ] **Lesson 030 — Database Test: the Unique Constraint Rejects Duplicates**
... [lean-ctx: omitted 1 lines]
  - Learn: `RefreshDatabase`, asserting exceptions, testing constraints.
... [lean-ctx: omitted 4 lines]
  - Status: NOT STARTED · Reqs: FR-06, FR-07, DI-01, DI-02
  - Learn: likely reviewer questions on the schema, with model reasoning.
... [lean-ctx: omitted 3 lines]
### Milestone 5 — Parsing (032–045)
- [ ] **Lesson 032 — PHP String and Array Tools for Parsing**
  - Status: NOT STARTED · Reqs: FR-04, FR-05
  - Learn: `explode` with limits, `substr`, `preg_match`, `array_chunk`, strict comparisons.
  - Build: — (isolated examples unrelated to the challenge)
... [lean-ctx: omitted 4 lines]
  - Learn: interfaces, the Strategy pattern, and when conditionals are enough.
... [lean-ctx: omitted 1 lines]
  - Done when: recommendation delivered in the Decision format and recorded under Decisions.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 034 — Implement the Parsed Transaction DTO**
... [lean-ctx: omitted 10 lines]
  - Tests: amount normalization tests · Evidence: — · Decisions: —
- [ ] **Lesson 036 — Amount Normalization: Implementation**
... [lean-ctx: omitted 1 lines]
  - Learn: strict validation, string-to-integer conversion without floats.
... [lean-ctx: omitted 2 lines]
  - Tests: amount normalization tests · Evidence: — · Decisions: —
... [lean-ctx: omitted 7 lines]
  - Status: NOT STARTED · Reqs: FR-04, AMB-03
... [lean-ctx: omitted 5 lines]
  - Status: NOT STARTED · Reqs: FR-04, AMB-05
  - Learn: turning alternating segments into an associative array.
  - Build: the mentee implements reference and metadata parsing.
... [lean-ctx: omitted 3 lines]
  - Status: NOT STARTED · Reqs: FR-04, SC-02
  - Learn: designing negative tests; domain exceptions.
... [lean-ctx: omitted 1 lines]
  - Done when: invalid date, amount, missing reference, odd metadata, and empty line are rejected (observed).
  - Tests: PayTech malformed tests · Evidence: — · Decisions: —
... [lean-ctx: omitted 8 lines]
  - Learn: delimiter-based parsing with `//`.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 043 — Splitting a Multi-Line Body**
... [lean-ctx: omitted 1 lines]
  - Learn: `\n` vs `\r\n`, blank and trailing lines.
  - Build: the mentee implements and tests line splitting.
  - Done when: an N-line body yields N parsed transactions (observed).
  - Tests: multi-line tests · Evidence: — · Decisions: —
... [lean-ctx: omitted 1 lines]
  - Status: NOT STARTED · Reqs: FR-03, AMB-02
  - Learn: backed enums, mapping a bank to a parser, container resolution.
... [lean-ctx: omitted 1 lines]
  - Done when: each bank resolves to its parser and an unknown bank is impossible (observed).
  - Tests: resolver tests · Evidence: — · Decisions: —
... [lean-ctx: omitted 1 lines]
  - Status: NOT STARTED · Reqs: FR-02–FR-05
  - Learn: likely reviewer questions on parsing, with model reasoning.
... [lean-ctx: omitted 3 lines]
### Milestone 6 — Webhook Reception (046–054)
- [ ] **Lesson 046 — HTTP and Webhook Fundamentals**
... [lean-ctx: omitted 3 lines]
  - Done when: lesson delivered (including why 202 Accepted fits asynchronous processing).
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-01, AMB-01, AMB-02
  - Learn: `install:api`, route parameters, enum route binding, CSRF exclusion for APIs.
... [lean-ctx: omitted 1 lines]
  - Done when: `php artisan route:list` shows the route (observed).
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-01, DI-02, TS-01
... [lean-ctx: omitted 6 lines]
  - Learn: thin controllers, reading the raw body, persist-then-acknowledge.
... [lean-ctx: omitted 5 lines]
  - Learn: validation at the trust boundary; 404 vs 422.
... [lean-ctx: omitted 2 lines]
  - Tests: reception edge-case tests · Evidence: — · Decisions: —
- [ ] **Lesson 051 — Payload Size Limits and Resource Exhaustion**
... [lean-ctx: omitted 3 lines]
  - Done when: an oversized payload is rejected (observed).
  - Tests: size-limit test · Evidence: — · Decisions: —
- [ ] **Lesson 052 — Webhook Authentication: Options and Documented Limitation**
... [lean-ctx: omitted 1 lines]
  - Learn: shared secrets, HMAC signatures, IP allow-lists, mTLS; why we must not invent the bank's protocol.
  - Build: implement the recommended minimal option or document the limitation, per the lesson's decision.
  - Done when: recommendation delivered and recorded; tests pass if implemented (observed).
... [lean-ctx: omitted 3 lines]
  - Learn: `.env`, `config()`, `.env.example`, config caching pitfalls.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 054 — Safe Error Responses and Logging Without Sensitive Data**
... [lean-ctx: omitted 1 lines]
  - Learn: exception handling in `bootstrap/app.php`, `APP_DEBUG`, log redaction.
... [lean-ctx: omitted 1 lines]
  - Done when: errors expose no internals; logs exclude raw financial payloads where unnecessary.
... [lean-ctx: omitted 1 lines]
### Milestone 7 — Asynchronous Processing and Idempotency (055–070)
- [ ] **Lesson 055 — Queues, Jobs, and Workers Fundamentals**
... [lean-ctx: omitted 1 lines]
  - Learn: jobs, connections, queues, workers, `jobs` and `failed_jobs` tables.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 056 — Decision: Synchronous vs Asynchronous Processing and the Queue Driver**
... [lean-ctx: omitted 1 lines]
  - Learn: database vs Redis queues; operational trade-offs.
  - Build: record the decision and configure the queue connection.
  - Done when: recommendation delivered and recorded under Decisions.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 057 — Creating the Processing Job and Dispatching After Commit**
... [lean-ctx: omitted 1 lines]
  - Learn: `make:job`, serializing models, `afterCommit`.
... [lean-ctx: omitted 5 lines]
  - Learn: `Queue::fake()`, `assertPushed`.
... [lean-ctx: omitted 2 lines]
  - Tests: dispatch test · Evidence: — · Decisions: —
... [lean-ctx: omitted 2 lines]
  - Learn: separation of concerns between the job, the parser, and persistence.
... [lean-ctx: omitted 1 lines]
  - Done when: a processed webhook creates transactions for the right client (observed in a test).
... [lean-ctx: omitted 3 lines]
  - Learn: `firstOrCreate` vs `insertOrIgnore` vs `upsert`; check-then-insert races.
... [lean-ctx: omitted 1 lines]
  - Done when: recommendation delivered and recorded under Decisions.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 061 — Implement the Idempotent Import**
... [lean-ctx: omitted 11 lines]
- [ ] **Lesson 063 — Database Transactions and Atomicity Boundaries**
... [lean-ctx: omitted 1 lines]
  - Learn: `DB::transaction`, rollback, what must be atomic and what must not.
... [lean-ctx: omitted 1 lines]
  - Done when: recommendation delivered; boundary tested (observed).
  - Tests: atomicity test · Evidence: — · Decisions: —
- [ ] **Lesson 064 — Webhook Processing Status Lifecycle**
... [lean-ctx: omitted 1 lines]
  - Learn: pending, processing, processed, and failed states.
  - Build: the mentee implements the status transitions.
  - Done when: tests assert each transition (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 065 — Concurrency and Race Conditions**
... [lean-ctx: omitted 5 lines]
- [ ] **Lesson 066 — Concurrency Verification Strategy**
... [lean-ctx: omitted 1 lines]
  - Learn: what can and cannot be proven in PHPUnit; simulating concurrent duplicates.
... [lean-ctx: omitted 1 lines]
  - Done when: the test passes and its limitations are documented (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 067 — Partial Failures: Recording Invalid Lines**
... [lean-ctx: omitted 4 lines]
  - Tests: partial-failure test · Evidence: — · Decisions: —
... [lean-ctx: omitted 2 lines]
  - Learn: `#[Tries]`, `#[Backoff]`, `failed()`, `queue:retry`; retry safety through idempotency.
... [lean-ctx: omitted 1 lines]
  - Done when: a failing job is retried and then lands in `failed_jobs` (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 069 — Observability: Logs and Diagnostics**
... [lean-ctx: omitted 5 lines]
- [ ] **Lesson 070 — Interview Knowledge: Processing and Idempotency**
  - Status: NOT STARTED · Reqs: DI-01, FR-06, FR-07
  - Learn: likely reviewer questions on the processing pipeline, with model reasoning.
... [lean-ctx: omitted 3 lines]
### Milestone 8 — Pausing and Resuming Ingestion (071–075)
- [ ] **Lesson 071 — How `queue:pause` Works in Laravel 13**
... [lean-ctx: omitted 1 lines]
  - Learn: pause signals through the cache; worker behavior; `queue:continue`.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 072 — Test: Webhooks Are Accepted While Processing Is Paused**
... [lean-ctx: omitted 3 lines]
  - Done when: webhooks are stored as pending with no transactions created (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 073 — Resuming and Recovering Pending Webhooks**
... [lean-ctx: omitted 1 lines]
  - Learn: recovering webhooks whose job was lost; safe re-dispatch.
  - Build: implement the agreed recovery mechanism.
  - Done when: a resumed or recovered webhook is processed exactly once (observed).
... [lean-ctx: omitted 3 lines]
  - Learn: running `queue:work`, pausing, sending webhooks, resuming.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 075 — Interview Knowledge: Durability**
... [lean-ctx: omitted 1 lines]
  - Learn: likely reviewer questions on the no-data-loss guarantee and its limits, with model reasoning.
... [lean-ctx: omitted 3 lines]
### Milestone 9 — Performance (076–080)
- [ ] **Lesson 076 — Performance Fundamentals: Queries, Bulk Inserts, Memory**
... [lean-ctx: omitted 3 lines]
  - Done when: lesson delivered with a worked query-count estimate.
... [lean-ctx: omitted 3 lines]
  - Learn: chunked `insertOrIgnore`/`upsert`, preserving idempotency.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 078 — Designing the 1,000-Transaction Test**
... [lean-ctx: omitted 1 lines]
  - Learn: methodology, environment, deterministic data generation, no invented thresholds.
... [lean-ctx: omitted 1 lines]
  - Done when: methodology delivered and recorded.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 079 — Implementing the 1,000-Transaction Test**
... [lean-ctx: omitted 1 lines]
  - Learn: generating payloads; asserting correctness and query count.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 080 — Measuring, Bottleneck Analysis, and Documenting Results**
... [lean-ctx: omitted 1 lines]
  - Learn: timing, query logs, interpreting results honestly.
... [lean-ctx: omitted 1 lines]
  - Done when: results include environment and limitations.
... [lean-ctx: omitted 1 lines]
### Milestone 10 — XML Generation (081–092)
- [ ] **Lesson 081 — XML Fundamentals**
... [lean-ctx: omitted 1 lines]
  - Learn: declaration, elements, nesting, encoding, well-formedness.
... [lean-ctx: omitted 1 lines]
  - Done when: lesson delivered (structure of the PDF sample explained).
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-08, SC-03
  - Learn: `XMLWriter` vs `DOMDocument` vs `SimpleXML` vs string concatenation.
... [lean-ctx: omitted 1 lines]
  - Done when: recommendation delivered and recorded under Decisions.
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: FR-08, AMB-10
  - Learn: modeling the input with defaults (PaymentType 99, ChargeDetails SHA).
... [lean-ctx: omitted 9 lines]
- [ ] **Lesson 085 — TransferInfo: Reference, Date, Amount, and Currency**
  - Status: NOT STARTED · Reqs: FR-08, AMB-09
... [lean-ctx: omitted 1 lines]
  - Build: the mentee implements TransferInfo.
  - Done when: the TransferInfo assertions pass (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 086 — SenderInfo and ReceiverInfo**
... [lean-ctx: omitted 2 lines]
  - Build: the mentee implements both sections.
... [lean-ctx: omitted 4 lines]
  - Learn: conditional elements.
... [lean-ctx: omitted 1 lines]
  - Done when: with-notes and without-notes tests pass (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 088 — Conditional PaymentType**
... [lean-ctx: omitted 1 lines]
  - Learn: default-value omission.
... [lean-ctx: omitted 1 lines]
  - Done when: the 99 and non-99 tests pass (observed).
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 089 — Conditional ChargeDetails**
... [lean-ctx: omitted 5 lines]
- [ ] **Lesson 090 — Escaping and Special Characters**
... [lean-ctx: omitted 1 lines]
  - Learn: `&`, `<`, `>`, quotes, UTF-8 names; XML injection.
... [lean-ctx: omitted 2 lines]
  - Tests: escaping tests · Evidence: — · Decisions: —
- [ ] **Lesson 091 — Structural Assertions with DOM and XPath**
  - Status: NOT STARTED · Reqs: FR-08–FR-11, TS-01
  - Learn: asserting structure instead of brittle string equality.
... [lean-ctx: omitted 5 lines]
  - Learn: likely reviewer questions on XML, with model reasoning.
... [lean-ctx: omitted 3 lines]
### Milestone 11 — Documentation (093–097)
- [ ] **Lesson 093 — README: Purpose, Stack, Setup, and Running**
... [lean-ctx: omitted 1 lines]
  - Learn: writing reproducible setup instructions.
... [lean-ctx: omitted 1 lines]
  - Done when: reviewed; the commands are verified.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 094 — README: Webhook Formats and XML Behavior**
... [lean-ctx: omitted 1 lines]
  - Learn: documenting external contracts.
... [lean-ctx: omitted 1 lines]
  - Done when: reviewed against the implementation.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 095 — README: Design Decisions and Trade-offs**
... [lean-ctx: omitted 3 lines]
  - Done when: reviewed; no inflated claims.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 096 — README: Assumptions and Known Limitations**
  - Status: NOT STARTED · Reqs: DC-01, AMB-01–AMB-11, SC-01
  - Learn: honest disclosure.
... [lean-ctx: omitted 3 lines]
- [ ] **Lesson 097 — Reviewer Comments Where Beneficial**
... [lean-ctx: omitted 5 lines]
### Milestone 12 — Final Verification and Interview (098–106)
- [ ] **Lesson 098 — Clean-Code Sweep: Pint, `dd()`/`dump()`, Commented-Out Code**
... [lean-ctx: omitted 11 lines]
- [ ] **Lesson 100 — Fresh-Clone Setup Reproducibility**
... [lean-ctx: omitted 2 lines]
  - Build: clone into a temporary directory and follow the README.
  - Done when: the app installs, migrates, and passes tests from a clean clone (observed).
... [lean-ctx: omitted 5 lines]
  - Done when: the init commit is pristine; commits are coherent; no secrets or `plan.md`.
... [lean-ctx: omitted 3 lines]
  - Learn: evidence-based auditing (PASS / FAIL / NOT VERIFIED).
... [lean-ctx: omitted 1 lines]
  - Done when: every mandatory requirement has PASS with evidence.
... [lean-ctx: omitted 2 lines]
  - Status: NOT STARTED · Reqs: SC-01–SC-04, DI-01, DI-02
... [lean-ctx: omitted 2 lines]
  - Done when: findings are resolved or documented.
... [lean-ctx: omitted 1 lines]
- [ ] **Lesson 104 — Interview Preparation: Receiving Money**
  - Status: NOT STARTED · Reqs: FR-01–FR-07, DI-01, DI-02, PF-01
  - Learn: likely reviewer questions on receiving money, with model answers.
  - Build: — (mentor-written question bank with model answers; practice is optional)
... [lean-ctx: omitted 2 lines]
- [ ] **Lesson 105 — Interview Preparation: Sending Money, Testing, and Trade-offs**
  - Status: NOT STARTED · Reqs: FR-08–FR-11, TS-01
  - Learn: likely reviewer questions on XML, testing, and trade-offs, with model answers.
  - Build: — (mentor-written question bank with model answers; practice is optional)
... [lean-ctx: omitted 4 lines]
  - Learn: prioritizing future improvements honestly.
  - Build: — (mentor provides a prioritized list; optionally added to the README)
... [lean-ctx: omitted 2 lines]
## 8. Requirement → Lesson Coverage Map
| Req | Lessons |
... [lean-ctx: omitted 2 lines]
| FR-02 | 002, 043 |
| FR-03 | 002, 033, 044 |
... [lean-ctx: omitted 5 lines]
| FR-09 | 005, 087 |
| FR-10 | 005, 088 |
... [lean-ctx: omitted 6 lines]
| DC-02 | 097 |
... [lean-ctx: omitted 1 lines]
| SB-02 | 014, 101 |
| SB-03 | 015, 098 |
| SB-04 | 098 |
... [lean-ctx: omitted 1 lines]
| SC-02 | 040, 050–051 |
| SC-03 | 082, 090 |
... [lean-ctx: omitted 1 lines]
## 9. Progress Tracker (current position)
Canonical live tracker: [`progress.md`](progress.md). Snapshot below must stay aligned after each lesson.
... [lean-ctx: omitted 1 lines]
- Current lesson: 001 — Transaction Identity and Duplicate Acceptance Criteria (NOT STARTED)
... [lean-ctx: omitted 4 lines]
- Outstanding issues: README must document every ASSUMPTION (AMB-01–AMB-11)
- Verified facts: Laravel 13 supports PHP 8.3–8.5 (target runtime **8.5**); Laravel 13 has `queue:pause` / `queue:continue` (official 13.x docs)
... [lean-ctx: omitted 2 lines]

