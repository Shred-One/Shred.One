---
title: Shred.one use cases
description: Route Shred.one to a Solana validator, Jito proxy or local gRPC decoder.
order: 3
updated: 2026-08-16
---

# Shred.one use cases

Shred.one delivers raw Solana Data Shreds and Coding Shreds to one public IPv4 UDP destination. Choose the receiver that matches your workload.

| Goal | Shred.one destination | Continue with |
| --- | --- | --- |
| Give a Solana validator an additional shred path | The validator host and its actual TVU UDP port | [Solana validator](solana-validator.md) |
| Fan Shred.one packets out to a validator or another local receiver | Jito ShredStream proxy source port, commonly `20000/udp` | [Jito ShredStream proxy](jito-shredstream.md) |
| Decode entries and transactions before a full block is assembled | Jito ShredStream proxy source port with its gRPC service enabled | [Early transaction decoding](early-transaction-decoding.md) |

<div class="docs-path"><code>Shred.one</code><span>UDP -&gt;</span><code>public IPv4:port</code><span>-&gt;</span><code>your receiver</code></div>

## Measure on your infrastructure

Treat Shred.one as an additional best-effort UDP path. Measure first valid arrival on your own host, keep packet validation enabled and plan for duplicates, reordering and missing packets. Shred.one does not guarantee a fixed latency improvement for every validator, region or network path.

## Before you Subscribe

- Confirm the exact receiving port instead of assuming a default.
- Open only the required UDP path in both provider and host firewalls.
- Keep management and gRPC ports private.
- Validate packets in the receiving application.
- Start with one Shred.one 24-hour cycle and compare results against your existing feed.
