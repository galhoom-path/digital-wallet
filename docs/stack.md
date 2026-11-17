# Stack — locked

Official source: [Laravel Release Notes](https://laravel.com/docs/13.x/releases) (also linked as https://laravel.com/framework/docs/releases).

## Decision

| Item | Value | Status |
| --- | --- | --- |
| Framework | **Laravel 13.x** (`^13.0`) | **LOCKED** |
| PHP | **8.5** (runtime target) | **LOCKED** |
| Laravel 13 official PHP range | 8.3 – 8.5 | Constraint from docs |
| Create command (Lesson 011) | `composer create-project laravel/laravel:^13.0 solution` (or equivalent official installer targeting 13.x) | Pending Lesson 011 |
| Git init commit | Pristine Laravel 13 skeleton only (SB-01) | Pending Lesson 013 |

## Support policy (Laravel 13)

| | |
| --- | --- |
| Released | 17 March 2026 |
| Bug fixes until | Q3 2027 |
| Security fixes until | 17 March 2028 |

## Rules

1. Develop and verify on **PHP 8.5** (`php -v` must show 8.5.x).
2. Do **not** scaffold Laravel 11/12 or any other major version.
3. Do **not** use PHP 8.6 for this challenge (not in Laravel 13’s official support table).
4. Do **not** invent stack requirements the challenge brief never stated (no mandatory Redis, Docker, Horizon, etc.) unless a lesson decision records them as optional tooling.
5. Verify installed framework with `php artisan --version` inside `solution/` after Lesson 011 — must report **13.x**.
6. Prefer framework-native features for queues/pause (`queue:pause` / `queue:continue` where documented for 13.x) over custom reinventions.
