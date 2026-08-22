---
title: Quick start
description: Start Shred.one in three visual steps and verify UDP delivery.
order: 1
updated: 2026-08-16
---

# Quick start

Start your first Shred.one destination and a 24-hour service cycle.

<ol class="docs-visual-steps">
  <li>
    <strong>Sign in to Shred.one</strong>
    <p>Enter your email and open the secure single-use link.</p>
    <button class="docs-image-trigger" type="button" data-docs-image-trigger aria-label="View larger: Shred.one Sign in screen">
      <img src="/docs/quick-start/sign-in.png" alt="Shred.one sign-in form with an email field and Send magic link button" width="960" height="720" loading="lazy" />
    </button>
  </li>
  <li>
    <strong>Fund your account</strong>
    <p>Copy the fixed deposit address and send native USDC on Solana mainnet.</p>
    <button class="docs-image-trigger" type="button" data-docs-image-trigger aria-label="View larger: Shred.one Account screen">
      <img src="/docs/quick-start/fund-account.png" alt="Shred.one Account screen showing the USDC deposit address and QR code" width="960" height="720" loading="lazy" />
    </button>
  </li>
  <li>
    <strong>Add and activate</strong>
    <p>Enter your public IPv4 and UDP port, then Subscribe and wait for Active.</p>
    <button class="docs-image-trigger" type="button" data-docs-image-trigger aria-label="View larger: Shred.one Services screen">
      <img src="/docs/quick-start/add-destination.png" alt="Shred.one Services screen showing the region, public IPv4 and UDP port fields" width="960" height="720" loading="lazy" />
    </button>
  </li>
</ol>

## 1. Sign in

Open Shred.one, choose **Sign in**, enter your email address and use the secure single-use link sent to you.

## 2. Fund your account

Open **Account** and copy the fixed deposit address. Send only native USDC on Solana mainnet. A finalized payment credits your shared balance; it does not start a Shred.one service automatically.

## 3. Add and activate a destination

Open **Services**, select Amsterdam and enter a public IPv4 address with a UDP port from 1 to 65535. Confirm that your receiver and firewall are ready before continuing, then choose **Add destination**.

Choose **Subscribe**. Shred.one checks your balance and available capacity before debit. Wait for the service to become **Active** before expecting packets.

Active confirms that Shred.one applied the destination. It does not prove that the packets passed your provider firewall, host firewall or receiving process.

## Choose the correct receiver port

Your Shred.one destination must be the public address and UDP port of the process that should receive packets. Continue with the matching guide:

- [Solana validator TVU](/docs/solana-validator/)
- [Jito ShredStream proxy, including forward-only mode](/docs/jito-shredstream/)
- [Early transaction decoding over local gRPC](/docs/early-transaction-decoding/)
