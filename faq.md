<div align="center">

# FAQ

**Frequently asked questions about Arena**

</div>

---

## General

### What is Arena?

Arena is a provably fair betting game on Solana where players wager SOL on one of two fighters (Purple or Green). Winners are determined by verifiable on-chain randomness (VRF), and payouts are automatic.

### Is Arena safe to use?

Arena is built on Solana with transparent, verifiable mechanics. All transactions, outcomes, and payouts are recorded on-chain and can be independently verified. As with any betting platform, only wager what you can afford to lose.

### What wallets are supported?

| Wallet | Type |
|:--|:--|
| Phantom | Browser / Mobile |
| Solflare | Browser / Mobile |
| Trust | Browser / Mobile |
| MetaMask | Browser / Mobile |
| Coinbase Wallet | Browser / Mobile |
| Ledger | Hardware |
| Torus | Social Login |

### Is Arena available on mobile?

Yes. Use Arena on mobile through your wallet's built-in browser (Phantom, Solflare, or Coinbase Wallet mobile apps).

---

## Wallet & Connection

### Why do I need to sign a message when connecting?

The signature verification proves you own the wallet without costing any gas fees. This is a standard security practice that protects against wallet spoofing.

### How long do sessions last?

Wallet sessions last **2 hours** for security. After that, you'll need to reconnect and sign again.

### Can I auto-reconnect?

Yes. If you return within your session window, Arena will automatically reconnect to your previously connected wallet.

### Can I switch wallets?

Yes. Disconnect your current wallet and connect with a different one. Each wallet has its own betting history.

---

## Betting

### What are the betting limits?

| | |
|:--|:--|
| **Minimum Bet** | 0.01 SOL |
| **Maximum Bet** | 10 SOL per wallet per round |

### Can I bet on both sides?

No. You can only bet on one side (Purple or Green) per round. Once you place a bet, you're locked to that side.

### Can I add to my bet?

Yes. You can add more SOL to your existing bet on the same side until betting closes (10 seconds before round end).

### Why does betting close early?

Betting closes 10 seconds before the round ends to prevent last-second manipulation and ensure fair play.

### What happens if I'm the only bettor?

The round won't start until both sides have at least one bet. If no one bets on the other side within 10 minutes, your bet is refunded.

### Can I cancel my bet?

No. Once a bet is placed and confirmed on-chain, it cannot be cancelled or withdrawn.

---

## No-Contest & Cancellations

### What is a no-contest?

A no-contest is when a round is cancelled and all bets are fully refunded. This happens in two situations:

| Condition | Trigger |
|:--|:--|
| **One-sided timeout** | Only one side has bets for 10 minutes |
| **Lopsided odds** | Either side's odds drop to 1.1x or below |

### Why was my round cancelled due to "lopsided odds"?

If one side has overwhelming bets (odds ≤ 1.1x), the round is cancelled to protect players. A 95/5 split means one side would only profit ~5%—not worth the risk. All bets are fully refunded.

### What happens to my bet if a round is cancelled?

Your bet is fully refunded with no fees taken. The refund is automatic.

### How do I know if a round was cancelled?

Cancelled rounds are marked on the Provably Fair page with the reason (timeout or odds). The UI will also show a cancellation notice.

---

## Rounds & Timing

### How long is a round?

Each round lasts **3 minutes** once both sides have at least one bet.

### When does the timer start?

The timer starts automatically when both Purple and Green have at least one bet placed.

### What happens after a round ends?

| Step | Action |
|:--|:--|
| **1** | Odds checked (if either side ≤ 1.1x, round is cancelled) |
| **2** | Winner determined by VRF randomness |
| **3** | Payouts processed automatically |
| **4** | 30-second break |
| **5** | New round begins |

### What is the break between rounds?

There's a **30-second break** after each round settles before the next round begins.

---

## Payouts

### How do I claim my winnings?

You don't need to claim manually. Winnings are **automatically sent** to your wallet when a round settles.

### How are winnings calculated?

Winners split 90% of the losing pool proportionally based on their bet size:

| | |
|:--|:--|
| **Formula** | Your Winnings = (Your Bet ÷ Total Winning Pool) × (Losing Pool × 0.90) |

### Do I get my original bet back?

Yes. If you win, you receive your original bet **plus** your share of the losing pool.

### How long do payouts take?

Payouts are processed immediately when a round settles. You should see the SOL in your wallet within seconds.

