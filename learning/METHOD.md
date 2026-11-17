# Learning method (adapted from study-template)

Source judgment: [galhoom-path/study-template](https://github.com/galhoom-path/study-template) `template.md`.
This is a **Track 5 Practice build**, not a Study-track repo. We **do not** create `01-Lectures/` → `04-Final-Project/`. We absorb the teaching professionalism that improves this challenge.

## What we took

| Study-template idea | How it applies here |
| --- | --- |
| Learner writes every line | Mentor never writes `solution/` code (already locked) |
| 20/80 focus | Pareto lesson format (already locked) |
| Max 2 new concepts per unit | Enforce in each lesson’s High-Value section |
| Analogy before code | Short real-world analogy when a new concept appears |
| Plain-language first use | Define every new term in one line on first use |
| PLAN → DO → CHECK → ACT | Session cycle for every lesson |
| Explicit PLAN fields | Goal, concepts, prerequisites stated before teaching |
| Name the gap | ACT names the miss before any re-teach |
| Logic before syntax | Confirm the idea first; fix syntax separately |
| No progress without proof | Implementation lessons need evidence |
| Official sources only | Laravel / PHP docs — see Official Sources below |
| Living repo | Same repo tracks Laravel 13 / PHP 8.5; update in place |
| Visual maps (GitHub-clear Mermaid) | `learning/visual-maps/` at milestone boundaries |
| Milestone checks | Review checklist after each curriculum milestone with a pass bar |
| Interview depth | Existing interview lessons; strong-answer coverage rules |
| Skip-ahead | Allowed; list skipped dependencies in one sentence |
| File-labeled snippets | Every mentor code block states the target path |
| Full example unless partial | Show complete classes/methods unless labeled `partial example` |

## What we rejected (wrong fit)

- Four Study tracks / lecture folders as the repo spine
- Waiting on “do you understand?” / quiz gates (conflicts with autonomous mentoring)
- Emoji-heavy teaching chrome
- Flutter-only rules (`context.mounted`, `pubspec.yaml` Bloc pins)
- Re-teaching PHP fundamentals owned by [php-fundamentals](https://github.com/galhoom-path/php-fundamentals) / [php-oop](https://github.com/galhoom-path/php-oop)

## Session cycle (every lesson)

```text
PLAN  → read progress; state goal + 2–3 concepts + prerequisites; name lesson + requirement IDs
DO    → teach (analogy → concepts → decision → task); mentee writes/runs
CHECK → verification evidence (output, tests, or conceptual delivery)
ACT   → name the gap if needed; update progress.md; name next lesson — or re-teach once
```

### PLAN (before teaching)

State all three in a few short lines:

1. **Single goal** of this lesson (one sentence).
2. **Two to three concepts** the mentee will own by the end.
3. **Prerequisites** from earlier lessons (or “none — first of this theme”).

### ACT (after CHECK)

- Evidence met → confirm briefly; update `learning/progress.md`; name the next lesson.
- Partial → name exactly what is right; say: `The part that needs one more pass is...`; re-teach only that gap once; give a smaller task.
- Stuck → return to the analogy; shrink the task.
- **Logic before syntax:** if the approach is right but PHP/Laravel syntax is off, confirm the logic first, then correct the syntax separately.

## Lesson quality bar (on top of the 7-part Pareto format)

1. At most **two** new concepts in High-Value.
2. If a concept is new, open with a **short everyday analogy** (see Analogy bank below — not another API).
3. First use of a technical term → one-line plain definition (see Glossary).
4. Mentor examples in chat may be tiny and annotated; the mentee types anything that belongs in `solution/`.
5. Show the **simplest working shape first**, then add one layer if the lesson needs it.
6. Every mentor code block has a **path label** above it (e.g. `solution/app/Models/Client.php`).
7. Show a **full** class/method unless the snippet is explicitly labeled `partial example`.
8. Annotate every line of mentor-shown snippets (zero uncommented lines).
9. End with Verification + Key Takeaway + Common Mistake (already required).
10. Cite an official source when the lesson depends on framework behavior (Laravel docs deep link).
11. Stack pins: **Laravel 13** / **PHP 8.5**. When the project is first created, show the exact create command / `composer.json` constraints — never assume they are already present.

## Analogy bank (challenge domain)

Use these when the matching idea appears. Invent similar everyday ones for anything missing.

| Concept | Analogy |
| --- | --- |
| State / durable record | A bank passbook: the page you can read later is the record; a spoken balance is not. |
| Receive vs process | A receptionist stamps the mail and puts it in the inbox; the accountant processes it later. |
| Queue / job | A ticket printer: the request is accepted now; work happens when a clerk pulls the next ticket. |
| Idempotency | A stamped “already paid” receipt — handing the same bill twice must not charge twice. |
| Unique key / constraint | A locker number: two coats cannot claim the same locker. |
| Webhook | A doorbell with a written note: the visitor leaves a message; you decide when to act on it. |
| Pause / resume ingestion | A closed / open service window at a desk — mail still arrives, processing waits. |
| Ledger / transaction | A numbered receipt book: every move is a new line; you do not erase old lines. |
| XML export | A filled-out government form: only the fields that apply for this case are included. |

## Glossary (plain language on first use)

| Term | Plain meaning |
| --- | --- |
| Idempotent | Doing the same request again does not create a second effect. |
| Webhook | An HTTP callback your system receives when an external system has news. |
| Queue | A waiting line of work items processed later, one after another (or in workers). |
| Job | One unit of queued work (a class that performs the processing). |
| Migration | A versioned recipe that changes the database structure. |
| Eloquent model | A PHP class that maps to a database table and its rows. |
| Form Request | A Laravel class that validates and authorizes an incoming HTTP request. |
| Feature test | An automated test that hits HTTP routes and asserts responses / side effects. |
| Sealed set of outcomes | A locked list of result shapes the code must handle (no surprise fourth case). |

## Do not

- Write `solution/` files for the mentee
- Use “simply” / “just” to dismiss difficulty
- Invent brief requirements
- Dump a third concept into the same lesson
- Draw the mentee’s milestone maps for them (mentor may show a **starter** map; mentee owns updates)
- Skip naming the gap when CHECK fails
- Block the session on conversational quiz answers (proof is code, tests, or the milestone checklist)

## Official sources (this repo)

| Topic | Source |
| --- | --- |
| Laravel 13 releases / PHP range | https://laravel.com/docs/13.x/releases |
| Laravel docs (13.x) | https://laravel.com/docs/13.x |
| Queues / jobs | https://laravel.com/docs/13.x/queues |
| HTTP tests | https://laravel.com/docs/13.x/http-tests |
| PHP manual | https://www.php.net/manual/en/ |

Last verified: 2026-11-17 · Stack: Laravel 13 · PHP 8.5
