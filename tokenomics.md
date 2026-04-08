<div align="center">

# Tokenomics

**Automatic buyback and burn mechanism funded by every settled round**

</div>

---

## Fee Distribution

When a round ends, fees are calculated as a percentage of the **total pot** (Purple pool + Green pool):

| Recipient | Share of Total Pot | Description |
|:--|:--:|:--|
| Winners | 85% | Distributed proportionally to bettors on the winning side |
| Daily Jackpot | 1% | Funds the 24-hour jackpot prize pool |
| Platform | 14% | Funds buyback & burn, operations, and referral rewards |

The 14% platform share is allocated as follows:

| Allocation | Description |
|:--|:--|
| **Referral Rewards** | A percentage of each referred user's bet (paid first, capped) |
| **Buyback & Burn** | 50% of the remaining platform share |
| **Operations** | 50% of the remaining platform share |

| | |
|:--|:--|
| **Original Bet** | Winners always get their original bet back as part of their share |
| **No-Contest** | If a round is cancelled, all bets are refunded with **no fees** |
| **Source** | Fees come from the total pot — referral rewards are never deducted from winnings |

---

## Token Buyback & Burn

Every settled round, half of the platform share is used to:

| Step | Action |
|:--|:--|
| **1** | Buy tokens on Jupiter (Solana's leading DEX aggregator) |
| **2** | Burn the tokens permanently using Token-2022's native burn function |

### Why Buyback & Burn?

| | |
|:--|:--|
| **Deflationary Pressure** | Reduces total token supply over time |
| **Constant Buy Pressure** | Every round generates buying activity |
| **Transparent** | All transactions are verifiable on-chain |
| **Automatic** | Executes immediately when rounds settle |

### Technical Process

| Step | Action |
|:--|:--|
| **1** | Round settles with a winner determined |
| **2** | Vault drains to the platform treasury |
| **3** | Jupiter Swap — SOL swapped for tokens using optimal routing |
| **4** | Token Burn — tokens burned via Token-2022's burn instruction |
| **5** | Both transactions linked to the round for verification |

---

## Verifying Burns

Every burn transaction can be verified on the [Provably Fair](provably-fair.md) page:

| Step | Action |
|:--|:--|
| **1** | Find any settled round |
| **2** | Click to expand the round details |
| **3** | View the "Swap" transaction (Jupiter buyback) |
| **4** | View the "Burn" transaction (token burn) |

> Both transactions link directly to Solscan for full verification.

---

## Example Distribution

**Round Results:**

| | |
|:--|:--|
| **Purple Pool** | 8 SOL |
| **Green Pool** | 12 SOL |
| **Total Pot** | 20 SOL |
| **Winner** | Purple |

**Pot Distribution:**

| Recipient | Calculation | Amount |
|:--|:--|:--|
| Winners | 20 × 0.85 | 17.00 SOL |
| Daily Jackpot | 20 × 0.01 | 0.20 SOL |
| Platform Share | 20 × 0.14 | 2.80 SOL |

**Purple Bettor Winnings:**

If you bet **2 SOL** on Purple (25% of the Purple pool):

| | |
|:--|:--|
| **Your share of winnings** | 17.00 × 0.25 = 4.25 SOL |
| **Net profit** | 4.25 − 2.00 = 2.25 SOL |

**Platform Share Allocation (2.80 SOL, before referrals):**

| Allocation | Calculation | Amount |
|:--|:--|:--|
| Buyback & Burn | 2.80 × 0.50 | 1.40 SOL |
| Operations | 2.80 × 0.50 | 1.40 SOL |

> If any winners or losers in this round were referred, a portion of those bets would be paid out as referral rewards from the platform share before the 50/50 split.

---

## Daily Jackpot

In addition to the buyback and burn mechanism, Arena runs a **24-hour jackpot cycle** funded by 1% of every round's total pot.

| | |
|:--|:--|
| **Contribution** | 1% of the total pot |
| **Cycle Duration** | 24 hours (UTC) |
| **Winner Selection** | VRF-based random draw from all participants in the cycle |
| **Payout** | Entire jackpot balance sent to the winner |

Each cycle uses a dedicated on-chain wallet. All contributions and the winner payout are verifiable on Solscan.

> See [How It Works — Daily Jackpot](how-it-works.md#daily-jackpot) for full details.

---

## Referral Rewards

A percentage of every referred user's bet is paid to their referrer, automatically, as part of round settlement. Rewards come out of the platform's share — they never reduce winnings or pool size.

> See [Referrals](referrals.md) for the full breakdown.

---

## No-Contest Rounds

When a round is cancelled (due to timeout or lopsided odds):

| | |
|:--|:--|
| **Refunds** | All bets fully refunded |
| **Fees** | No fees taken |
| **Burns** | No buyback and burn occurs |
| **Jackpot** | No jackpot contribution |
| **Result** | Players receive exactly what they bet |

---

## Cumulative Burns

The [Provably Fair](provably-fair.md) page tracks:

| | |
|:--|:--|
| **Total Burned** | Tokens permanently removed across all rounds |
| **Total SOL Volume** | Processed through the platform |
| **Total Rounds** | Number of settled rounds |

> This number grows with every settled round, creating ongoing deflationary pressure on the token supply.

---

## System Components

| Component | Purpose |
|:--|:--|
| On-Chain Vault Program | Trustless custody of bets per round |
| Jupiter Lite API | Optimal swap routing (supports Token-2022) |
| Token-2022 Program | Native burn functionality |
| Per-Round Treasury | Funds the off-chain pieces of settlement |
| Payout Recovery Workers | Background retries for failed swaps and burns |

> All transactions are processed automatically when a round settles — no manual intervention required.

---

## Payout Reliability

Arena includes a robust payout system:

| | |
|:--|:--|
| **Immediate Processing** | Payouts begin as soon as rounds settle |
| **On-Chain Vault** | Winners are paid directly from the round's program vault |
| **Retry Workers** | Failed buyback or burn attempts are retried automatically |
| **On-Chain Verification** | All payouts can be verified on Solscan |

---

<div align="center">

**Next:** [Referrals](referrals.md) · [Provably Fair](provably-fair.md)

<br />

<sub>Built on Solana</sub>

</div>
