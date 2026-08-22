# Shred.one

Low-latency raw Solana shreds delivered directly to your UDP endpoint.

**Fast. Simple. Reliable.**

[Start benchmarking](https://shred.one/login/?next=%2Fapp%2F) · [Read Docs & Support](en/)

## Region network

Amsterdam is the first open region. More regions are coming later.

| Region | Availability |
| --- | --- |
| Amsterdam | Available now |
| London | Coming later |
| Frankfurt | Coming later |
| New York | Coming later |

## Benchmark Shred.one in just a few minutes.

1. **Sign in by email.** Use a single-use magic link.
2. **Fund your account.** Pay with native USDC on Solana.
3. **Add your IP:Port.** Enter your public IPv4:UDP endpoint and start receiving raw shreds.

Fully automated. Start benchmarking in minutes.

## Raw Shred Delivery

- **Early access to leader shreds.** Receive Solana shreds extremely early in the propagation path.
- **Clean, authenticated shreds.** Leader-signed Solana shreds without unverified, invalid, or spam traffic.
- **Raw UDP to your IP:Port.** Receive raw Solana shreds directly at your UDP endpoint.

### Lower bandwidth footprint

Clean, leader-signed shreds mean less wasted traffic. No unverified or spam shreds — less bandwidth, less receiver load, more headroom.

## Side-by-side benchmark in Amsterdam

57,476 matched transactions compared by first arrival time.

| Feed | Arrived first | Avg lead | P50 | P75 | P95 | P99 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| **Shred.one** | **87.53%** | 3.397 ms | 2.789 ms | 4.553 ms | 8.611 ms | 12.741 ms |
| Jito ShredStream | 12.47% | 0.382 ms | 0.250 ms | 0.587 ms | 0.970 ms | 1.411 ms |

**Lead metrics are calculated when that feed arrived first.**

0 dropped · 0 decode errors · 0 bad signatures

**Methodology:** Both feeds were observed in the same Amsterdam comparison setup. Only transactions present in both captures were matched, and first observed arrival determined the winner. Lead percentiles are calculated separately for the feed that arrived first. Results describe this comparison, not a delivery guarantee.

### ~⅔ lower bandwidth observed vs Jito ShredStream

Observed in the same Amsterdam comparison setup. Clean, authenticated shreds with less redundant traffic reaching your receiver.

## Pricing

| Plan | Price | Availability |
| --- | ---: | --- |
| Regular Pricing | 15 USDC / day | Standard price |
| Founding Pricing | **6.5 USDC / day** | Currently available until Sep 30, 2026 at 23:59 UTC |

Benchmark once or keep it running. Make one native USDC payment of at least **195 USDC** before the cutoff to keep this Founding Pricing forever. Limited availability.

Available now: **Amsterdam**.

## Know what you are benchmarking

### Can I start benchmarking with 6.5 USDC?

Yes. During Founding Pricing, 6.5 USDC funds one service for one 24-hour cycle, so you can benchmark once or keep the service running.

### Can one 195 USDC payment keep my Founding price?

Yes. Make one native USDC payment of at least 195 USDC by Sep 30, 2026 at 23:59 UTC. The full payment is credited to your account balance; it is not an extra fee. Your account then keeps the 6.5 USDC / day Founding Pricing forever across every current and future service and region, even if subscriptions stop, expire, or are interrupted. Multiple smaller payments are not combined for qualification.

### Can I use Shred.one with Jito ShredStream?

Yes. Point Shred.one to the proxy source UDP port and use the official proxy in forward-only mode without requesting shreds from Jito. [Read the Jito ShredStream guide](en/jito-shredstream.md).

### Can I send Shred.one directly to an Agave validator?

Yes. Route Shred.one to the actual TVU UDP port used by your validator, then validate and measure the additional packet path on your own host. [Read the Solana validator guide](en/solana-validator.md).

### Can I benchmark Shred.one against Jito ShredStream or my current feed?

Yes. Run the feeds alongside each other and compare them using your own infrastructure and measurements.

### Can I receive decoded transactions?

Yes. Run the official Jito proxy locally with its gRPC service enabled. SubscribeEntries streams a slot and serialized Vec<Entry> bytes; each decoded Solana Entry can contain transactions. Early decoding does not mean those transactions are confirmed or finalized. [Read the early decoding guide](en/early-transaction-decoding.md).

## Ready to benchmark?

Benchmark Shred.one with your own infrastructure.

[Start benchmarking](https://shred.one/login/?next=%2Fapp%2F)

Best-effort UDP — no replay or resend.

Need help? Email [support@shred.one](mailto:support@shred.one).
