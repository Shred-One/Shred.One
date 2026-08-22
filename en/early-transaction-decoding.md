---
title: Early transaction decoding
description: Decode Shred.one packets into Solana entries through the Jito proxy gRPC service.
order: 6
updated: 2026-08-16
---

# Decode transactions from Shred.one packets

The Jito ShredStream proxy can reconstruct entries from received shreds and publish them through a gRPC server. Shred.one still delivers raw UDP packets; the proxy provides the local decoding layer.

<div class="docs-path"><code>Shred.one</code><span>UDP -&gt;</span><code>proxy :20000</code><span>gRPC -&gt;</span><code>client :9999</code></div>

## 1. Start forward-only decoding

Build the proxy from its [official repository](https://github.com/jito-labs/shredstream-proxy), then run:

```bash
RUST_LOG=info ./target/release/jito-shredstream-proxy forward-only \
  --src-bind-addr 0.0.0.0 \
  --src-bind-port 20000 \
  --dest-ip-ports 127.0.0.1:8001 \
  --grpc-service-port 9999
```

The proxy currently requires at least one forwarding destination, so replace `127.0.0.1:8001` with a real local receiver. Set your Shred.one destination to public `IPv4:20000` on the proxy host.

## 2. Protect the gRPC port

The official proxy binds its gRPC server to all interfaces. Do not expose `9999/tcp` to the public Internet. Block it at the provider and host firewalls, or allow only a trusted private network. Keep the client on the same host when possible.

## 3. Subscribe to decoded entries

The official protobuf exposes `ShredstreamProxy.SubscribeEntries`. Each message contains a slot and serialized `Vec<Entry>` bytes. Start from the [official Jito Rust example](https://github.com/jito-labs/shredstream-proxy/blob/master/examples/deshred.rs), which connects to `http://127.0.0.1:9999`, subscribes and deserializes entries.

Transactions are contained inside those decoded Solana entries. Receiving an entry early only means the proxy reconstructed it from the shreds available to that proxy; it does not mean any contained transaction is `confirmed` or `finalized`. Use an appropriate Solana commitment source before treating transaction state as confirmed or final.

Your client must:

- handle reconnects and stream interruption;
- validate decoded transactions before acting on them;
- tolerate duplicates, missing shreds and out-of-order arrival;
- bound queues and memory under burst traffic; and
- record source and arrival timestamps for reproducible comparisons.

## What this mode does not provide

Shred.one does not operate or authenticate this gRPC endpoint. The proxy stream is not a Yellowstone Geyser API, does not expose the same filter model and is not a replay service. It publishes entries reconstructed from the shreds the proxy received.

## Official sources

Technical steps verified on 16 Aug 2026 against the [Jito decoding guide](https://docs.jito.wtf/lowlatencytxnfeed/#decoding-shreds), the [official `SubscribeEntries` protobuf](https://github.com/jito-labs/mev-protos/blob/master/shredstream.proto), the [official decoder example](https://github.com/jito-labs/shredstream-proxy/blob/master/examples/deshred.rs), and the [proxy command implementation](https://github.com/jito-labs/shredstream-proxy/blob/master/proxy/src/main.rs).
