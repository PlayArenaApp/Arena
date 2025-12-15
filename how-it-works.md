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

Each fighter is randomly selected from a roster of **70+ unique characters** representing fighters from around the world. Fighters track their win/loss records over time.

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
- If 10 minutes pass with bets on only one side, round is cancelled

### Active (3 minutes)

- Triggered automatically when both sides have bets
- Players can continue placing bets
- Live odds update in real-time
- Betting closes **10 seconds** before round ends
- Live chat available during battles

### Break (30 seconds)

- Round timer has ended
- Odds check: if either side's odds are 1.1x or below, round is cancelled
- Otherwise, winner is determined using VRF
- Payouts processed automatically
- Results displayed with winner announcement

### Settlement

- All bets finalized
- Winners receive SOL automatically
- REN buyback and burn executed (8% of losing pool)
- Round data archived for transparency
- New round begins

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

### One-Sided Timeout (10 Minutes)

If only one side has bets and no opposing bets are placed within 10 minutes, the round is cancelled.

| | |
|:--|:--|
| **Why** | Prevents players from having funds locked indefinitely |
| **Trigger** | 10 minutes pass with bets on only one side |
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

Winners split **90% of the losing pool** proportionally based on their bet size.

### Example

Round ends with:

| | |
|:--|:--|
| **Purple Pool** | 10 SOL (3 bettors) |
| **Green Pool** | 5 SOL (2 bettors) |
| **Winner** | Purple |

Distribution of the losing pool (5 SOL):

| Recipient | Calculation | Amount |
|:--|:--|:--|
| Winners | 5 × 0.90 | 4.5 SOL |
| REN Buyback | 5 × 0.08 | 0.4 SOL |
| Platform | 5 × 0.02 | 0.1 SOL |

If you bet **4 SOL** on Purple (40% of Purple pool):

| | |
|:--|:--|
| **Your share** | 4.5 × 0.40 = 1.8 SOL profit |
| **You receive** | 4 + 1.8 = 5.8 SOL total |

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

- View all 70+ fighters on the Gallery page
- Each fighter displays their country of origin on a world map
- Filter by active/inactive status
- See win/loss records and last battle time

---

## Real-Time Features

Arena uses **WebSocket connections** for live updates:

| | |
|:--|:--|
| **Bet updates** | See new bets appear instantly |
| **Pool changes** | Watch odds shift in real-time |
| **Round state** | Immediate notifications when rounds start/end |
| **Chat messages** | Instant delivery of chat messages |
| **Winner announcements** | Celebration animations when rounds settle |

---

## Chat System

During active rounds, players can chat:

| | |
|:--|:--|
| **Character limit** | 200 characters |
| **Moderation** | Basic filters in place |
| **Visibility** | All connected users |
| **Admin messages** | Display with special badges |

---

<div align="center">

**Next:** [Provably Fair](provably-fair.md) — Verify past outcomes

<br />

<sub>Built on Solana</sub>

</div>