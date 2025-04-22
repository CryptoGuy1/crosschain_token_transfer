---

```markdown
# 🚀 Cross-Chain USDC Transfer using Chainlink CCIP

This project demonstrates how to perform cross-chain USDC token transfers from **Avalanche Fuji** to **Ethereum Sepolia** using [Chainlink CCIP (Cross-Chain Interoperability Protocol)](https://docs.chain.link/ccip), with integration support via the [Chainlink Transporter App](https://transporter.chain.link/) and [Snowtrace](https://testnet.snowtrace.io/) for transaction tracking.

> ⚠️ This code is for **educational and experimental purposes** only. Do not use in production environments.

---

## 🔗 Tech Stack

- **Solidity v0.8.19**
- **Chainlink CCIP** (Token Transfer)
- **USDC** on Avalanche Fuji Testnet
- **LINK** (Fee token)
- **Chainlink Transporter App** – UI to monitor/execute CCIP transfers
- **Snowtrace** – Block explorer for Avalanche Fuji

---

## 📦 Contract Summary

### `TransferUSDCBasic.sol`

A simple contract that:

- Transfers **USDC** tokens from Avalanche Fuji to Ethereum Sepolia via CCIP.
- Pays the required **CCIP fee in LINK**.
- Validates user balances and approvals before sending.
- Emits events to track successful cross-chain messages.

---

## 🌍 Supported Networks

| Network           | Role        | Details                                                                 |
|------------------|-------------|-------------------------------------------------------------------------|
| Avalanche Fuji   | Source chain| CCIP Router Address: `0xF694E193200268f9a4868e4Aa017A0118C9a8177`       |
| Ethereum Sepolia | Target chain| Chain Selector: `16015286601757825753`                                 |
| LINK (Fuji)      | Fee token   | `0x0b9d5D9136855f6FEc3c0993feE6E9CE8a297846`                             |
| USDC (Fuji)      | Token       | `0x5425890298aed601595a70AB815c96711a31Bc65`                             |

---

## 🧪 How to Use

### 1. **Install Dependencies**

```bash
npm install
```

### 2. **Compile Contracts**

```bash
npx hardhat compile
```

### 3. **Deploy to Fuji**

Ensure you have:
- A funded wallet with Fuji AVAX + LINK
- RPC URL and private key in `.env`

```bash
npx hardhat run scripts/deploy.js --network fuji
```

### 4. **Approve USDC to Contract**

Before calling `transferUsdcToSepolia`, approve the contract to transfer your USDC:

```solidity
usdcToken.approve(<contractAddress>, amount);
```

Or interact via Remix / frontend interface.

### 5. **Initiate Cross-Chain Transfer**

Call:

```solidity
transferUsdcToSepolia(receiver, amount)
```

- Ensure the contract has enough LINK to cover CCIP fees.
- Track emitted `UsdcTransferred` events.

---

## 🔍 Track the Transfer

### 🔗 [Chainlink Transporter App](https://transporter.chain.link/)

- Use the message ID emitted by `UsdcTransferred` to monitor delivery.
- Track gas usage, logs, and success/failure status.

### 🔎 [Snowtrace](https://testnet.snowtrace.io/)

- View the Avalanche Fuji transaction hash.
- Monitor LINK and USDC token balances on-chain.

---

## 🛠 Developer Utilities

- `allowanceUsdc()` – View how much USDC you've approved to the contract
- `balancesOf(address)` – View LINK + USDC balances
- `withdrawToken(address, token)` – Owner-only emergency withdrawal

---

## 🧠 Learn More

- [Chainlink CCIP Documentation](https://docs.chain.link/ccip)
- [Transporter UI Guide](https://docs.chain.link/ccip/transporter/introduction)
- [Fuji LINK Faucet](https://faucets.chain.link/fuji)
- [Snowtrace](https://testnet.snowtrace.io/)

---

## 🙏 Credits

Built as part of a cross-chain development exercise exploring real-world CCIP usage for secure token transfer workflows.

---

## 📜 License

MIT © 2025
```

---

