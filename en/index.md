---
title: Docs & Support
description: Set up, manage, and troubleshoot your Shred.one service.
order: 0
updated: 2026-08-21
---

# Docs & Support

Set up, manage, and troubleshoot your Shred.one service.

Shred.one provides low-latency raw Solana shred delivery over UDP:

- **Early access to leader shreds.** Receive Solana shreds extremely early in the propagation path.
- **Clean, authenticated shreds.** Receive leader-signed Solana shreds without unverified, invalid, or spam traffic.
- **Raw UDP to your IP:Port.** Send the feed to the public IPv4 UDP endpoint you control.

The clean, authenticated feed is the service output, not a replacement for defense in depth at your receiver. Because UDP delivery is best-effort, your receiver must still validate packets independently and handle duplicates, out-of-order delivery, missing packets, FEC recovery, firewall configuration, routing, and socket buffers.

## Start with the essentials

- Follow the [Quick start](/docs/quick-start/) to create your first destination.
- Check [Receiver readiness](/docs/receiver-readiness/) before you Subscribe.
- Review [Payments](/docs/payments/) and [Billing & renewal](/docs/billing-renewal/) before funding your account.

A destination moves through Inactive, Pending, Deploying, Active, and Stopping states. Relay activation is complete only after the current full destination list is applied.

## Operate your service

Use [Destination changes](/docs/destination-changes/) when your public IPv4 address or UDP port changes. See [Service states & troubleshooting](/docs/service-states-troubleshooting/) when activation or delivery needs attention.

## Build with Shred.one

Start from the [Shred.one use cases](/docs/use-cases/) when you want to:

- deliver Shred.one packets to a [Solana validator TVU port](/docs/solana-validator/);
- place the [Jito ShredStream proxy](/docs/jito-shredstream/) between Shred.one and one or more local consumers; or
- expose decoded Solana entries through the [local gRPC stream](/docs/early-transaction-decoding/) from the proxy.

Use the [FAQ](/docs/faq/) for port, authentication, duplicate packet and service-boundary answers.

## Service boundary

Shred.one delivers raw Solana Data Shreds and Coding Shreds over UDP. The clean, authenticated feed is the service output, not a replacement for defense in depth at your receiver. Because UDP delivery is best-effort, your receiver must still validate packets independently and handle duplicates, out-of-order delivery, missing packets, FEC recovery, firewall configuration, routing, and socket buffers.

## Need help?

Visit [Support](/docs/support/) or email support@shred.one for account, payment or delivery help.
