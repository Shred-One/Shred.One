---
title: Receiver readiness
description: Prepare a public IPv4 UDP receiver for Shred.one delivery.
order: 2
updated: 2026-08-08
---

# Receiver readiness

Prepare your endpoint before starting a paid cycle.

## Network checklist

- Use a public IPv4 unicast address.
- Open the selected UDP port in the operating system and provider firewall.
- Confirm NAT and routing forward traffic to the receiving process.
- Review anti-DDoS rules that may filter sustained UDP traffic.

## Application checklist

Your receiver is responsible for socket and kernel buffers, packet validation, duplicates, out-of-order delivery and FEC recovery. UDP is best-effort; Shred.one does not provide replay or retransmission.

## Status meaning

Active means RelayNetwork reported that the destination was applied. It does not prove that packets crossed the Internet, passed your firewall or reached your application.
