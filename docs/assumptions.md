# Assumptions

Missing business details from the challenge brief. Each is labeled **ASSUMPTION** and must appear in the final README.

Type: **TECH** = mentor recommends · **BIZ** = missing business rule.

| ID | Question | Type | Recommendation | Why | Rejected alternatives |
| --- | --- | --- | --- | --- | --- |
| AMB-01 | How is the client identified? Bodies have no client field. | BIZ | Client comes from the request: webhook URL is client-specific (`{client}` route param) resolved to an existing client. | Body cannot identify the client; route param is explicit and testable. | Parsing `internal_reference` (Acme has no metadata); custom header; single hard-coded client. |
| AMB-02 | How do we know which bank sent the webhook? | TECH | One route segment `{bank}` constrained to known banks → parser map. Unknown bank → 404. | Explicit beats guessing; each bank configures its own URL. | Content sniffing (fragile); custom header (hides the contract). |
| AMB-03 | PayTech `20250615156,50` — date and amount have no separator. | BIZ | Date = first 8 chars `YYYYMMDD`; amount = rest before first `#`. Validate as a real calendar date. | Sample reference also starts with `20250615`; fixed width is unambiguous. | Regex guessing without fixed width. |
| AMB-04 | What makes a transaction unique? | TECH + BIZ | Identity = `(bank, reference)`; composite unique index. | Same reference appears in both bank samples; reference alone collides across banks. DB constraint is race-safe. | Reference alone; hash of whole line; include client in the key. |
| AMB-05 | Can metadata values contain `/`? Zero key/value pairs? | BIZ | Keys/values never contain `/` or `#`; alternating segments; zero pairs valid; odd count malformed. Spaces in values OK. | Only deterministic reading consistent with the sample. | Trailing free text (loses structure). |
| AMB-06 | Amount format and range. | BIZ + TECH | Digits, comma, exactly two decimals, no thousands separator, strictly positive. Never floats — integer minor units or `DECIMAL`. | Matches “two decimals”; binary floats cannot represent money exactly. | Loose formats (silent money corruption). |
| AMB-07 | Currency of incoming transactions. | BIZ | Single-currency wallet (SAR, consistent with XML sample). No currency column on incoming txs (YAGNI). | Formats carry no currency; storing one would invent data. | Constant currency column (implies information we lack). |
| AMB-08 | How to pause ingestion without data loss? | TECH | Stage 1: HTTP always stores raw body, returns 2xx. Stage 2: queued job parses/imports. Pause stops stage 2 only (`queue:pause` / `queue:continue`). | Receive ≠ record ≠ process. Framework pause avoids custom flags. | Sync processing; custom pause flag; queue-only without raw table. |
| AMB-09 | XML date `2025-02-25 06:33:00+03` is not strict ISO 8601. | TECH + BIZ | Match the sample (`Y-m-d H:i:s` + hour-only offset). | PDF shows expected output. | Strict ISO with `T` and `:00` minutes. |
| AMB-10 | Input for XML generation? | TECH | Plain PHP class: typed transfer-request object → XML string. Unit-tested. No HTTP, no persistence. | Brief: “only worry about generating the XML.” | HTTP endpoint or Artisan command (YAGNI). |
| AMB-11 | Malformed line inside a batch? | BIZ + TECH | Import valid lines; record invalid lines with reason; mark webhook partially failed. Keep raw body. | All-or-nothing withholds valid credits; silent drop loses diagnostics. Idempotency makes reprocess safe. | Reject whole batch; silent drop. |
