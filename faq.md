<div align="center">

# FAQ

**Frequently asked questions about Arena**

</div>

---

## General

### What is Arena?

Arena is a provably fair betting game on Solana where players wager SOL on one of two fighters (Purple or Green). Bets are held in an on-chain Solana program vault, winners are determined by verifiable on-chain randomness (VRF), and payouts are automatic.

### Is Arena safe to use?

Arena is built on Solana with transparent, verifiable mechanics. Bets are custodied by an on-chain program — not a custodial wallet — and all transactions, outcomes, and payouts are recorded on-chain and can be independently verified. As with any betting platform, only wager what you can afford to lose.

### What wallets are supported?

| Wallet | Type |
|:--|:--|
| Phantom | Browser / Mobile |
| Solflare | Browser / Mobile |
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

The round won't start until both sides have at least one bet. If no one bets on the other side within 2 minutes, your bet is refunded.

### Can I cancel my bet?

No. Once a bet is placed and confirmed on-chain, it cannot be cancelled or withdrawn.

### Where does my SOL go when I place a bet?

Your SOL is deposited into the round's on-chain **vault** — a Solana program-owned account that holds funds in trust until the round settles. Vault deposits, payouts, and the final sweep are all viewable on Solscan.

---

## No-Contest & Cancellations

### What is a no-contest?

A no-contest is when a round is cancelled and all bets are fully refunded. This happens in two situations:

| Condition | Trigger |
|:--|:--|
| **One-sided timeout** | Only one side has bets for 2 minutes |
| **Lopsided odds** | Either side's odds drop to 1.1x or below |

### Why was my round cancelled due to "lopsided odds"?

If one side has overwhelming bets (odds ≤ 1.1x), the round is cancelled to protect players. A 95/5 split means one side would only profit ~5% — not worth the risk. All bets are fully refunded.

### What happens to my bet if a round is cancelled?

Your bet is fully refunded with no fees taken. The refund is automatic.

### How do I know if a round was cancelled?

Cancelled rounds are marked on the Provably Fair page with the reason (timeout or odds). The UI will also show a cancellation notice.

---

## Rounds & Timing

### How long is a round?

Each round lasts **90 seconds** once both sides have at least one bet.

### When does the timer start?

The timer starts automatically when both Purple and Green have at least one bet placed.

### What happens after a round ends?

| Step | Action |
|:--|:--|
| **1** | Odds checked (if either side ≤ 1.1x, round is cancelled) |
| **2** | Winner determined by VRF randomness |
| **3** | Payouts processed from the on-chain vault |
| **4** | Fight video plays while settlement runs |
| **5** | 30-second break, then a new round begins |

### What is the break between rounds?

There's a **30-second break** after each round settles before the next round begins.

---

## Payouts

### How do I claim my winnings?

You don't need to claim manually. Winnings are **automatically sent** to your wallet from the on-chain vault when a round settles.

### How are winnings calculated?

Winners split **85% of the total pot** proportionally based on bet size:

| | |
|:--|:--|
| **Formula** | Your Winnings = (Your Bet ÷ Winning Pool) × (Total Pot × 0.85) |

### Do I get my original bet back?

Yes. Your share of the 85% winnings pool already includes your original bet plus your portion of the loser's pool.

### How long do payouts take?

Payouts are processed immediately when a round settles. You should see the SOL in your wallet within seconds.

### I won but didn't receive my payout?

Check the Provably Fair page to verify your win and view the payout transaction. If there's an issue, the transaction may have failed due to network congestion — payouts are retried automatically.

---

## Fees

### How is the pot divided?

| Recipient | Share of Total Pot |
|:--|:--:|
| Winners | 85% |
| Daily Jackpot | 1% |
| Platform | 14% |

The 14% platform share funds operations, the buyback & burn program, and referral rewards.

### Are fees taken from winnings?

Fees are taken from the **total pot**, not from individual winnings. Your share is a proportional cut of the 85% allocated to winners.

### Is buyback & burn really automatic?

Yes. Half of the 14% platform share is automatically used to buy tokens on Jupiter and burn them via Token-2022's native burn instruction. Both transactions are linked from each settled round on the Provably Fair page.

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

Two fighters are randomly selected at the start of each round from a roster of **70 characters**. Fighters have a one-round cooldown after appearing to ensure variety.

### Where can I see all fighters?

Visit the Fighter Gallery page to see all fighters, their countries of origin, and their win/loss records.

---

## On-Chain Vaults

### What is the vault?

Each round has its own **vault** — a Solana program-owned account (PDA) that holds all bets for that round. Funds are not held in a custodial wallet during a round.

### Why is this important?

