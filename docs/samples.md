# Samples from the challenge brief

Use these exact samples in tests. Do not invent alternate “realistic” formats that contradict the brief.

## PayTech (incoming webhook line)

```text
20250615156,50#202506159000001#internal_reference/RF123456-001/payment_method/bank_transfer/purpose/debt payment march
```

Field reading (AMB-03, AMB-05):

| Part | Value |
| --- | --- |
| Date | `20250615` (`YYYYMMDD`) |
| Amount | `156,50` |
| Reference | `202506159000001` |
| Metadata | `internal_reference` → `RF123456-001`, `payment_method` → `bank_transfer`, `purpose` → `debt payment march` |

Delimiter: `#`. Metadata: alternating key/value segments separated by `/`.

## Acme (incoming webhook line)

```text
156,50 // 202506159000001 // 20250615
```

| Part | Value |
| --- | --- |
| Amount | `156,50` |
| Reference | `202506159000001` |
| Date | `20250615` |

Delimiter: ` // ` (spaces around `//` as in the sample — confirm exact spacing when implementing against this string).

## Multi-line webhook body

One transaction per line. A single webhook may contain many lines (FR-02). Handle `\n` and `\r\n`, blank lines, and a trailing newline.

## Payment-request XML (outgoing)

Shape to match (conditional elements FR-09–FR-11):

```xml
<?xml version="1.0" encoding="utf-8"?>
<PaymentRequest>
  <TransferInfo>
    <Reference>...</Reference>
    <Date>2025-02-25 06:33:00+03</Date>
    <Amount>...</Amount>
    <Currency>SAR</Currency>
    <!-- Notes: omit when empty -->
    <!-- PaymentType: omit when 99 -->
    <!-- ChargeDetails: omit when SHA -->
  </TransferInfo>
  <SenderInfo>
    <!-- sender fields -->
  </SenderInfo>
  <ReceiverInfo>
    <!-- receiver fields -->
  </ReceiverInfo>
</PaymentRequest>
```

Exact element names and nesting are finalized against the brief sample in Lessons 005 and 081–089. Date format follows AMB-09 (match the sample, not strict ISO-8601 with `T`).

## Performance sample size

PF-01: design a deterministic 1,000-line webhook test (methodology in Lessons 078–080). Do not invent pass/fail latency thresholds the brief never stated.
