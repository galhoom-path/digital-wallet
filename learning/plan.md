# Digital Wallet Coding Challenge — Mentoring Plan

> Private mentoring curriculum and checkpoints.
> Live position: [`progress.md`](progress.md). Requirements: [`../docs/requirements.md`](../docs/requirements.md).
> This file lives outside `solution/` and is never part of the submitted repository.
> Language: **English only**.

## 000. Pareto Principle — High-Impact Microlearning Policy (latest; overrides lesson format and length rules below)

Every lesson teaches the ~20% of concepts that deliver ~80% of the practical value needed **now**. Optimize explanation
length, never correctness.

**Lesson format (exact):**

1. **What & Why** — what we are doing; why it matters for the challenge (requirement IDs).
2. **High-Value (20%)** — 1–3 essential concepts; unfamiliar terms defined; only knowledge needed now.
3. **Best Engineering Decision** — the recommendation, its primary reason, the main alternative and why it is weaker.
4. **Your Task** — ONE small actionable step; the mentee implements it.
5. **Verification** — how to confirm it works, concisely.
6. **Key Takeaway** — the single most important point.
7. **Common Mistake** — one mistake to avoid.

**Length:** target 100–180 words; maximum 200. Exceed it only when essential for correctness, security, or a genuinely
complex concept. Do not split one simple concept into several lessons just to satisfy the limit.

**Avoid:** long introductions, repetition, excess examples or analogies, extensive comparisons, large code blocks,
academic detail, unrelated edge cases, multiple tasks, quizzes, mandatory questions, conversational gates.

**Internal checklist per lesson:** what must be known to implement correctly · which decision matters most · what can be
postponed · the smallest useful step · the mistake most likely to break correctness.

**Never omitted for brevity:** financial data integrity, idempotency, database constraints, concurrency, webhook
durability, security, error handling, automated testing, explicit PDF requirements. These may take several micro-lessons.

**Checkpoints:** after each lesson, record its status, the key concept, and implementation status and verification
status *separately*, then name the next lesson. Implementation is never marked complete without verification.

## 00. Teaching Model Policy (overrides every conflicting instruction below; lesson format superseded by Section 000)

**Autonomous teaching, zero mandatory questions.** The mentor teaches proactively; the mentee is never interrogated.

The mentor must NOT:

- ask questions and wait for answers before continuing;
- require written criteria, explanations, or justifications in chat;
- run mandatory quizzes or "do you understand?" checks;
- block lesson completion on a conversational answer.

Responsibilities:

| Mentor | Mentee |
| --- | --- |
| Research, analyze requirements, explain concepts, recommend decisions, compare alternatives, explain trade-offs, give implementation instructions, review code, explain fixes, track progress | Write all application code, run commands, apply the techniques, test the application, own and understand the solution |

The mentor never implements the challenge.

Former lesson format (superseded by the 7-part Pareto format in Section 000; kept for reference):

1. **What We're Doing**
2. **Why We're Doing It** (requirement IDs)
3. **What You Need to Understand** (concepts and terms defined)
4. **Recommended Engineering Decision** (what, why, alternatives, why not, trade-offs)
5. **Implementation Instructions** (one very small task, written by the mentee)
6. **Verification** (expected behavior and testing guidance)
7. **Interview Knowledge** (the likely question *and* its correct reasoning, explained directly)
8. **Checkpoint** (status recorded here; learned / implemented / remaining)

Completion rules:

- **Conceptual lessons** are COMPLETED once the explanation is delivered.
- **Implementation lessons** are COMPLETED only with observed evidence (command output, passing tests, reviewed code).
- The mentee may move ahead before an implementation is verified. That lesson then stays `IN PROGRESS` / `NOT VERIFIED`.
  Progress is never falsified.

## 0. Engineering Decision-Making Policy (mandatory, overrides earlier instructions)

**Rule: Never assume the mentee already knows the correct answer.**
The mentor investigates, evaluates, recommends, justifies, and teaches. The mentee implements, tests, and owns the solution.

For every meaningful technical decision:

1. **Investigate** — PDF requirements, official Laravel 13 docs, established practice.
2. **Evaluate** — realistic approaches vs. correctness, simplicity, security, performance, scalability, maintainability.
3. **Recommend** — one explicit recommendation for this challenge.
4. **Justify** — why it wins, why alternatives lose, which trade-offs we accept.
5. **Teach** — explain every unfamiliar concept before asking the mentee to use it.
6. **Guide implementation** — one very small task; the mentee writes the code.
7. **Explain the interview reasoning** — the mentor states the likely reviewer question and its correct answer directly.

Decision explanation format (concise, proportionate to importance):
**Decision · Why · Alternatives · Why Not · Trade-offs · Implementation · Interview Knowledge**

Technical decisions vs. missing business requirements:

- Technical decisions: the mentor recommends.
- Missing business requirements: identify the ambiguity, list interpretations, recommend a minimal defensible
  assumption, label it **ASSUMPTION**, and ask for external clarification only when a documented assumption is unsafe.
- Never make the mentee choose between approaches they have not yet studied.

Applies to all existing and future lessons.

## 1. Environment Baseline

