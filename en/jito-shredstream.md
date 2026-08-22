---
title: Jito ShredStream proxy
description: Route Shred.one through authenticated or forward-only Jito ShredStream proxy modes.
order: 5
updated: 2026-08-16
---

# Route Shred.one through Jito ShredStream proxy

> Jito announced that its hosted ShredStream service will shut down on 05 Sep 2026. The `forward-only` proxy mode remains useful as an open-source UDP forwarder and decoder, but do not design a new long-term dependency on the hosted Jito feed. Check the current Jito notice before deployment.

The proxy can receive Shred.one on one UDP port and fan packets out to one or more local destinations. This keeps Shred.one configuration simple when a validator or decoder already uses the Jito proxy format.

<div class="docs-path"><code>Shred.one</code><span>UDP -&gt;</span><code>proxy :20000</code><span>-&gt;</span><code>validator TVU</code></div>

## Install from the official repository

Build only from the [official `jito-labs/shredstream-proxy` repository](https://github.com/jito-labs/shredstream-proxy). Review a release tag or commit and pin it before production use.

```bash
git clone https://github.com/jito-labs/shredstream-proxy.git --recurse-submodules
cd shredstream-proxy
git checkout <reviewed-tag-or-commit>
cargo build --release --bin jito-shredstream-proxy
```

The build requires the Rust toolchain and dependencies declared by that repository. Do not run an unreviewed third-party installer.

## No Jito key: forward-only mode

`forward-only` does not request shreds from Jito and does not need a Jito authentication keypair. It forwards packets received on `src-bind-addr:src-bind-port` to every `dest-ip-ports` target.

```bash
RUST_LOG=info ./target/release/jito-shredstream-proxy forward-only \
  --src-bind-addr 0.0.0.0 \
  --src-bind-port 20000 \
  --dest-ip-ports 127.0.0.1:8001
```

Replace `127.0.0.1:8001` with the real local receiver. For a validator, [discover its TVU port](/docs/solana-validator/) first.

Then set the Shred.one destination to:

```text
IPv4: the public IPv4 address of the proxy host
UDP port: 20000
```

Allow `20000/udp` through the required provider and host firewall path. The port is an example and matches the proxy default; you may choose another port and use the same value in Shred.one and `--src-bind-port`.

## Existing approved Jito key: authenticated mode

If Jito has already approved your key and the hosted service is still available, the official native command uses the `shredstream` subcommand:

```bash
RUST_LOG=info ./target/release/jito-shredstream-proxy shredstream \
  --block-engine-url https://mainnet.block-engine.jito.wtf \
  --auth-keypair /secure/path/jito-auth-keypair.json \
  --desired-regions amsterdam \
  --src-bind-port 20000 \
  --dest-ip-ports 127.0.0.1:8001
```

Keep the keypair outside the repository and logs. Point Shred.one to the same public `IPv4:20000` receiver so both paths enter the proxy before forwarding. Expect duplicates and keep downstream validation enabled.

## Verify

```bash
sudo tcpdump -ni any "udp and dst port 20000"
```

Check proxy logs for received, forwarded, failed and duplicate shred counters. Also verify the downstream validator or consumer; seeing packets at the public socket does not prove local forwarding succeeded.

## Official sources

Technical steps verified on 16 Aug 2026 against the [Jito ShredStream setup and sunset notice](https://docs.jito.wtf/lowlatencytxnfeed/), the [official proxy source and command definitions](https://github.com/jito-labs/shredstream-proxy/blob/master/proxy/src/main.rs), and the [official repository](https://github.com/jito-labs/shredstream-proxy).
