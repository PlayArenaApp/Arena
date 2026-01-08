<div align="center">

# Provably Fair

**Complete transparency for every round outcome**

</div>

---

## Overview

Arena is committed to complete transparency. Every round outcome is determined by verifiable on-chain randomness that cannot be manipulated by anyone — including us.

| | |
|:--|:--|
| **Verifiable Randomness** | Outcomes determined by Switchboard VRF, not by any human or algorithm we control |
| **Public Verification** | Anyone can verify that outcomes were fair after the fact |
| **On-Chain Storage** | All data stored on Solana and publicly accessible |

---

## How Randomness Works

Arena uses **Switchboard VRF** (Verifiable Random Function) to determine winners.

### The VRF Process

<div align="center">

```
┌─────────────┐      ┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│ ROUND ENDS  │ ───▶ │   COMMIT    │ ───▶ │   REVEAL    │ ───▶ │   WINNER    │
└─────────────┘      └─────────────┘      └─────────────┘      └─────────────┘
       │                    │                    │                    │
       ▼                    ▼                    ▼                    ▼
   Timer expires      Request sent to      Random value         First byte
                      Switchboard          revealed on-chain    determines winner
```

</div>

### Winner Determination

| First Byte Value | Result |
|:--|:--|
| Even (0, 2, 4, 6...) | Purple wins |
| Odd (1, 3, 5, 7...) | Green wins |

### Why Switchboard VRF?

| | |
|:--|:--|
| **Decentralized** | Multiple independent oracles participate in randomness generation |
| **Cryptographically Secure** | Uses verifiable random function cryptography |
| **On-Chain Verifiable** | All commit/reveal transactions recorded on Solana |
| **Tamper-Proof** | No single party can predict or manipulate the outcome |

---

## Verifying a Round

Every settled round on Arena can be independently verified.

### Step 1: Visit the Provably Fair Page

