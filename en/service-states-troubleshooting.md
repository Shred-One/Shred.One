---
title: Service states & troubleshooting
description: Understand Shred.one service states and common delivery checks.
order: 6
updated: 2026-08-08
---

# Service states & troubleshooting

Service status describes control-plane progress, not end-to-end packet delivery.

## Service states

- **Inactive:** not deployed and not being billed.
- **Pending:** Subscribe was recorded and checks are in progress.
- **Deploying:** a paid activation or destination change is waiting to be applied.
- **Active:** RelayNetwork reported the destination as applied.
- **Stopping:** delivery was removed from the desired list and confirmation is pending.

## No packets while Active

Confirm the public IPv4 address and UDP port, operating system firewall, provider firewall, NAT, routing, anti-DDoS policy, socket buffers and receiving process. Active does not prove packets reached the application.

## Delayed state

If Deploying or Stopping remains unchanged for an extended period, email support@shred.one with your account email, service ID, destination and the approximate start time.
