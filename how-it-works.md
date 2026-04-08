<div align="center">

# How It Works

**A complete breakdown of Arena's game mechanics**

</div>

---

## The Arena

Two fighters face off in each round:

| | |
|:--|:--|
| **Purple Fighter** | Left side |
| **Green Fighter** | Right side |

Each fighter is randomly selected from a roster of **70 unique characters** representing fighters from around the world. Fighters track their win/loss records over time.

---

## Round Lifecycle

<div align="center">

```
┌─────────────┐      ┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│   WAITING   │ ───▶ │   ACTIVE    │ ───▶ │    BREAK    │ ───▶ │   SETTLED   │
└─────────────┘      └─────────────┘      └─────────────┘      └─────────────┘
```

</div>

### Waiting

- New round created with two random fighters
- Round waits for bets on **both sides**
- Timer doesn't start until both Purple and Green have at least one bet
- If 2 minutes pass with bets on only one side, round is cancelled

### Active (90 seconds)

- Triggered automatically when both sides have bets
- Players can continue placing bets
- Live odds update in real-time
- Betting closes **10 seconds** before round ends
- Live chat available during battles

### Break (30 seconds)

- Round timer has ended
- Odds check: if either side's odds are 1.1x or below, round is cancelled
- Otherwise, winner is determined using VRF
- Fight video plays while payouts are processed in parallel
- Results displayed with winner announcement

### Settlement

- Winners paid directly from the on-chain vault
- Remaining vault balance swept to platform treasury
- Daily jackpot share contributed (1% of total pot)
- Referral rewards distributed
- Buyback and burn executed
- New round begins

---

## On-Chain Vaults

Every bet is held in a **per-round vault** owned by Arena's Solana program. Funds do not sit in a custodial wallet during active rounds.

| | |
|:--|:--|
| **Trustless Custody** | Vaults are program-derived addresses (PDAs) — no human signs to move funds during a round |
| **Direct Payouts** | Winners receive SOL directly from the vault |
| **Verifiable** | Vault address, deposits, and payouts are all publicly viewable on Solscan |
| **Round-Scoped** | Each round has its own vault — funds are never pooled across rounds |

---

## How Winners Are Determined

Arena uses **Switchboard VRF** (Verifiable Random Function) for provably fair outcomes.

### The Process

1. When a round ends (and passes the odds check), a randomness request is sent to Switchboard
2. Switchboard's decentralized oracle network generates verifiable random bytes
3. The first byte of the random value determines the winner:

| Value | Result |
|:--|:--|
| Even (0, 2, 4...) | Purple wins |
| Odd (1, 3, 5...) | Green wins |

### Why VRF?

| | |
|:--|:--|
| **Tamper-proof** | No one can predict or manipulate the outcome |
| **Verifiable** | Anyone can verify the randomness on-chain |
| **Transparent** | All VRF data is stored and displayed publicly |
| **Decentralized** | Multiple independent oracles participate |

---

## No-Contest Rules

Arena automatically protects players from unfair situations. When a no-contest is triggered, **all bets are fully refunded**.

### One-Sided Timeout (2 Minutes)

If only one side has bets and no opposing bets are placed within 2 minutes, the round is cancelled.

| | |
|:--|:--|
| **Why** | Prevents players from having funds locked indefinitely |
| **Trigger** | 2 minutes pass with bets on only one side |
| **Result** | All bets refunded in full |

### Lopsided Odds Protection (1.1x Threshold)

If either side's odds are at or below 1.1x when the battle timer expires, the round is cancelled.

| | |
|:--|:--|
| **Why** | Prevents "guaranteed win" scenarios where one side has overwhelming odds |
| **Trigger** | Either side's odds ≤ 1.1x at round end |
| **Result** | All bets refunded in full |

### Examples

| Purple Pool | Green Pool | Purple Odds | Green Odds | Result |
|:--|:--|:--|:--|:--|
| 9.5 SOL | 0.5 SOL | 1.05x | 20x | Cancelled |
| 0.5 SOL | 9.5 SOL | 20x | 1.05x | Cancelled |
| 8.0 SOL | 2.0 SOL | 1.25x | 5x | Proceeds to VRF |
| 5.0 SOL | 5.0 SOL | 2x | 2x | Proceeds to VRF |

> **Odds calculation:** Total Pool ÷ Side Pool

---

## Payout Calculation

Fees are calculated from the **total pot** (Purple pool + Green pool):

| Recipient | Share of Total Pot | Description |
|:--|:--:|:--|
| Winners | 85% | Distributed proportionally based on bet size |
| Daily Jackpot | 1% | Contributed to the active 24-hour cycle |
| Platform | 14% | Funds buyback & burn, operations, and referral rewards |

### Example

Round ends with:

| | |
|:--|:--|
| **Purple Pool** | 10 SOL |
| **Green Pool** | 5 SOL |
| **Total Pot** | 15 SOL |
| **Winner** | Purple |

Distribution of the total pot:

| Recipient | Calculation | Amount |
|:--|:--|:--|
| Winners | 15 × 0.85 | 12.75 SOL |
| Daily Jackpot | 15 × 0.01 | 0.15 SOL |
| Platform Share | 15 × 0.14 | 2.10 SOL |

If you bet **4 SOL** on Purple (40% of the Purple pool):