**Locked stack:** Laravel **13.x** on **PHP 8.5** — see [`../docs/stack.md`](../docs/stack.md) and [official releases](https://laravel.com/docs/13.x/releases).

Re-verify on the mentee's machine in Lessons 008–011. Do not trust stale host facts.

| Item | Expected / notes |
| --- | --- |
| PHP | **8.5.x** (confirm with `php -v`; Laravel 13 official range is 8.3–8.5) |
| Composer | Current 2.x |
| Laravel | **13.x only** via official create-project in Lesson 011 (`^13.0`) |
| Laravel 13 support | Released 2026-03-17; bug fixes until Q3 2027; security until 2028-03-17 |
| Git | Initialized inside `solution/` only (Lesson 013) |
| Mentoring layout | `docs/`, `learning/`, `AGENTS.md`, `.cursor/rules/` — not submitted |
| Challenge 100% | All **MANDATORY** (+ ENCOURAGED DC-01) IDs in [`../docs/requirements.md`](../docs/requirements.md) PASS — no invented extras |

**Machine preflight (2026-11-17):** PHP 8.5.12, Composer 2.11.2, Git 2.56, required extensions present, Composer diagnose OK with 7-Zip — see [`READY.md`](READY.md).

Still open until later lessons: database engine choice (Lesson 010), Git user identity if unset (Lesson 009).

## 2. Requirements Traceability Baseline

Status legend: `TODO` / `IN PROGRESS` / `DONE`. Verification: `NOT VERIFIED` / `PASS` / `FAIL`.

### Functional

| ID | Requirement | Source (PDF) | Area | Acceptance criteria | Tests | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| FR-01 | Receive bank notifications via webhook | p1 "Receiving Money" | HTTP layer | Endpoint accepts bank payloads | TBD | TODO | NOT VERIFIED |
| FR-02 | One webhook may contain multiple transactions (one per line) | p1 | Parsing | N lines -> N transactions | TBD | TODO | NOT VERIFIED |
| FR-03 | Body format is controlled by each bank | p1 | Parsing | Each bank parsed by its own rules | TBD | TODO | NOT VERIFIED |
| FR-04 | Parse PayTech format: Date, Amount, `#`, Reference, `#`, key/value pairs | p1 | Parsing | Sample line parsed into correct fields | TBD | TODO | NOT VERIFIED |
| FR-05 | Parse Acme format: Amount `//` Reference `//` Date | p1 | Parsing | Sample line parsed into correct fields | TBD | TODO | NOT VERIFIED |
| FR-06 | Import parsed transactions into the database | p1 | Persistence | Rows stored with correct values | TBD | TODO | NOT VERIFIED |
| FR-07 | Attach each transaction to a client | p1 | Persistence | Transaction has a client association | TBD | TODO | NOT VERIFIED |
| FR-08 | Build the payment-request XML from request details | p1-2 "Sending Money" | XML | Output matches prescribed structure | TBD | TODO | NOT VERIFIED |
| FR-09 | Omit `Notes` when there are no notes | p2 | XML | No `<Notes>` element when empty | TBD | TODO | NOT VERIFIED |
| FR-10 | Include `PaymentType` only when value != 99 | p2 | XML | Absent for 99, present otherwise | TBD | TODO | NOT VERIFIED |
| FR-11 | Include `ChargeDetails` only when value != SHA | p2 | XML | Absent for SHA, present otherwise | TBD | TODO | NOT VERIFIED |

### Data Integrity

| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DI-01 | Duplicate bank reports must not change the client's final transaction list | p1 | DB + processing | Same transaction reported 2+ times -> stored once | TBD | TODO | NOT VERIFIED |
| DI-02 | Ingestion can be stopped without dropping incoming webhooks | p1 | Ingestion | While paused, webhooks are durably kept and processed after resuming | TBD | TODO | NOT VERIFIED |

### Performance

| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| PF-01 | Consider efficiency and scaling; e.g. parse a 1,000-transaction webhook with acceptable performance | p3 | Parsing + persistence | Test with 1,000 lines; methodology documented | TBD | TODO | NOT VERIFIED |

### Testing

| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TS-01 | Solution covered with automated tests | p3 | `tests/` | Every FR/DI/PF item has a passing test | — | TODO | NOT VERIFIED |

### Documentation

| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| DC-01 | README documentation (heavily encouraged) incl. design decisions | p3 | `README.md` | Accurately describes the implemented system | — | TODO | NOT VERIFIED |
| DC-02 | Reviewer-oriented code comments where beneficial (optional) | p3 | Code | Comments explain non-obvious decisions only | — | TODO | NOT VERIFIED |

### Submission

| ID | Requirement | Source | Area | Acceptance criteria | Tests | Impl. | Verif. |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SB-01 | Separate commit containing framework init files | p3 | Git | First commit = pristine framework | — | TODO | NOT VERIFIED |
| SB-02 | Work organized in subsequent commits | p3 | Git | Logical, scoped commits | — | TODO | NOT VERIFIED |
| SB-03 | Clean code, standard styling, consistent indentation | p3 | Code | Pint passes | — | TODO | NOT VERIFIED |
| SB-04 | No commented-out code, no `dd()` / `dump()` | p3 | Code | Search finds none | — | TODO | NOT VERIFIED |

### Security (no explicit PDF requirement — reasonable engineering considerations)

| ID | Consideration | Status |
| --- | --- | --- |
| SC-01 | Webhook authentication (PDF defines no protocol; must not be invented — document as limitation/assumption) | TODO |
| SC-02 | Treat webhook body as untrusted input; validate and bound payload size | TODO |
| SC-03 | Safe XML generation (escaping special characters) | TODO |
| SC-04 | No secrets committed; sensitive data kept out of logs | TODO |

## 3. Open Questions — Classification and Recommendations

Type: **TECH** = technical decision (mentor recommends) · **BIZ** = missing business requirement (documented ASSUMPTION).
Each recommendation is re-examined in depth in the lesson where it becomes relevant.

| ID | Question | Type | Recommendation | Reasoning | Alternatives (rejected) | External clarification needed? |
| --- | --- | --- | --- | --- | --- | --- |
| AMB-01 | How is the client identified? Neither sample format contains a client/account field. | BIZ | ASSUMPTION: the client is identified by the request, not the body — the webhook URL registered with the bank is client-specific (route parameter), resolved to an existing client. | The body cannot identify a client, so the identifier must come from the request context. A route parameter is explicit, testable, and adds no fields to the bank's format. | Parse `internal_reference` from PayTech metadata (Acme has no metadata, so it fails for one bank); a custom header (works but hides the contract); a single hard-coded client (does not satisfy "attaching it to the client"). | Desirable but not blocking. Document the assumption in the README. |
| AMB-02 | How do we know which bank sent the webhook? | TECH | One route per bank, e.g. a `{bank}` route segment constrained to the known banks, mapped to a parser. | Explicit beats guessing. Each bank configures its own URL anyway. Unknown banks get a 404. | Detecting the format from content (fragile: Acme and PayTech lines could be confused, and an attacker could pick the parser); a header (less visible, no real benefit). | No. |
| AMB-03 | PayTech `20250615156,50` — date and amount have no separator. | BIZ | ASSUMPTION: the date is always the first 8 characters in `YYYYMMDD`; the amount is everything before the first `#` after those 8 characters. Validate as a real calendar date. | The sample's reference also starts with `20250615`, which supports a fixed 8-digit date. A fixed width is the only unambiguous way to split. | Regex guessing (cannot be unambiguous without the fixed-width rule). | No. Document it. |
| AMB-04 | What makes a transaction unique (duplicate detection)? | TECH + BIZ | ASSUMPTION: a reference is unique **per bank**. Identity = (bank, reference), enforced by a composite unique index in the database. | Both samples use the **same** reference `202506159000001` from different banks, so the reference alone is not safe globally. The database constraint is race-safe; application checks are not. | Reference alone (cross-bank collisions); hashing the whole line (a re-report with different metadata formatting would create a duplicate); including the client in the key (unnecessary, because a bank reference identifies one transaction). | No. |
| AMB-05 | Can metadata values contain `/`? Can a PayTech line have zero key/value pairs? | BIZ | ASSUMPTION: keys and values never contain `/` or `#`; segments alternate key/value; zero pairs is valid; an odd number of segments is malformed. Values may contain spaces (`debt payment march`). | This is the only interpretation consistent with the sample that can be parsed deterministically. | Treating the trailing part as free text (loses structure). | No. Document it. |
| AMB-06 | Amount format and range. | BIZ + TECH | ASSUMPTION: digits, a comma, exactly two decimals, no thousands separator, strictly positive (incoming money). TECH: never use floats; store exact values (integer minor units or `DECIMAL`), decided in the data-model lesson. | Matches the PDF ("two decimals"). Binary floats cannot represent most decimal fractions exactly. | Accepting loose formats (silent misparsing of money is worse than rejecting a line). | No. |
| AMB-07 | Currency of incoming transactions. | BIZ | ASSUMPTION: a single-currency wallet (SAR, consistent with the XML sample). No currency column for incoming transactions (YAGNI); listed as a known limitation. | Neither webhook format carries a currency, so storing one would be fabricated data. | Adding a currency column filled with a constant (implies information we do not have). | No. Document it. |
| AMB-08 | How is ingestion paused, and how is data loss prevented? | TECH | Two stages: (1) the HTTP endpoint **always** stores the raw webhook body durably in the database, then returns 2xx; (2) a queued job parses and imports it. Pausing stops stage 2 only, using Laravel 13's built-in `queue:pause` / `queue:continue` (verified in the official 13.x docs). Raw webhook rows keep a processing status so they can be audited and reprocessed. | Receiving, durably recording, and processing are separate. Pausing workers never touches reception, so nothing is dropped. Using a framework feature means no custom pause flag. | Synchronous processing (cannot be paused without rejecting webhooks); a custom pause flag in config or the database (reinvents a framework feature); relying only on the queue payload without a raw-webhook table (no audit trail, and a lost job loses the data). | No. |
| AMB-09 | XML date `2025-02-25 06:33:00+03` is not strict ISO 8601. | TECH + BIZ | Reproduce the sample format exactly (`Y-m-d H:i:s` plus an hour-only offset). ASSUMPTION: offsets with minutes (e.g. +05:30) are out of scope, or are rendered with minutes. Finalized in the XML lesson. | The PDF shows the expected output. Matching it is the safest reading. | ISO 8601 `2025-02-25T06:33:00+03:00` (deviates from the sample). | No. |
| AMB-10 | What is the input for XML generation? | TECH | A plain PHP class that takes a typed transfer-request object and returns an XML string, covered by unit tests. No HTTP endpoint and no persistence. | The PDF: "you need to only worry about generating the XML." An endpoint adds scope without value. | An HTTP endpoint or an Artisan command (out of scope, YAGNI). | No. |
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

Rules:

1. All application code, migrations, tests, configuration, and project documentation live in `solution/`.
2. Mentoring artifacts (`learning/`, `docs/`, `AGENTS.md`, Cursor rules) stay outside `solution/`.
3. Git is initialized inside `solution/` only. The first commit contains only the pristine Laravel 13 skeleton (SB-01).
4. Later commits are coherent, scoped, and use Conventional Commits (SB-02).
5. No AI prompts, mentoring notes, or checkpoints ever enter `solution/`.
6. Verify the working directory and target paths before creating or modifying any file.
7. The Laravel project inside `solution/` is created in Lesson 011, not earlier. A placeholder README may exist before that. The mentor never writes application code; the mentee does.
8. Language: English only for mentor replies and all workspace documents.

## 5. Session Resume Protocol

At the start of every session:

1. Read `learning/progress.md` and this file.
2. Inspect `solution/` (if it exists): files, `git log`, and test results when relevant.
3. Identify the last lesson whose completion is backed by evidence.
4. Compare the recorded progress with the actual project. If they disagree, explain the discrepancy and reconcile using verifiable evidence. A file existing is not proof that a lesson is complete.
5. Resume at the correct checkpoint. Never restart the curriculum unnecessarily.
6. Reply in English only.

## 6. Lesson Workflow and Checkpoint Rules

After every lesson:

1. Review the mentee's work, if the lesson has an implementation task.
2. Verify the completion criteria using evidence (conceptual lessons: explanation delivered).
3. Update the checkpoint (status, evidence, decisions).
4. Record the current position in Section 9.
5. Name the next lesson. The mentee continues whenever ready; there is no conversational gate.

Status values: `NOT STARTED` · `IN PROGRESS` · `BLOCKED` · `COMPLETED`.
Never mark a lesson complete without evidence. Never skip lessons silently. Missing prerequisites are inserted
with suffixed IDs (e.g. `Lesson 038a`) so that existing IDs and progress remain stable.

## 7. Lesson Roadmap — 106 lessons, 12 milestones

Fields per lesson: **Learn** = learning objective · **Build** = implementation objective · **Reqs** = requirement IDs ·
**Done when** = completion criteria · **Tests** · **Evidence** · **Decisions** = engineering decisions learned.

### Milestone 1 — Requirements and Acceptance Criteria (001–007)

- [ ] **Lesson 001 — Transaction Identity and Duplicate Acceptance Criteria**
  - Status: NOT STARTED · Reqs: DI-01, DI-02, AMB-04, AMB-08
  - Learn: acceptance criteria (Given/When/Then), transaction identity, natural keys, idempotency;
    receiving vs durably recording vs processing.
  - Build: — (mentor provides the criteria below when the lesson is delivered)
  - Done when: lesson delivered.
  - Criteria (become automated tests in Lesson 062):
    - AC-01 Given client C has no transactions, when the same PayTech line arrives in two separate webhooks for C,
      then C has exactly 1 transaction with that reference.
    - AC-02 Given client C has no transactions, when one webhook for C contains the same Acme line twice,
      then C has exactly 1 transaction with that reference.
    - AC-03 Given no transactions exist, when reference `202506159000001` arrives once from PayTech and once from Acme,
      then 2 transactions exist, one per bank.
  - Key concept: identity = (bank, reference) + unique index = idempotent, race-safe duplicate prevention.
  - Implementation: none required · Verification: N/A (criteria verified by tests in Lesson 062)
  - Tests: — (implemented in Lesson 062) · Evidence: — ·
    Decisions: identity = (bank, reference) [ASSUMPTION], enforced by a database unique index; a 2xx response means
    "durably recorded," not "processed"
- [ ] **Lesson 002 — Webhook Formats and Parsing Acceptance Criteria**
  - Status: NOT STARTED · Reqs: FR-02, FR-03, FR-04, FR-05, AMB-03, AMB-05, AMB-06
  - Learn: dissecting both sample lines field by field; fixed-width vs delimiter-based formats.
  - Build: — (mentor provides the criteria and expected field values for both samples)
  - Done when: lesson delivered; criteria recorded in this checkpoint.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 003 — Receiving vs Recording vs Processing**
  - Status: NOT STARTED · Reqs: FR-01, DI-02, AMB-08
  - Learn: durability, acknowledgment semantics, why a 2xx response must mean "durably recorded."
  - Build: — (mentor provides the pause/resume no-data-loss criteria)
  - Done when: lesson delivered; criteria (paused reception, resumed processing, crash) recorded in this checkpoint.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 004 — Client Association Acceptance Criteria**
  - Status: NOT STARTED · Reqs: FR-06, FR-07, AMB-01
  - Learn: why the body cannot identify the client; request-scoped identification.
  - Build: — (mentor provides the client-association criteria)
  - Done when: lesson delivered; criteria and ASSUMPTION AMB-01 recorded in this checkpoint.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 005 — XML Acceptance Criteria**
  - Status: NOT STARTED · Reqs: FR-08, FR-09, FR-10, FR-11, AMB-09
  - Learn: reading the sample XML as a specification; presence vs absence of elements.
  - Build: — (mentor provides the XML criteria)
  - Done when: lesson delivered; six criteria (Notes on/off, PaymentType 99/other, ChargeDetails SHA/other) recorded in this checkpoint.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 006 — Non-Functional, Security, and Submission Criteria**
  - Status: NOT STARTED · Reqs: PF-01, TS-01, SB-01–SB-04, SC-01–SC-04
  - Learn: the difference between explicit requirements and engineering considerations; not inventing numeric targets.
  - Build: — (mentor provides the performance and submission criteria)
  - Done when: lesson delivered; criteria recorded without fabricated performance thresholds.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 007 — Interview Knowledge: Requirements and Assumptions**
  - Status: NOT STARTED · Reqs: all, AMB-01–AMB-11
  - Learn: likely reviewer questions on requirements and assumptions, with model reasoning.
  - Build: — (mentor-written briefing; no quiz)
  - Done when: briefing delivered covering every ASSUMPTION.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 2 — Environment, Project Setup, and Git (008–015)

- [ ] **Lesson 008 — Workspace Layout and the `solution/` Directory**
  - Status: NOT STARTED · Reqs: SB-01
  - Learn: separating planning artifacts from the deliverable.
  - Build: explain the layout; no files created yet.
  - Done when: lesson delivered (why `plan.md` stays outside the repository).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 009 — Verifying PHP Extensions and Tooling**
  - Status: NOT STARTED · Reqs: —
  - Learn: `php -m`, required extensions (`dom`, `xmlwriter`, `pdo_*`, `mbstring`), Git configuration.
  - Build: run the checks and report the output.
  - Done when: all required extensions are confirmed present.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 010 — Database Engine Decision**
  - Status: NOT STARTED · Reqs: DI-01, PF-01
  - Learn: SQLite vs MySQL vs PostgreSQL for development, tests, and concurrency semantics.
  - Build: record the decision and configure nothing yet.
  - Done when: recommendation delivered and recorded, including the concurrency-testing trade-off.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 011 — Creating the Laravel 13 Project in `solution/`**
  - Status: NOT STARTED · Reqs: SB-01
  - Learn: `composer create-project`, version constraints, verifying the installed framework version.
  - Build: the mentee creates `solution/` with Laravel 13.
  - Done when: `php artisan --version` shows 13.x inside `solution/`.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 012 — Laravel 13 Directory Structure and Request Lifecycle**
  - Status: NOT STARTED · Reqs: —
  - Learn: `bootstrap/app.php`, routes, service container, providers, `.env`.
  - Build: — (guided tour)
  - Done when: lesson delivered (request path from `public/index.php` to a route).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 013 — Git Init, `.gitignore`, and the Framework-Initialization Commit**
  - Status: NOT STARTED · Reqs: SB-01
  - Learn: what belongs in the init commit; `.env` vs `.env.example`; `vendor/` exclusion.
  - Build: `git init` inside `solution/` and create the first commit.
  - Done when: `git log` shows one commit with the pristine skeleton only; no secrets tracked.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 014 — Conventional Commits and Commit Scoping**
  - Status: NOT STARTED · Reqs: SB-02
  - Learn: `feat`, `fix`, `test`, `refactor`, `docs`, `chore`; one logical change per commit.
  - Build: — (applied from now on)
  - Done when: lesson delivered with worked commit-message examples.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 015 — Running the Test Suite and the Pint Baseline**
  - Status: NOT STARTED · Reqs: TS-01, SB-03
  - Learn: `php artisan test`, PHPUnit configuration, Laravel Pint.
  - Build: run the default tests and Pint.
  - Done when: default tests pass and Pint reports no issues (observed output).
  - Tests: default example tests · Evidence: — · Decisions: —

### Milestone 3 — Domain Fundamentals (016–019)

- [ ] **Lesson 016 — Why Floating-Point Numbers Fail for Money**
  - Status: NOT STARTED · Reqs: AMB-06
  - Learn: IEEE 754 binary floating point; rounding errors.
  - Build: optional throwaway PHP experiment outside `solution/`.
  - Done when: lesson delivered (why `0.1 + 0.2` breaks money math).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 017 — Money Representation Decision**
  - Status: NOT STARTED · Reqs: AMB-06, FR-06
  - Learn: integer minor units vs `DECIMAL(p,s)`; conversions at the boundaries.
  - Build: record the decision.
  - Done when: recommendation delivered in the Decision format and recorded under Decisions.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 018 — Dates, Time Zones, and Immutable Dates in PHP**
  - Status: NOT STARTED · Reqs: AMB-03, AMB-09
  - Learn: `CarbonImmutable`, strict format parsing, invalid dates such as `20250231`.
  - Build: — (concept and small isolated experiment)
  - Done when: lesson delivered (strict vs lenient date parsing).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 019 — Data Transfer Objects and `readonly` Classes**
  - Status: NOT STARTED · Reqs: FR-04, FR-05
  - Learn: DTOs, immutability, typed properties, constructor promotion.
  - Build: — (design only; implemented in Lesson 034)
  - Done when: lesson delivered with the recommended fields and types.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 4 — Data Modeling (020–031)

- [ ] **Lesson 020 — Identifying Entities and Drawing the ERD**
  - Status: NOT STARTED · Reqs: FR-06, FR-07, DI-02
  - Learn: entities, relationships, cardinality.
  - Build: — (mentor provides the recommended ERD: clients, webhooks, transactions)
  - Done when: ERD delivered with every relationship justified.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 021 — Clients Table Design**
  - Status: NOT STARTED · Reqs: FR-07, AMB-01
  - Learn: minimal columns, public identifiers vs internal IDs.
  - Build: — (mentor provides the recommended columns and types; implemented in Lessons 025–027)
  - Done when: recommended design delivered and recorded.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 022 — Raw Webhook Table Design**
  - Status: NOT STARTED · Reqs: DI-02, AMB-08, AMB-11
  - Learn: storing raw payloads, status columns, timestamps for auditing.
  - Build: — (mentor provides the recommended columns and types; implemented in Lessons 025–027)
  - Done when: recommended design delivered and recorded.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 023 — Transactions Table Design**
  - Status: NOT STARTED · Reqs: FR-06, DI-01, AMB-04, AMB-05
  - Learn: storing amount, date, reference, bank, metadata (JSON column trade-offs).
  - Build: — (mentor provides the recommended columns and types; implemented in Lessons 025–027)
  - Done when: recommended design delivered and recorded.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 024 — Foreign Keys, Unique Constraints, and Indexes**
  - Status: NOT STARTED · Reqs: DI-01, PF-01
  - Learn: referential integrity, composite unique index on (bank, reference), index selection.
  - Build: — (mentor provides the recommended constraints and indexes)
  - Done when: each index is justified by a query or an integrity rule.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 025 — Migration: Clients**
  - Status: NOT STARTED · Reqs: FR-07
  - Learn: Laravel schema builder basics.
  - Build: the mentee writes the clients migration.
  - Done when: `php artisan migrate` succeeds (observed).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 026 — Migration: Webhooks**
  - Status: NOT STARTED · Reqs: DI-02
  - Learn: long text columns, enum-like status columns.
  - Build: the mentee writes the webhooks migration.
  - Done when: migration runs; schema reviewed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 027 — Migration: Transactions**
  - Status: NOT STARTED · Reqs: FR-06, DI-01
  - Learn: foreign keys and composite unique indexes in migrations.
  - Build: the mentee writes the transactions migration.
  - Done when: migration runs; unique index present.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 028 — Eloquent Models, Relationships, and Casts**
  - Status: NOT STARTED · Reqs: FR-06, FR-07
  - Learn: `belongsTo`, `hasMany`, attribute casts, mass-assignment protection.
  - Build: the mentee writes the three models.
  - Done when: models reviewed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 029 — Model Factories for Tests**
  - Status: NOT STARTED · Reqs: TS-01
  - Learn: factories, deterministic test data.
  - Build: the mentee writes factories.
  - Done when: factories create valid records in a test.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 030 — Database Test: the Unique Constraint Rejects Duplicates**
  - Status: NOT STARTED · Reqs: DI-01, TS-01
  - Learn: `RefreshDatabase`, asserting exceptions, testing constraints.
  - Build: the mentee writes the test.
  - Done when: the test passes (observed).
  - Tests: unique-constraint test · Evidence: — · Decisions: —
- [ ] **Lesson 031 — Interview Knowledge: Data Model**
  - Status: NOT STARTED · Reqs: FR-06, FR-07, DI-01, DI-02
  - Learn: likely reviewer questions on the schema, with model reasoning.
  - Build: — (mentor-written briefing; no quiz)
  - Done when: briefing delivered.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 5 — Parsing (032–045)

- [ ] **Lesson 032 — PHP String and Array Tools for Parsing**
  - Status: NOT STARTED · Reqs: FR-04, FR-05
  - Learn: `explode` with limits, `substr`, `preg_match`, `array_chunk`, strict comparisons.
  - Build: — (isolated examples unrelated to the challenge)
  - Done when: lesson delivered with worked examples.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 033 — Parser Design Decision: One Class per Bank**
  - Status: NOT STARTED · Reqs: FR-03
  - Learn: interfaces, the Strategy pattern, and when conditionals are enough.
  - Build: record the decision.
  - Done when: recommendation delivered in the Decision format and recorded under Decisions.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 034 — Implement the Parsed Transaction DTO**
  - Status: NOT STARTED · Reqs: FR-04, FR-05
  - Learn: applying Lesson 019.
  - Build: the mentee writes the DTO.
  - Done when: reviewed; types match the money and date decisions.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 035 — Amount Normalization: Test First**
  - Status: NOT STARTED · Reqs: AMB-06, TS-01
  - Learn: unit tests, data providers, valid and invalid cases.
  - Build: the mentee writes failing tests.
  - Done when: tests exist and fail for the right reason (observed).
  - Tests: amount normalization tests · Evidence: — · Decisions: —
- [ ] **Lesson 036 — Amount Normalization: Implementation**
  - Status: NOT STARTED · Reqs: AMB-06
  - Learn: strict validation, string-to-integer conversion without floats.
  - Build: the mentee implements it.
  - Done when: Lesson 035 tests pass (observed).
  - Tests: amount normalization tests · Evidence: — · Decisions: —
- [ ] **Lesson 037 — PayTech Parser: Sample-Line Test**
  - Status: NOT STARTED · Reqs: FR-04, TS-01
  - Learn: test-first with the exact PDF sample.
  - Build: the mentee writes the failing test.
  - Done when: the test fails for the right reason (observed).
  - Tests: PayTech sample test · Evidence: — · Decisions: —
- [ ] **Lesson 038 — PayTech Parser: Date and Amount Split**
  - Status: NOT STARTED · Reqs: FR-04, AMB-03
  - Learn: fixed-width parsing.
  - Build: the mentee implements the split.
  - Done when: date and amount assertions pass.
  - Tests: PayTech sample test · Evidence: — · Decisions: —
- [ ] **Lesson 039 — PayTech Parser: Reference and Metadata Pairs**
  - Status: NOT STARTED · Reqs: FR-04, AMB-05
  - Learn: turning alternating segments into an associative array.
  - Build: the mentee implements reference and metadata parsing.
  - Done when: the full sample test passes (observed).
  - Tests: PayTech sample test · Evidence: — · Decisions: —
- [ ] **Lesson 040 — PayTech Parser: Malformed Input Tests**
  - Status: NOT STARTED · Reqs: FR-04, SC-02
  - Learn: designing negative tests; domain exceptions.
  - Build: the mentee writes tests and handles the failures.
  - Done when: invalid date, amount, missing reference, odd metadata, and empty line are rejected (observed).
  - Tests: PayTech malformed tests · Evidence: — · Decisions: —
- [ ] **Lesson 041 — Acme Parser: Tests**
  - Status: NOT STARTED · Reqs: FR-05, TS-01
  - Learn: applying the same test pattern to a second format.
  - Build: the mentee writes the sample and malformed tests.
  - Done when: tests fail for the right reason (observed).
  - Tests: Acme parser tests · Evidence: — · Decisions: —
- [ ] **Lesson 042 — Acme Parser: Implementation**
  - Status: NOT STARTED · Reqs: FR-05
  - Learn: delimiter-based parsing with `//`.
  - Build: the mentee implements it.
  - Done when: Lesson 041 tests pass (observed).
  - Tests: Acme parser tests · Evidence: — · Decisions: —
- [ ] **Lesson 043 — Splitting a Multi-Line Body**
  - Status: NOT STARTED · Reqs: FR-02
  - Learn: `\n` vs `\r\n`, blank and trailing lines.
  - Build: the mentee implements and tests line splitting.
  - Done when: an N-line body yields N parsed transactions (observed).
  - Tests: multi-line tests · Evidence: — · Decisions: —
- [ ] **Lesson 044 — Resolving the Parser for a Bank**
  - Status: NOT STARTED · Reqs: FR-03, AMB-02
  - Learn: backed enums, mapping a bank to a parser, container resolution.
  - Build: the mentee implements the bank enum and the mapping.
  - Done when: each bank resolves to its parser and an unknown bank is impossible (observed).
  - Tests: resolver tests · Evidence: — · Decisions: —
- [ ] **Lesson 045 — Interview Knowledge: Parsing**
  - Status: NOT STARTED · Reqs: FR-02–FR-05
  - Learn: likely reviewer questions on parsing, with model reasoning.
  - Build: — (mentor-written briefing; no quiz)
  - Done when: briefing delivered.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 6 — Webhook Reception (046–054)

- [ ] **Lesson 046 — HTTP and Webhook Fundamentals**
  - Status: NOT STARTED · Reqs: FR-01
  - Learn: methods, status codes (200, 202, 4xx, 5xx), raw bodies, content types, sender retries.
  - Build: —
  - Done when: lesson delivered (including why 202 Accepted fits asynchronous processing).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 047 — API Routing in Laravel 13 and Route Design**
  - Status: NOT STARTED · Reqs: FR-01, AMB-01, AMB-02
  - Learn: `install:api`, route parameters, enum route binding, CSRF exclusion for APIs.
  - Build: the mentee defines the route.
  - Done when: `php artisan route:list` shows the route (observed).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 048 — Feature Test: the Webhook Is Accepted and Stored**
  - Status: NOT STARTED · Reqs: FR-01, DI-02, TS-01
  - Learn: Laravel HTTP tests, sending raw bodies, database assertions.
  - Build: the mentee writes the failing feature test.
  - Done when: the test fails for the right reason (observed).
  - Tests: webhook reception test · Evidence: — · Decisions: —
- [ ] **Lesson 049 — Controller: Durably Storing the Raw Webhook**
  - Status: NOT STARTED · Reqs: FR-01, DI-02
  - Learn: thin controllers, reading the raw body, persist-then-acknowledge.
  - Build: the mentee implements the controller.
  - Done when: Lesson 048 test passes (observed).
  - Tests: webhook reception test · Evidence: — · Decisions: —
- [ ] **Lesson 050 — Unknown Bank, Unknown Client, and Empty Body**
  - Status: NOT STARTED · Reqs: SC-02, FR-07
  - Learn: validation at the trust boundary; 404 vs 422.
  - Build: the mentee writes tests and handling.
  - Done when: each case returns the expected status and stores nothing (observed).
  - Tests: reception edge-case tests · Evidence: — · Decisions: —
- [ ] **Lesson 051 — Payload Size Limits and Resource Exhaustion**
  - Status: NOT STARTED · Reqs: SC-02, PF-01
  - Learn: denial of service, server and application limits.
  - Build: the mentee adds a size limit with a test.
  - Done when: an oversized payload is rejected (observed).
  - Tests: size-limit test · Evidence: — · Decisions: —
- [ ] **Lesson 052 — Webhook Authentication: Options and Documented Limitation**
  - Status: NOT STARTED · Reqs: SC-01
  - Learn: shared secrets, HMAC signatures, IP allow-lists, mTLS; why we must not invent the bank's protocol.
  - Build: implement the recommended minimal option or document the limitation, per the lesson's decision.
  - Done when: recommendation delivered and recorded; tests pass if implemented (observed).
  - Tests: TBD · Evidence: — · Decisions: —
- [ ] **Lesson 053 — Secrets and Environment Configuration**
  - Status: NOT STARTED · Reqs: SC-04
  - Learn: `.env`, `config()`, `.env.example`, config caching pitfalls.
  - Build: move any secret into configuration.
  - Done when: no secret is tracked by Git (observed).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 054 — Safe Error Responses and Logging Without Sensitive Data**
  - Status: NOT STARTED · Reqs: SC-04
  - Learn: exception handling in `bootstrap/app.php`, `APP_DEBUG`, log redaction.
  - Build: review error paths.
  - Done when: errors expose no internals; logs exclude raw financial payloads where unnecessary.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 7 — Asynchronous Processing and Idempotency (055–070)

- [ ] **Lesson 055 — Queues, Jobs, and Workers Fundamentals**
  - Status: NOT STARTED · Reqs: DI-02
  - Learn: jobs, connections, queues, workers, `jobs` and `failed_jobs` tables.
  - Build: —
  - Done when: lesson delivered (life of a job).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 056 — Decision: Synchronous vs Asynchronous Processing and the Queue Driver**
  - Status: NOT STARTED · Reqs: DI-02, PF-01
  - Learn: database vs Redis queues; operational trade-offs.
  - Build: record the decision and configure the queue connection.
  - Done when: recommendation delivered and recorded under Decisions.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 057 — Creating the Processing Job and Dispatching After Commit**
  - Status: NOT STARTED · Reqs: DI-02
  - Learn: `make:job`, serializing models, `afterCommit`.
  - Build: the mentee creates and dispatches the job.
  - Done when: reviewed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 058 — Test: Storing a Webhook Dispatches the Job**
  - Status: NOT STARTED · Reqs: DI-02, TS-01
  - Learn: `Queue::fake()`, `assertPushed`.
  - Build: the mentee writes the test.
  - Done when: the test passes (observed).
  - Tests: dispatch test · Evidence: — · Decisions: —
- [ ] **Lesson 059 — Import Service: Parse and Attach to the Client**
  - Status: NOT STARTED · Reqs: FR-06, FR-07
  - Learn: separation of concerns between the job, the parser, and persistence.
  - Build: the mentee implements the import logic.
  - Done when: a processed webhook creates transactions for the right client (observed in a test).
  - Tests: import tests · Evidence: — · Decisions: —
- [ ] **Lesson 060 — Idempotent Writes Decision**
  - Status: NOT STARTED · Reqs: DI-01
  - Learn: `firstOrCreate` vs `insertOrIgnore` vs `upsert`; check-then-insert races.
  - Build: record the decision.
  - Done when: recommendation delivered and recorded under Decisions.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 061 — Implement the Idempotent Import**
  - Status: NOT STARTED · Reqs: DI-01
  - Learn: applying Lesson 060.
  - Build: the mentee implements it.
  - Done when: reviewed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 062 — Duplicate Tests: Across Webhooks, Within a Webhook, Across Banks**
  - Status: NOT STARTED · Reqs: DI-01, TS-01
  - Learn: turning Lesson 001's criteria into tests.
  - Build: the mentee writes three tests.
  - Done when: all three pass (observed).
  - Tests: duplicate tests · Evidence: — · Decisions: —
- [ ] **Lesson 063 — Database Transactions and Atomicity Boundaries**
  - Status: NOT STARTED · Reqs: DI-01, DI-02
  - Learn: `DB::transaction`, rollback, what must be atomic and what must not.
  - Build: apply the boundary.
  - Done when: recommendation delivered; boundary tested (observed).
  - Tests: atomicity test · Evidence: — · Decisions: —
- [ ] **Lesson 064 — Webhook Processing Status Lifecycle**
  - Status: NOT STARTED · Reqs: DI-02, AMB-11
  - Learn: pending, processing, processed, and failed states.
  - Build: the mentee implements the status transitions.
  - Done when: tests assert each transition (observed).
  - Tests: status tests · Evidence: — · Decisions: —
- [ ] **Lesson 065 — Concurrency and Race Conditions**
  - Status: NOT STARTED · Reqs: DI-01
  - Learn: two workers and the same reference; why the unique index is the last line of defense.
  - Build: —
  - Done when: lesson delivered (the race and its resolution).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 066 — Concurrency Verification Strategy**
  - Status: NOT STARTED · Reqs: DI-01, TS-01
  - Learn: what can and cannot be proven in PHPUnit; simulating concurrent duplicates.
  - Build: the mentee writes the agreed test.
  - Done when: the test passes and its limitations are documented (observed).
  - Tests: concurrency test · Evidence: — · Decisions: —
- [ ] **Lesson 067 — Partial Failures: Recording Invalid Lines**
  - Status: NOT STARTED · Reqs: AMB-11
  - Learn: partial success and diagnostics.
  - Build: the mentee implements recording of invalid lines.
  - Done when: a mixed webhook imports valid lines and records invalid ones (observed).
  - Tests: partial-failure test · Evidence: — · Decisions: —
- [ ] **Lesson 068 — Retries, Backoff, and Failed Jobs**
  - Status: NOT STARTED · Reqs: DI-02
  - Learn: `#[Tries]`, `#[Backoff]`, `failed()`, `queue:retry`; retry safety through idempotency.
  - Build: configure retries.
  - Done when: a failing job is retried and then lands in `failed_jobs` (observed).
  - Tests: retry test · Evidence: — · Decisions: —
- [ ] **Lesson 069 — Observability: Logs and Diagnostics**
  - Status: NOT STARTED · Reqs: SC-04
  - Learn: structured log context, what to log, what never to log.
  - Build: add minimal logging.
  - Done when: reviewed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 070 — Interview Knowledge: Processing and Idempotency**
  - Status: NOT STARTED · Reqs: DI-01, FR-06, FR-07
  - Learn: likely reviewer questions on the processing pipeline, with model reasoning.
  - Build: — (mentor-written briefing; no quiz)
  - Done when: briefing delivered.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 8 — Pausing and Resuming Ingestion (071–075)

- [ ] **Lesson 071 — How `queue:pause` Works in Laravel 13**
  - Status: NOT STARTED · Reqs: DI-02, AMB-08
  - Learn: pause signals through the cache; worker behavior; `queue:continue`.
  - Build: —
  - Done when: lesson delivered (what is and is not paused).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 072 — Test: Webhooks Are Accepted While Processing Is Paused**
  - Status: NOT STARTED · Reqs: DI-02, TS-01
  - Learn: testing durability independently of workers.
  - Build: the mentee writes the test.
  - Done when: webhooks are stored as pending with no transactions created (observed).
  - Tests: paused-ingestion test · Evidence: — · Decisions: —
- [ ] **Lesson 073 — Resuming and Recovering Pending Webhooks**
  - Status: NOT STARTED · Reqs: DI-02
  - Learn: recovering webhooks whose job was lost; safe re-dispatch.
  - Build: implement the agreed recovery mechanism.
  - Done when: a resumed or recovered webhook is processed exactly once (observed).
  - Tests: resume tests · Evidence: — · Decisions: —
- [ ] **Lesson 074 — End-to-End Manual Verification with a Real Worker**
  - Status: NOT STARTED · Reqs: DI-02, FR-01
  - Learn: running `queue:work`, pausing, sending webhooks, resuming.
  - Build: the mentee runs the scenario.
  - Done when: the observed results match Lesson 003's criteria.
  - Tests: manual scenario · Evidence: — · Decisions: —
- [ ] **Lesson 075 — Interview Knowledge: Durability**
  - Status: NOT STARTED · Reqs: DI-02
  - Learn: likely reviewer questions on the no-data-loss guarantee and its limits, with model reasoning.
  - Build: — (mentor-written briefing; no quiz)
  - Done when: briefing delivered.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 9 — Performance (076–080)

- [ ] **Lesson 076 — Performance Fundamentals: Queries, Bulk Inserts, Memory**
  - Status: NOT STARTED · Reqs: PF-01
  - Learn: per-row queries vs bulk inserts, N+1, memory growth.
  - Build: —
  - Done when: lesson delivered with a worked query-count estimate.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 077 — Bulk Import with Chunking**
  - Status: NOT STARTED · Reqs: PF-01, DI-01
  - Learn: chunked `insertOrIgnore`/`upsert`, preserving idempotency.
  - Build: the mentee refactors the import.
  - Done when: all existing tests still pass (observed).
  - Tests: full suite · Evidence: — · Decisions: —
- [ ] **Lesson 078 — Designing the 1,000-Transaction Test**
  - Status: NOT STARTED · Reqs: PF-01
  - Learn: methodology, environment, deterministic data generation, no invented thresholds.
  - Build: — (mentor provides the test methodology)
  - Done when: methodology delivered and recorded.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 079 — Implementing the 1,000-Transaction Test**
  - Status: NOT STARTED · Reqs: PF-01, TS-01
  - Learn: generating payloads; asserting correctness and query count.
  - Build: the mentee writes the test.
  - Done when: the test passes (observed).
  - Tests: 1,000-transaction test · Evidence: — · Decisions: —
- [ ] **Lesson 080 — Measuring, Bottleneck Analysis, and Documenting Results**
  - Status: NOT STARTED · Reqs: PF-01, DC-01
  - Learn: timing, query logs, interpreting results honestly.
  - Build: record the measurements for the README.
  - Done when: results include environment and limitations.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 10 — XML Generation (081–092)

- [ ] **Lesson 081 — XML Fundamentals**
  - Status: NOT STARTED · Reqs: FR-08
  - Learn: declaration, elements, nesting, encoding, well-formedness.
  - Build: —
  - Done when: lesson delivered (structure of the PDF sample explained).
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 082 — PHP XML API Decision**
  - Status: NOT STARTED · Reqs: FR-08, SC-03
  - Learn: `XMLWriter` vs `DOMDocument` vs `SimpleXML` vs string concatenation.
  - Build: record the decision.
  - Done when: recommendation delivered and recorded under Decisions.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 083 — Transfer Request Input Object**
  - Status: NOT STARTED · Reqs: FR-08, AMB-10
  - Learn: modeling the input with defaults (PaymentType 99, ChargeDetails SHA).
  - Build: the mentee writes the input object.
  - Done when: reviewed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 084 — Test First: the Sample XML**
  - Status: NOT STARTED · Reqs: FR-08, TS-01
  - Learn: comparing XML in tests.
  - Build: the mentee writes the failing test.
  - Done when: the test fails for the right reason (observed).
  - Tests: sample XML test · Evidence: — · Decisions: —
- [ ] **Lesson 085 — TransferInfo: Reference, Date, Amount, and Currency**
  - Status: NOT STARTED · Reqs: FR-08, AMB-09
  - Learn: date and amount formatting rules.
  - Build: the mentee implements TransferInfo.
  - Done when: the TransferInfo assertions pass (observed).
  - Tests: sample XML test · Evidence: — · Decisions: —
- [ ] **Lesson 086 — SenderInfo and ReceiverInfo**
  - Status: NOT STARTED · Reqs: FR-08
  - Learn: nested elements.
  - Build: the mentee implements both sections.
  - Done when: the sample XML test passes (observed).
  - Tests: sample XML test · Evidence: — · Decisions: —
- [ ] **Lesson 087 — Conditional Notes**
  - Status: NOT STARTED · Reqs: FR-09
  - Learn: conditional elements.
  - Build: the mentee writes tests and the implementation.
  - Done when: with-notes and without-notes tests pass (observed).
  - Tests: Notes tests · Evidence: — · Decisions: —
- [ ] **Lesson 088 — Conditional PaymentType**
  - Status: NOT STARTED · Reqs: FR-10
  - Learn: default-value omission.
  - Build: the mentee writes tests and the implementation.
  - Done when: the 99 and non-99 tests pass (observed).
  - Tests: PaymentType tests · Evidence: — · Decisions: —
- [ ] **Lesson 089 — Conditional ChargeDetails**
  - Status: NOT STARTED · Reqs: FR-11
  - Learn: same pattern, verified independently.
  - Build: the mentee writes tests and the implementation.
  - Done when: the SHA and non-SHA tests pass (observed).
  - Tests: ChargeDetails tests · Evidence: — · Decisions: —
- [ ] **Lesson 090 — Escaping and Special Characters**
  - Status: NOT STARTED · Reqs: SC-03
  - Learn: `&`, `<`, `>`, quotes, UTF-8 names; XML injection.
  - Build: the mentee writes escaping tests.
  - Done when: the output stays well-formed with hostile input (observed).
  - Tests: escaping tests · Evidence: — · Decisions: —
- [ ] **Lesson 091 — Structural Assertions with DOM and XPath**
  - Status: NOT STARTED · Reqs: FR-08–FR-11, TS-01
  - Learn: asserting structure instead of brittle string equality.
  - Build: the mentee refines the XML tests.
  - Done when: the tests assert element presence, absence, and values (observed).
  - Tests: XML suite · Evidence: — · Decisions: —
- [ ] **Lesson 092 — Interview Knowledge: XML**
  - Status: NOT STARTED · Reqs: FR-08–FR-11
  - Learn: likely reviewer questions on XML, with model reasoning.
  - Build: — (mentor-written briefing; no quiz)
  - Done when: briefing delivered.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 11 — Documentation (093–097)

- [ ] **Lesson 093 — README: Purpose, Stack, Setup, and Running**
  - Status: NOT STARTED · Reqs: DC-01
  - Learn: writing reproducible setup instructions.
  - Build: the mentee drafts the section.
  - Done when: reviewed; the commands are verified.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 094 — README: Webhook Formats and XML Behavior**
  - Status: NOT STARTED · Reqs: DC-01
  - Learn: documenting external contracts.
  - Build: the mentee drafts the section.
  - Done when: reviewed against the implementation.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 095 — README: Design Decisions and Trade-offs**
  - Status: NOT STARTED · Reqs: DC-01
  - Learn: concise decision records.
  - Build: the mentee drafts the section.
  - Done when: reviewed; no inflated claims.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 096 — README: Assumptions and Known Limitations**
  - Status: NOT STARTED · Reqs: DC-01, AMB-01–AMB-11, SC-01
  - Learn: honest disclosure.
  - Build: the mentee drafts the section.
  - Done when: every ASSUMPTION is listed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 097 — Reviewer Comments Where Beneficial**
  - Status: NOT STARTED · Reqs: DC-02
  - Learn: when a comment adds value and when it is noise.
  - Build: the mentee adds or removes comments.
  - Done when: reviewed.
  - Tests: — · Evidence: — · Decisions: —

### Milestone 12 — Final Verification and Interview (098–106)

- [ ] **Lesson 098 — Clean-Code Sweep: Pint, `dd()`/`dump()`, Commented-Out Code**
  - Status: NOT STARTED · Reqs: SB-03, SB-04
  - Learn: automated checks for submission hygiene.
  - Build: run Pint and the searches.
  - Done when: clean output is observed.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 099 — Full Test Run and Coverage Review**
  - Status: NOT STARTED · Reqs: TS-01
  - Learn: mapping tests to requirements; finding gaps.
  - Build: run the suite and close the gaps.
  - Done when: the whole suite passes (observed); every FR/DI/PF has a test.
  - Tests: full suite · Evidence: — · Decisions: —
- [ ] **Lesson 100 — Fresh-Clone Setup Reproducibility**
  - Status: NOT STARTED · Reqs: DC-01
  - Learn: verifying the README from scratch.
  - Build: clone into a temporary directory and follow the README.
  - Done when: the app installs, migrates, and passes tests from a clean clone (observed).
  - Tests: full suite · Evidence: — · Decisions: —
- [ ] **Lesson 101 — Git History Review**
  - Status: NOT STARTED · Reqs: SB-01, SB-02
  - Learn: reading history as a reviewer.
  - Build: inspect `git log`.
  - Done when: the init commit is pristine; commits are coherent; no secrets or `plan.md`.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 102 — Final Requirements Audit**
  - Status: NOT STARTED · Reqs: all
  - Learn: evidence-based auditing (PASS / FAIL / NOT VERIFIED).
  - Build: complete the traceability matrix in Section 2.
  - Done when: every mandatory requirement has PASS with evidence.
  - Tests: full suite · Evidence: — · Decisions: —
- [ ] **Lesson 103 — Security and Data-Integrity Audit**
  - Status: NOT STARTED · Reqs: SC-01–SC-04, DI-01, DI-02
  - Learn: threat review of the finished system.
  - Build: walk through each threat.
  - Done when: findings are resolved or documented.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 104 — Interview Preparation: Receiving Money**
  - Status: NOT STARTED · Reqs: FR-01–FR-07, DI-01, DI-02, PF-01
  - Learn: likely reviewer questions on receiving money, with model answers.
  - Build: — (mentor-written question bank with model answers; practice is optional)
  - Done when: question bank delivered.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 105 — Interview Preparation: Sending Money, Testing, and Trade-offs**
  - Status: NOT STARTED · Reqs: FR-08–FR-11, TS-01
  - Learn: likely reviewer questions on XML, testing, and trade-offs, with model answers.
  - Build: — (mentor-written question bank with model answers; practice is optional)
  - Done when: question bank delivered.
  - Tests: — · Evidence: — · Decisions: —
- [ ] **Lesson 106 — Retrospective: What I Would Improve With More Time**
  - Status: NOT STARTED · Reqs: DC-01
  - Learn: prioritizing future improvements honestly.
  - Build: — (mentor provides a prioritized list; optionally added to the README)
  - Done when: reviewed.
  - Tests: — · Evidence: — · Decisions: —

## 8. Requirement → Lesson Coverage Map

| Req | Lessons |
| --- | --- |
| FR-01 | 003, 046–049, 074 |
| FR-02 | 002, 043 |
| FR-03 | 002, 033, 044 |
| FR-04 | 002, 019, 034, 037–040 |
| FR-05 | 002, 019, 034, 041–042 |
| FR-06 | 004, 017, 020, 023, 027–028, 059 |
| FR-07 | 004, 020–021, 025, 028, 050, 059 |
| FR-08 | 005, 081–086, 091 |
| FR-09 | 005, 087 |
| FR-10 | 005, 088 |
| FR-11 | 005, 089 |
| DI-01 | 001, 024, 027, 030, 060–063, 065–066, 077 |
| DI-02 | 003, 022, 026, 048–049, 055–058, 064, 068, 071–075 |
| PF-01 | 006, 051, 076–080 |
| TS-01 | 015, 029–030, 035, 037, 041, 048, 058, 062, 066, 072, 079, 084, 091, 099 |
| DC-01 | 080, 093–096, 100, 106 |
| DC-02 | 097 |
| SB-01 | 008, 011, 013, 101 |
| SB-02 | 014, 101 |
| SB-03 | 015, 098 |
| SB-04 | 098 |
| SC-01 | 052, 096, 103 |
| SC-02 | 040, 050–051 |
| SC-03 | 082, 090 |
| SC-04 | 053–054, 069 |

## 9. Progress Tracker (current position)

Canonical live tracker: [`progress.md`](progress.md). Snapshot below must stay aligned after each lesson.

- Current milestone: 1 — Requirements and Acceptance Criteria
- Current lesson: 001 — Transaction Identity and Duplicate Acceptance Criteria (NOT STARTED)
- Last completed lesson: —
- Next lesson: 001 — Transaction Identity and Duplicate Acceptance Criteria
- `solution/` Laravel project: no (placeholder folder only; create in Lesson 011)
- Tests written: 0 · Tests passing: 0
- Outstanding issues: README must document every ASSUMPTION (AMB-01–AMB-11)
- Verified facts: Laravel 13 supports PHP 8.3–8.5 (target runtime **8.5**); Laravel 13 has `queue:pause` / `queue:continue` (official 13.x docs)
- Topics requiring revision: none yet
- Language: English only (mentor + all docs)
