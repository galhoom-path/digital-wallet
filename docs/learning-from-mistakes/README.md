# Learning from mistakes

Short root-cause notes for surprises found while building. One file per lesson learned.

## When to add a note

After a bug whose root cause would save time next time (especially money, queues, idempotency, XML, tests).

## Template

```markdown
# <Short title>

**Date:** YYYY-MM-DD · **Area:** …

## Symptom
## Root cause
## Resolution
## Lesson
```

## Seeded (from prior practice — apply when relevant)

### Queue dispatch before commit

If you `dispatch()` a job that loads a row created in the same DB transaction, a sync/fast worker can run **before commit** and see nothing. Create inside the transaction; dispatch **after commit** (`afterCommit`).

### Unique index beats check-then-insert

Application-level “select then insert” races under concurrency. For DI-01, the composite unique index on `(bank, reference)` is the last line of defense.

### Webhook 2xx means durably recorded

Do not treat HTTP success as “fully processed.” Persist the raw body first; process asynchronously.