It means bets are in trustless custody while the round is live. Arena cannot move funds out of a vault arbitrarily — only the program can, and only after the round has been finalized on-chain.

### Where can I see the vault?

The Provably Fair page links each settled round to its vault address on Solscan, where you can see every deposit and the final payout flow.

---

## Token Buyback & Burn

### What is the platform token?

A community token associated with Arena. Half of every platform fee is used to buy this token on Jupiter and burn it permanently.

### How does buyback and burn work?

| Step | Action |
|:--|:--|
| **1** | Round settles, platform share allocated |
| **2** | Half of the share is swapped from SOL → token via Jupiter |
| **3** | Tokens burned using Token-2022's burn function |
| **4** | Both transactions verifiable on-chain |

### Where can I verify burns?

The Provably Fair page shows buyback (Swap) and burn transactions for every round. Click the links to view on Solscan.

### Do I need the token to play?

No. Arena only uses SOL for betting. The token is not required to play.

---

## Daily Jackpot

### What is the Daily Jackpot?

Arena runs a 24-hour jackpot cycle. 1% of every round's total pot is contributed to the jackpot. At the end of each cycle, a random participant wins the entire pot.

### How do I enter the jackpot?

You're automatically entered when you place a bet during an active jackpot cycle. Every round you participate in counts as an entry.

### How is the jackpot winner selected?

The winner is selected using the same Switchboard VRF randomness used for round outcomes — provably fair and verifiable on-chain.

### Where can I see the current jackpot?

The jackpot amount and countdown timer are displayed in the Arena header when a cycle is active.

### Can I verify the jackpot payout?

Yes. Each jackpot cycle uses a dedicated on-chain wallet. All contributions and the winner payout have verifiable transaction signatures on Solscan.

---

## Referrals

### How does the referral program work?

Share your referral link (`playarena.app/?ref=YOURCODE`). When someone you invite plays, you earn a share of every bet they place — win or lose. Rewards are paid automatically as part of round settlement.

### Where do referral rewards come from?

From Arena's 14% platform share, not from winnings or referral pools. Your friends' bets and payouts are not reduced by the program.

### Where do I get my referral link?

Connect your wallet, create a profile, and open the Referrals tab in your profile.

> See [Referrals](referrals.md) for full details.

---

## Leaderboards & Profiles

### What are the leaderboards?

Arena tracks player rankings across four categories: **Volume** (total SOL wagered), **Profit** (net earnings), **Streak** (consecutive wins), and **Biggest Win** (largest single win). Each can be filtered by Daily, Weekly, Monthly, or All Time.

### How do I create a profile?

Connect your wallet and click your wallet address in the header to access your profile. From there you can set a display name and choose an avatar.

### Do I need a profile to play?

Yes. A profile is required to place bets. Connect your wallet and click your wallet address in the header to set up your display name and avatar.

### What stats does my profile track?

| Stat | Description |
|:--|:--|
| Total Bets | Number of bets placed |
| Win Rate | Percentage of rounds won |
| Total Wagered | Total SOL bet across all rounds |
| Total Won | Total SOL received from winnings |
| Referral Earnings | Total SOL earned from the referral program |

### Can I see my bet history?

Yes. Your profile page shows your latest bets with the side you chose, amount wagered, and winnings.

---

## Treasury & Wallet Connections

### Why does Bubble Maps show wallets connected?

This is expected behavior because of how settlement works. Per-round vaults pay winners, and a per-round treasury wallet handles the off-chain pieces of settlement (jackpot transfer, referral payouts, sweep to the developer wallet). Because many wallets receive SOL from these treasuries, on-chain analysis tools will draw connections between participating wallets — this reflects normal gameplay flow, not common ownership.

> Trustless on-chain custody, transparent settlement, and verifiable payouts are the design goals here.

### How does Arena verify bets?

Every bet transaction is verified on-chain before being accepted:

| Check | Description |
|:--|:--|
| **Signature** | Transaction signature is valid |
| **Sender** | Matches your connected wallet |
| **Amount** | Matches your bet amount |
| **Destination** | Is the round's vault PDA |

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

Arena's bet custody runs through an on-chain Anchor program that has been internally reviewed and tested. Public audit reports will be linked from the documentation when available.

---

## Support

### How do I get help?

For support, join our community channels or reach out through the website.

### I have a suggestion for Arena

We welcome feedback. Share your ideas in our community channels.

### Where can I see platform stats?

The Provably Fair page shows cumulative stats including total rounds, total volume, and total tokens burned.

---

<div align="center">

**More:** [Getting Started](getting-started.md) · [How It Works](how-it-works.md) · [Referrals](referrals.md) · [Provably Fair](provably-fair.md)

<br />

<sub>Built on Solana</sub>

</div>
