---
title: Destination changes
description: Change a Shred.one public IPv4 UDP destination safely.
order: 5
updated: 2026-08-08
---

# Destination changes

Each service uses one public IPv4 address and UDP port.

## While Inactive

You can change the destination before the next Subscribe. This does not debit balance, use capacity or deploy the destination.

## While Active

The latest valid change replaces any earlier request that has not been applied. The current destination remains active until RelayNetwork applies the new list. A short interruption may occur during the change.

## Change limit

An Active service accepts up to 10 valid changes in a rolling 24-hour window. From the sixth accepted change, Services shows the remaining count. Invalid, rejected and unchanged requests do not count.
