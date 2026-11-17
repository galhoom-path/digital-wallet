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
| No progress without proof | Implementation lessons need evidence |
| Official sources only | Laravel / PHP docs — see Official Sources below |
| Living repo | Same repo tracks Laravel 13 / PHP 8.5; update in place |
| Visual maps (GitHub-clear Mermaid) | `learning/visual-maps/` at milestone boundaries |
| Milestone checks | Review checklist after each curriculum milestone |
| Interview depth | Existing interview lessons; strong-answer coverage rules |
| Skip-ahead | Allowed; list skipped dependencies in one sentence |

## What we rejected (wrong fit)

- Four Study tracks / lecture folders as the repo spine  
- Waiting on “do you understand?” / quiz gates (conflicts with autonomous mentoring)  
- Emoji-heavy teaching chrome  
- Re-teaching PHP fundamentals owned by [php-fundamentals](https://github.com/galhoom-path/php-fundamentals) / [php-oop](https://github.com/galhoom-path/php-oop)

## Session cycle (every lesson)

```text
PLAN  → read progress; name lesson + requirement IDs
DO    → teach (analogy → concepts → decision → task); mentee writes/runs
CHECK → verification evidence (output, tests, or conceptual delivery)
ACT   → update progress.md; name next lesson — or re-teach the gap once
```

## Lesson quality bar (on top of the 7-part Pareto format)

1. At most **two** new concepts in High-Value.  
2. If a concept is new, open with a **short everyday analogy** (kitchen/mail/bank desk — not another API).  
3. First use of a technical term → one-line plain definition.  
4. Examples in chat may be tiny and annotated; the mentee types anything that belongs in `solution/`.  
5. End with Verification + Key Takeaway + Common Mistake (already required).  
6. Cite an official source when the lesson depends on framework behavior (Laravel docs deep link).

## Do not

- Write `solution/` files for the mentee  
- Use “simply” / “just” to dismiss difficulty  
- Invent brief requirements  
- Dump a third concept into the same lesson  
- Draw the mentee’s milestone maps for them (mentor may show a **starter** map; mentee owns updates)

## Official sources (this repo)

| Topic | Source |
| --- | --- |
| Laravel 13 releases / PHP range | https://laravel.com/docs/13.x/releases |
| Laravel docs (13.x) | https://laravel.com/docs/13.x |
| Queues / jobs | https://laravel.com/docs/13.x/queues |
| HTTP tests | https://laravel.com/docs/13.x/http-tests |
| PHP manual | https://www.php.net/manual/en/ |

Last verified: 2026-11-17 · Stack: Laravel 13 · PHP 8.5
