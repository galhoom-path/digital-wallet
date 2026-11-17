# Visual maps

Adapted from study-template **Visual Maps** standards — kept lean for a Practice build.

## Purpose

See the wallet as a system: receiving money, idempotency, pause/resume, XML send path.  
Maps live here so GitHub’s file view stays the acceptance check (not a local Mermaid plugin only).

## When to add or update a map

| Trigger | Map |
| --- | --- |
| After Milestone 1 (requirements) | `01-receive-vs-process.md` — receive → durable record → process |
| After Milestone 4 (data model) | `02-data-model.md` — clients / webhooks / transactions |
| After Milestone 7 (async + idempotency) | `03-ingestion-pipeline.md` — HTTP → queue → import → unique key |
| After Milestone 10 (XML) | `04-xml-generation.md` — transfer request → conditional elements |

Do not invent maps for decoration. One primary idea per file. Prefer `flowchart TB` or `sequenceDiagram`.

## Diagram standards (GitHub-clear)

- One fenced `mermaid` block per `map.md` / map file  
- About **4–12 nodes**; short plain labels  
- Pastel `classDef` + **dark text** (readable on GitHub light theme)  
- Never use `end` as a node id  
- No screenshots as the primary diagram  

## Ownership

- Mentor may seed a **starter** diagram when the milestone is reached.  
- Mentee updates the map when the design changes (CHECK: open the file on GitHub and confirm it reads cleanly).
