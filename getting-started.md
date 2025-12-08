<div align="center">

# Getting Started

**Everything you need to start betting on Arena**

</div>

---

## Prerequisites

| | |
|:--|:--|
| **Solana Wallet** | Any supported wallet provider |
| **SOL** | Solana's native token for placing bets |

---

## Supported Wallets

| Wallet | Type | Link |
|:--|:--|:--|
| Phantom | Browser / Mobile | [phantom.app](https://phantom.app) |
| Solflare | Browser / Mobile | [solflare.com](https://solflare.com) |
| Trust | Browser / Mobile | [trustwallet.com](https://trustwallet.com) |
| MetaMask | Browser / Mobile | [metamask.io](https://metamask.io) |
| Coinbase Wallet | Browser / Mobile | [coinbase.com/wallet](https://www.coinbase.com/wallet) |
| Ledger | Hardware | [ledger.com](https://www.ledger.com) |
| Torus | Social Login | [tor.us](https://tor.us) |

---

## Install a Wallet

### Phantom (Recommended)

1. Visit [phantom.app](https://phantom.app)
2. Download the browser extension for Chrome, Firefox, Brave, or Edge
3. Create a new wallet or import an existing one
4. Securely store your recovery phrase

### Solflare

1. Visit [solflare.com](https://solflare.com)
2. Download the browser extension or mobile app
3. Create or import your wallet

### Coinbase Wallet

1. Download from [coinbase.com/wallet](https://www.coinbase.com/wallet)
2. Follow the setup instructions
3. Enable Solana in your wallet settings

### Ledger (Hardware)

1. Connect your Ledger device
2. Install the Solana app via Ledger Live
3. Use a compatible browser extension to connect

---

## Fund Your Wallet

You'll need SOL to place bets:

| Method | Description |
|:--|:--|
| **Exchange** | Purchase on Coinbase, Binance, or Kraken and withdraw to your wallet |
| **On-Ramp** | Use a fiat on-ramp service within your wallet |
| **Transfer** | Receive SOL from another wallet |

---

## Connect to Arena

1. Visit [playarena.app](https://playarena.app)
2. Click **Connect Wallet** in the header
3. Select your wallet from the popup
4. Approve the connection request
5. Sign the verification message (no gas fees)

Your wallet address and SOL balance will appear in the header once connected.

> **Sessions** — Last 2 hours for security. Auto-reconnect is enabled within your session window.

---

## Place Your First Bet

1. **Choose your side** — Click on Purple or Green
2. **Enter amount** — Use the slider or input field (0.01–10 SOL)
3. **Confirm** — Click the bet button and approve the transaction
4. **Wait** — Your bet is locked for this round

---

## Round Flow

| Phase | Duration | Details |
|:--|:--|:--|
| **Waiting** | — | Round starts when both sides have at least one bet |
| **Active** | 3 minutes | Betting closes 10 seconds before round ends |
| **Settlement** | Instant | Winner determined via VRF |
| **Payout** | Automatic | Winnings sent directly to your wallet |

You can add to your existing bet until betting closes (same side only).

---

## Betting Limits

| | |
|:--|:--|
| **Minimum Bet** | 0.01 SOL |
| **Maximum Bet** | 10 SOL per wallet |
| **Sides** | One side per wallet per round |

---

## Cancelled Rounds

Arena has automatic protections that may cancel a round:

| Condition | Trigger | Result |
|:--|:--|:--|
| One-Sided Timeout | 10 min with bets on only one side | Full refund |
| Lopsided Odds | Either side's odds drop to 1.1x or below | Full refund |

> All bets are fully refunded with no fees.

---

## Tips

| | |
|:--|:--|
| **Start small** | Get familiar with the platform before placing larger bets |
| **Watch first** | Observe a few rounds to understand the timing and flow |
| **Check balance** | Ensure you have enough SOL for your bet plus fees (~0.001 SOL) |
| **Verify outcomes** | Use the [Provably Fair](provably-fair.md) page to see how winners are determined |

---

## Troubleshooting

### Wallet won't connect

- Ensure your wallet extension is installed and unlocked
- Refresh the page
- Verify you're on Solana Mainnet
- Try a different supported wallet

### Sign-in rejected

- You must sign the verification message to use Arena
- This is a free signature that proves wallet ownership
- Try connecting again and approve the signature request

### Transaction failed

- Ensure you have enough SOL (bet amount + ~0.001 SOL for fees)
- Try again — network congestion can cause temporary failures
- Check your wallet for pending transactions

### Bet not showing

- Wait a few seconds for the transaction to confirm
- Refresh the page if needed
- Check your transaction on [Solscan](https://solscan.io)

### Session expired

- Sessions last 2 hours for security
- Reconnect your wallet to start a new session

---

<div align="center">

**Next:** [How It Works](how-it-works.md) — Game mechanics deep dive

<br />

<sub>Built on Solana</sub>

</div>