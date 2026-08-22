---
title: Solana validator
description: Send Shred.one packets to the actual TVU UDP port of a Solana validator.
order: 4
updated: 2026-08-16
---

# Send Shred.one to a Solana validator

Use Shred.one as an additional shred path to the TVU receiver of your validator. Your validator still validates packets, handles duplicates and performs normal shred recovery.

## 1. Find the actual TVU port

Do not assume that TVU is always port `8000`. The selected TVU port can differ by deployment. The official Jito proxy repository provides `scripts/get_tvu_port.sh` for local-ledger or remote-RPC discovery.

After cloning the [official Jito ShredStream proxy repository](https://github.com/jito-labs/shredstream-proxy), run the checked-out script locally:

```bash
cd shredstream-proxy
export LEDGER_DIR=/path/to/your/validator-ledger
bash ./scripts/get_tvu_port.sh
```

Review the script and pin a trusted repository tag or commit before production use. If your validator is remote, follow the remote-host form in the [official Jito setup guide](https://docs.jito.wtf/lowlatencytxnfeed/#preparation).

## 2. Prepare the UDP path

Allow the discovered TVU UDP port through the provider and host firewalls. Confirm that the public IPv4 routes to the validator process. Keep validator administration and RPC interfaces outside this rule.

```bash
sudo tcpdump -ni any "udp and dst port ${TVU_PORT}"
```

Replace `TVU_PORT` with the discovered numeric port before running the check.

## 3. Point Shred.one to TVU

In **Shred.one -> Services**, add:

```text
IPv4: the public IPv4 address of your validator
UDP port: the discovered TVU port
```

Subscribe and wait for **Active**. Confirm packets at the host and compare validator metrics before and after enabling Shred.one. Active only confirms that Shred.one applied the destination; it is not an end-to-end delivery probe.

## Safe rollout

- Keep the existing validator gossip and shred paths enabled.
- Verify packet volume, duplicate handling and resource use.
- Compare first valid shred arrival with synchronized clocks and a reproducible capture method.
- Unsubscribe Shred.one if the additional path does not improve your workload.

## Official sources

Technical steps verified on 16 Aug 2026 against the [Jito ShredStream setup guide](https://docs.jito.wtf/lowlatencytxnfeed/) and the [official Jito ShredStream proxy repository](https://github.com/jito-labs/shredstream-proxy).