### I won but didn't receive my payout?

Check the Provably Fair page to verify your win and view the payout transaction. If there's an issue, the transaction may have failed due to network congestion—payouts are retried automatically.

---

## Randomness & Fairness

### How is the winner determined?

Winners are determined by **Switchboard VRF** (Verifiable Random Function). The first byte of the random value is checked:

| Value | Result |
|:--|:--|
| Even number | Purple wins |
| Odd number | Green wins |

### Can Arena manipulate outcomes?

No. The randomness is generated by Switchboard's decentralized oracle network, which Arena does not control. The random value is committed before it's generated.

### How can I verify a round was fair?

Visit the [Provably Fair](provably-fair.md) page to see all historical rounds with their VRF data. Each round includes links to on-chain transactions you can verify on Solscan.

### Does pool size affect who wins?

No. The winner is determined purely by random coin flip (VRF). Pool size only affects how much winners receive.

### What if VRF is unavailable?

If Switchboard VRF is temporarily unavailable, Arena falls back to Solana blockhash-based randomness, which is also verifiable and outside our control.

---

## Fighters

### Do fighters have different stats or abilities?

No. Fighters are purely cosmetic. All outcomes are determined by randomness, not by fighter attributes.

### Why do fighters have win/loss records?

Fighter stats are tracked for fun and displayed in the Gallery. They reflect historical outcomes but don't influence future results.

### How are fighters selected?

Two fighters are randomly selected at the start of each round from a roster of **70+ characters**. Fighters have a one-round cooldown after appearing to ensure variety.

### Where can I see all fighters?

Visit the Fighter Gallery page to see all fighters, their countries of origin, and their win/loss records.

---

## REN Token

### What is REN?

REN is the token associated with Arena. 8% of each round's losing pool is used to buy REN on Jupiter and burn it permanently.

### How does buyback and burn work?

| Step | Action |
|:--|:--|
| **1** | Round settles, 8% of losing pool (in SOL) allocated |
| **2** | SOL swapped for REN via Jupiter |
| **3** | REN tokens burned using Token-2022's burn function |
| **4** | Both transactions verifiable on-chain |

### Where can I verify burns?

The Provably Fair page shows buyback (Swap) and burn transactions for every round. Click the links to view on Solscan.

### Do I need REN to play?

No. Arena only uses SOL for betting. REN is not required to play.

---

## Treasury & Wallet Connections

### Why does Bubble Maps show all player wallets connected?

This is expected behavior due to how Arena's treasury system works:

| | |
|:--|:--|
| **Bets** | All player bets are sent to a single treasury wallet |
| **Payouts** | All winnings are paid out from the same treasury wallet |

Because every player's wallet both sends SOL to (bets) and receives SOL from (payouts) the treasury, on-chain analysis tools like Bubble Maps will show connections between all participating wallets. This doesn't mean wallets are linked or controlled by the same entity—it simply reflects normal gameplay where funds flow through the central treasury.

> This is standard architecture for betting platforms and ensures transparent, verifiable payouts.

### Where are my SOL sent when I bet?

Bets are sent to Arena's treasury wallet, which automatically processes payouts and burns.

### How does Arena verify bets?

Every bet transaction is verified on-chain before being accepted:

| Check | Description |
|:--|:--|
| **Signature** | Transaction signature is valid |
| **Sender** | Matches your connected wallet |
| **Amount** | Matches your bet amount |
| **Destination** | Is the treasury wallet |

---

## Technical

### What network is Arena on?

Arena runs on **Solana Mainnet**.

### Is there rate limiting?

Yes, to prevent abuse:

| Limit | Value |
|:--|:--|
| API requests | 100/min per IP |
| Bets | 10/min per IP |
| Bets | 30/min per wallet |
| Chat messages | 20/min per IP |

### Is the smart contract audited?

Arena's betting system currently runs server-side with on-chain transactions for all bets, payouts, and burns. A fully on-chain Anchor smart contract is in development.

---

## Support

### How do I get help?

For support, join our community channels or reach out through the website.

### I have a suggestion for Arena

We welcome feedback. Share your ideas in our community channels.

### Where can I see platform stats?

The Provably Fair page shows cumulative stats including total rounds, total volume, and total REN burned.

---

<div align="center">

**More:** [Getting Started](getting-started.md) · [How It Works](how-it-works.md) · [Provably Fair](provably-fair.md)

<br />

<sub>Built on Solana</sub>

</div>