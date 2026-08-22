---
title: FAQ
description: Answers about Shred.one ports, Jito proxy modes, gRPC and UDP delivery.
order: 11
updated: 2026-08-16
---

# Shred.one FAQ

## Is the validator TVU port always 8000?

No. Discover the TVU port used by your validator instead of assuming a fixed value. The official Jito guide provides a discovery script and its examples commonly use `8001`, but your deployment can differ. See [Solana validator](solana-validator.md).

## Can I use the Jito proxy without a Jito key?

Yes, in `forward-only` mode. That mode does not request Jito shreds; it receives Shred.one UDP packets and forwards them to the configured local destinations. See [Jito ShredStream proxy](jito-shredstream.md).

## Is the hosted Jito ShredStream still a safe long-term dependency?

No. Jito announced a shutdown date of 05 Sep 2026. Check the [current official notice](https://docs.jito.wtf/lowlatencytxnfeed/) before using authenticated mode. Shred.one documentation keeps `forward-only` instructions because that behavior does not request the hosted Jito feed.

## Can I receive decoded transactions through gRPC?

Yes. Shred.one delivers raw Solana shreds over UDP, and you can run the Jito proxy locally with `--grpc-service-port` to reconstruct entries. Its `ShredstreamProxy.SubscribeEntries` RPC streams `Entry` protobuf messages containing a slot and serialized `Vec<Entry>` bytes; transactions are contained inside the decoded Solana entries. Early decoding does not mean a transaction is `confirmed` or `finalized`. See [Early transaction decoding](early-transaction-decoding.md).

## Why can I receive duplicate or out-of-order packets?

Shred.one is an additional best-effort UDP path. Redundant sources, network routing and retries at other layers can produce duplicates or reordering. Your receiver must validate, deduplicate and tolerate missing packets.

## Which port should I enter in Shred.one?

Enter the public UDP listener of your first receiving process: the actual validator TVU port, or the proxy `--src-bind-port`. Do not enter the local forwarding destination or gRPC TCP port of the proxy.

## Does Active prove packets reached my process?

No. Active means Shred.one applied the destination. Verify the provider firewall, host firewall, NAT, routing, packet capture and application counters separately.

## Can Shred.one guarantee a specific latency improvement?

No. Network path, region, host load and receiver implementation all affect arrival time. Benchmark Shred.one against your existing feed on the same host with synchronized clocks and a reproducible measurement method.