Go to [playarena.app/provably-fair](https://playarena.app/provably-fair) to see all settled rounds.

### Step 2: Expand a Round

Click on any round to see its full details:

| Field | Description |
|:--|:--|
| **Random Seed** | The hex string of random bytes used |
| **First Byte Value** | The decimal value of the first byte |
| **Winner Logic** | Even = Purple, Odd = Green |
| **VRF Transactions** | Links to on-chain proof |

### Step 3: Verify On-Chain

Each round displays links to:

| Transaction | Description |
|:--|:--|
| **Commit TX** | The initial randomness commitment |
| **Reveal TX** | The randomness reveal |
| **VRF Account** | The Switchboard randomness account |
| **Randomness Proof** | On-chain memo proving the random value |

> Click any link to view the transaction on Solscan.

---

## Understanding the Random Value

The random value is a **SHA-256 hash** displayed as a hexadecimal string:

```
a7b3f9c2e1d4...
```

### Reading the First Byte

The first two characters represent the first byte in hexadecimal:

| Example | Hex → Decimal | Result |
|:--|:--|:--|
| `a7...` | a7 = 167 | 167 is odd → **Green wins** |
| `2e...` | 2e = 46 | 46 is even → **Purple wins** |

---

## Fallback: Blockhash Randomness

In rare cases where Switchboard VRF is unavailable, Arena uses Solana blockhash-based randomness:

```
SHA256(blockhash:roundId)
```

| Step | Action |
|:--|:--|
| **1** | Take the Solana blockhash at round end time |
| **2** | Combine with the round ID |
| **3** | Compute SHA-256 hash |
| **4** | First byte determines winner (same even/odd rule) |

### Verifying Blockhash Randomness

For rounds using blockhash randomness, you can verify yourself:

```bash
# Linux/Mac
echo -n "BLOCKHASH:ROUNDID" | sha256sum
```

> The Provably Fair page provides a "Copy verification command" button for easy verification.

---

## What We Track

Every settled round permanently stores:

| Field | Description |
|:--|:--|
| `vrfRandomValue` | The full random hash (hex string) |
| `vrfAccountPubkey` | Switchboard randomness account address |
| `vrfCommitSignature` | Commit transaction signature |
| `vrfRevealSignature` | Reveal transaction signature |
| `vrfProofSignature` | On-chain memo proof transaction |
| `solanaBlockhash` | Blockhash (for fallback verification) |

---

## Verifying Your Bets On-Chain

Every bet placed on Arena is recorded on the Solana blockchain, providing complete transparency and auditability.

### Method 1: Individual Bet Verification

Each bet transaction includes an **on-chain memo** with your bet details:

```json
{
  "type": "bet",
  "round": 123,
  "side": "purple",
  "amount": 0.5,
  "wallet": "7ww9aDUi...",
  "ts": 1705764000000
}
```

| Step | Action |
|:--|:--|
| **1** | Find your bet transaction signature on the Provably Fair page or in your wallet history |
| **2** | Look up the transaction on [Solscan](https://solscan.io) |
| **3** | Check the **Memo** instruction — it contains your bet details embedded in the transaction |

### Method 2: Round Proof Hash Verification

After each round settles, Arena publishes a **SHA-256 hash** of all bets on-chain via a memo transaction. This allows anyone to verify that the bet list wasn't tampered with.

**What's included in the round proof:**

| Field | Description |
|:--|:--|
| `roundNumber` | The round number |
| `totalBets` | Number of bets in the round |
| `purplePool` | Total SOL bet on purple |
| `greenPool` | Total SOL bet on green |
| `winningSide` | The winner (purple/green) |
| `betsHash` | SHA-256 hash of all bets |

### Verification Steps

| Step | Action |
|:--|:--|
| **1** | Get the list of bets from the Provably Fair page for a specific round |
| **2** | Sort bets by transaction signature (alphabetically) |
| **3** | Create JSON array with format: `[{w: wallet, s: side, a: amount, tx: signature}, ...]` |
| **4** | Compute SHA-256 hash of the JSON string |
| **5** | Compare with the `roundProofHash` stored on-chain |

### Verification Script (Node.js)

```javascript
const crypto = require('crypto');

// Get bets from /api/rounds/history
const bets = [...]; // Array of bets for the round

// Sort by transaction signature
const sorted = bets.sort((a, b) =>
  a.transactionSignature.localeCompare(b.transactionSignature)
);

// Format for hashing
const betsForHash = sorted.map(b => ({
  w: b.walletAddress,
  s: b.side,
  a: b.amount,
  tx: b.transactionSignature
}));

// Compute hash
const hash = crypto
  .createHash('sha256')
  .update(JSON.stringify(betsForHash))
  .digest('hex');

console.log('Computed hash:', hash);
// Compare with roundProofHash from the round data
```

### Verification Script (Bash)

```bash
# Get round data from API and compute hash
curl -s "https://playarena.app/api/rounds/history" | \
  jq -r '.[0].bets | sort_by(.transactionSignature) |
  map({w:.walletAddress,s:.side,a:.amount,tx:.transactionSignature})' | \
  tr -d '\n ' | sha256sum
```

---

## Finding On-Chain Proofs

Each settled round stores two on-chain proof signatures:

| Field | Description | How to Verify |
|:--|:--|:--|
| `vrfProofSignature` | Randomness proof memo | Look up on Solscan, check memo contains round number and random value |
| `roundProofSignature` | Bets hash proof memo | Look up on Solscan, check memo contains `betsHash` |

**Example Solscan lookup:**

```
https://solscan.io/tx/YOUR_PROOF_SIGNATURE
```

> The memo program data will show the JSON proof that was published on-chain.

---

## Additional Transparency

Beyond randomness, the Provably Fair page also shows:

| | |
|:--|:--|
| **All Bets** | Every bet placed in each round with wallet addresses |
| **Payout Transactions** | Transaction links for each winner |
| **Buyback Transactions** | Jupiter swap transactions |
| **Burn Transactions** | REN token burn transactions |
| **Running Totals** | Cumulative rounds, bets, and REN burned |

---

## FAQ

### Can Arena manipulate outcomes?

No. The randomness is generated by Switchboard's decentralized oracle network. We commit to the randomness request before any random value exists, and the reveal is cryptographically bound to the commitment.

### What if Switchboard is down?

We fall back to Solana blockhash-based randomness, which is also verifiable and outside our control.

### Can I verify historical rounds?

Yes. All VRF data is permanently stored and displayed on the Provably Fair page. Older rounds may use the legacy blockhash method.

### How do I know the displayed hash is real?

Every hash links directly to on-chain transactions on Solscan. You can verify the actual data stored on Solana yourself.

### How do I verify my bet was recorded correctly?

Look up your bet transaction on Solscan and check the memo instruction. It will contain a JSON object with your round number, side, amount, and timestamp. This data is embedded in the transaction itself and cannot be altered.

### What if my bet isn't showing on-chain?

Every successful bet creates a Solana transaction with a memo. If your wallet shows the transaction but no memo, contact support with your transaction signature. All valid bets must have an on-chain record.

### Can Arena change the bet list after the round ends?

No. The round proof hash is computed from all bets sorted by transaction signature and published on-chain immediately after settlement. Any modification would change the hash and be detectable.

---

<div align="center">

**More:** [Getting Started](getting-started.md) · [How It Works](how-it-works.md) · [FAQ](faq.md)

<br />

<sub>Built on Solana</sub>

</div>