<div align="center">

# Tokenomics

**Automatic buyback and burn mechanism for REN token holders**

</div>

---

## Fee Distribution

When a round ends, the **losing pool** is distributed as follows:

| Recipient | Share | Description |
|:--|:--:|:--|
| Winners | 90% | Distributed proportionally to winning bettors |
| Buyback & Burn | 8% | Used to buy REN tokens and permanently burn them |
| Platform | 2% | Platform fee for operations and development |

| | |
|:--|:--|
| **Original Bet** | Winners always get their original bet back plus their share of the losing pool |
| **Fee Source** | Fees are only taken from the losing pool, never from the winning pool |
| **No-Contest** | If a round is cancelled, all bets are refunded with no fees |

---

## REN Buyback & Burn

Every settled round, **8% of the losing pool** is used to:

| Step | Action |
|:--|:--|
| **1** | Buy REN tokens on Jupiter (Solana's leading DEX aggregator) |
| **2** | Burn the REN tokens permanently using Token-2022's native burn function |

### Why Buyback & Burn?

| | |
|:--|:--|
| **Deflationary Pressure** | Reduces total REN supply over time |
| **Constant Buy Pressure** | Every round generates buying activity |
| **Transparent** | All transactions are verifiable on-chain |
| **Automatic** | Executes immediately when rounds settle |

### Technical Process

| Step | Action |
|:--|:--|
| **1** | Round settles with a winner determined |
| **2** | 8% of losing pool allocated for buyback |
| **3** | Jupiter Swap — SOL swapped for REN using optimal routing |
| **4** | Token Burn — REN burned via Token-2022's burn instruction |
| **5** | Both transactions linked to round for verification |

---

## Verifying Burns

Every burn transaction can be verified on the [Provably Fair](provably-fair.md) page:

| Step | Action |
|:--|:--|
| **1** | Find any settled round |
| **2** | Click to expand the round details |
| **3** | View the "Swap" transaction (Jupiter buyback) |
| **4** | View the "Burn" transaction (REN token burn) |

> Both transactions link directly to Solscan for full verification.

---

## Example Distribution

**Round Results:**

| | |
|:--|:--|
| **Purple Pool** | 8 SOL |
| **Green Pool** | 12 SOL |
| **Winner** | Purple |

**Losing Pool Distribution (12 SOL):**

| Recipient | Calculation | Amount |
|:--|:--|:--|
| Winners | 12 × 0.90 | 10.8 SOL |
| REN Buyback | 12 × 0.08 | 0.96 SOL |
| Platform | 12 × 0.02 | 0.24 SOL |

**Purple Bettor Winnings:**

If you bet **2 SOL** on Purple (25% of Purple pool):

| | |
|:--|:--|
| **Original bet returned** | 2 SOL |
| **Winnings share** | 10.8 × 0.25 = 2.7 SOL |
| **Total received** | 4.7 SOL |

---

## No-Contest Rounds

When a round is cancelled (due to timeout or lopsided odds):

| | |
|:--|:--|
| **Refunds** | All bets fully refunded |
| **Fees** | No fees taken (no 90/8/2 split) |
| **Burns** | No buyback and burn occurs |
| **Result** | Players receive exactly what they bet |

---

## Cumulative Burns

The [Provably Fair](provably-fair.md) page tracks:

| | |
|:--|:--|
| **Total REN Burned** | Across all rounds |
| **Total SOL Volume** | Processed through the platform |
| **Total Rounds** | Number of settled rounds |

> This number grows with every settled round, creating ongoing deflationary pressure on the REN token supply.

---

## System Components

| Component | Purpose |
|:--|:--|
| Jupiter Lite API | Optimal swap routing (supports Token-2022) |
| Token-2022 Program | Native burn functionality |
| Treasury Wallet | Automated transaction signing |
| Payout Queue | Reliable processing with retry logic |

> All transactions are processed automatically when a round settles — no manual intervention required.

---

## Payout Reliability

Arena includes a robust payout system:

| | |
|:--|:--|
| **Immediate Processing** | Payouts begin as soon as rounds settle |
| **Queue System** | Failed payouts are automatically retried |
| **Recovery Mechanism** | Incomplete payouts are recovered on restart |
| **On-Chain Verification** | All payouts can be verified on Solscan |

---

<div align="center">

**Next:** [Provably Fair](provably-fair.md) — Verify outcomes on-chain

<br />

<sub>Built on Solana</sub>

</div>