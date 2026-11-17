# Map 01 — Receive vs process

Status: Starter (refine after Milestone 1 / Lesson 003)  
Related: DI-02, FR-01, AMB-08  
Kind: flowchart

## What to show

Bank webhook hits HTTP → raw body stored → 2xx means **recorded** → worker parses/imports later → pause stops workers only.

```mermaid
flowchart TB
  Bank([Bank webhook]) --> HTTP[HTTP endpoint]
  HTTP --> Store[Store raw body]
  Store --> Ack([2xx recorded])
  Store --> Queue[Queue job]
  Queue --> Worker{Worker running?}
  Worker -->|Yes| Import[Parse and import]
  Worker -->|Paused| Wait[Stay pending]
  Wait -->|Resume| Worker
  Import --> Tx[(Transactions)]

  classDef startEnd fill:#dbeafe,stroke:#1d4ed8,color:#1e3a8a,stroke-width:2px
  classDef process fill:#f0fdf4,stroke:#15803d,color:#14532d,stroke-width:2px
  classDef decision fill:#fef3c7,stroke:#d97706,color:#78350f,stroke-width:2px
  class Bank,Ack startEnd
  class HTTP,Store,Queue,Import,Wait,Tx process
  class Worker decision
```

## CHECK

Can you explain why pausing must not reject new webhooks?

## Source

- Challenge requirements: DI-02, FR-01  
- Laravel queues: https://laravel.com/docs/13.x/queues