| | |
|:--|:--|
| **Your share** | 12.75 × 0.40 = 5.10 SOL |
| **Net profit** | 5.10 − 4.00 = 1.10 SOL |

The platform share covers operational costs, referral rewards, and the buyback & burn — see [Tokenomics](tokenomics.md) for the full breakdown.

---

## Betting Rules

### Limits

| | |
|:--|:--|
| **Minimum Bet** | 0.01 SOL |
| **Maximum Bet** | 10 SOL per wallet |
| **Sides** | One side per wallet per round |

### Adding to Your Bet

- You can add more SOL to your existing bet until betting closes
- You can only add to the **same side** you initially bet on
- Each addition is a separate transaction

### Betting Closes Early

Betting closes **10 seconds** before the round ends to:

- Prevent last-second manipulation
- Ensure fair play for all participants
- Allow time for final bets to confirm on-chain

---

## Fighter System

### Fighter Selection

| | |
|:--|:--|
| **Selection** | Two fighters randomly selected at round start |
| **Cooldown** | One-round cooldown after appearing (prevents repetition) |
| **Variety** | Ensures different fighters across consecutive rounds |

### Fighter Stats

| Stat | Description |
|:--|:--|
| Total Wins | Number of rounds this fighter has won |
| Total Losses | Number of rounds this fighter has lost |
| Last Fought | Timestamp of their most recent battle |
| Active Status | Whether the fighter is currently in rotation |

> Stats are purely cosmetic — **they don't affect outcomes**. Winners are always determined by VRF randomness.

### Fighter Gallery

- View the full active roster on the Gallery page
- Each fighter displays their country of origin on a world map
- Filter by active/inactive status
- See win/loss records and last battle time

---

## Real-Time Features

Arena delivers live updates throughout every round:

| | |
|:--|:--|
| **Bet updates** | See new bets appear instantly |
| **Pool changes** | Watch odds shift in real-time |
| **Round state** | Immediate notifications when rounds start/end |
| **Chat messages** | Instant delivery of chat messages |
| **Win-streak banners** | Special chat banners when a wallet hits a win-streak milestone |
| **Fight videos** | Cinematic post-round playback with winner overlay |
| **Jackpot updates** | Live jackpot amount and winner notifications |

---

## Daily Jackpot

Every round contributes to a **24-hour jackpot prize pool**. At the end of each cycle, one lucky participant wins the entire pot.

### How It Works

| | |
|:--|:--|
| **Contribution** | 1% of each round's total pot is transferred to the jackpot wallet |
| **Cycle** | 24-hour cycles (UTC) |
| **Winner Selection** | Random participant drawn via Switchboard VRF |
| **Payout** | Full jackpot balance sent directly to the winner's wallet |

### Eligibility

Any wallet that places a bet during the active jackpot cycle is automatically entered. The more rounds you participate in, the more entries you have.

### Transparency

| | |
|:--|:--|
| **Per-Cycle Wallet** | Each 24-hour cycle uses its own dedicated wallet |
| **On-Chain Deposits** | Every contribution has a verifiable transaction signature |
| **VRF Drawing** | Winner selected by the same provably fair randomness used for rounds |
| **Verifiable Payout** | Winner payout transaction is publicly viewable on-chain |

> The jackpot amount and countdown timer are displayed in the Arena header.

---

## Referral Rewards

Players can earn a share of every bet placed by users they refer.

| | |
|:--|:--|
| **Earn** | A percentage of each referred user's bet, every round they play |
| **Payment** | Distributed automatically as part of round settlement |
| **Source** | Paid from Arena's platform share — never out of winnings |

> See [Referrals](referrals.md) for full details on sharing your link, tracking earnings, and how rewards are calculated.

---

## Leaderboards

Arena tracks player performance across multiple categories and time periods.

### Ranking Categories

| Category | Description |
|:--|:--|
| **Volume** | Total SOL wagered |
| **Profit** | Net SOL earnings |
| **Streak** | Current consecutive wins |
| **Biggest Win** | Largest single-round win |

### Time Periods

| Period | Description |
|:--|:--|
| Daily | Resets every 24 hours |
| Weekly | Resets every 7 days |
| Monthly | Resets every 30 days |
| All Time | Cumulative since launch |

> Top 20 players are shown in each category. Rankings update automatically.

---

## Player Profiles

Players can optionally create a profile to personalize their Arena experience.

### Profile Features

| | |
|:--|:--|
| **Display Name** | 3–20 characters (alphanumeric + underscore) |
| **Avatar** | Choose from available avatars |
| **Stats** | Total bets, win rate, total wagered, total won |
| **Bet History** | View your latest bets with side, amount, and winnings |
| **Referrals** | Personal referral code, link, and earnings |
| **Win Streak** | Current consecutive wins displayed on leaderboards |

> Profiles are optional. You can bet without creating one — your truncated wallet address will be shown instead.

---

## Chat System

During active rounds, players can chat:

| | |
|:--|:--|
| **Character limit** | 200 characters |
| **Moderation** | Keyword filters and slow-mode controls |
| **Visibility** | All connected users |
| **Win-Streak Banners** | Auto-generated when a wallet hits a streak milestone |
| **Admin messages** | Display with special badges |

---

<div align="center">

**Next:** [Provably Fair](provably-fair.md) — Verify past outcomes

<br />

<sub>Built on Solana</sub>

</div>
