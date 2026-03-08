<p align="center">
  <img src="https://files.catbox.moe/j79uqp.png" alt="GasBorrow Logo" width="120"/>
</p>

<h1 align="center">GasBorrow Protocol</h1>

<p align="center">
  <b>Decentralized MON gas lending protocol on Monad Network</b><br/>
  Lenders earn yield · Borrowers get MON for gas · Owner earns fees
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Network-Monad%20Mainnet-7B5BF5?style=for-the-badge&logo=ethereum"/>
  <img src="https://img.shields.io/badge/Chain%20ID-143-00E5FF?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Lender%20APY-5%25-00FFA3?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Borrow%20APR-10%25-FF3CAC?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Built%20With-Solidity%200.8.20-363636?style=for-the-badge&logo=solidity"/>
</p>

<p align="center">
  <a href="https://explorer.monad.xyz/address/0xB1D6424336820D11Ba1053fE313101e4B45FE620">
    <img src="https://img.shields.io/badge/Contract-0xB1D642...E620-1a2540?style=for-the-badge"/>
  </a>
</p>

---

## 🌐 Live App

> Open `index.html` in your browser and connect MetaMask or NEAR Wallet

**Contract:** [`0xB1D6424336820D11Ba1053fE313101e4B45FE620`](https://explorer.monad.xyz/address/0xB1D6424336820D11Ba1053fE313101e4B45FE620)  
**Owner:** `0x592B35c8917eD36c39Ef73D0F5e92B0173560b2e`  
**Network:** Monad Mainnet · Chain ID 143

---

## 💰 How It Works

| Role | Action | Earn |
|---|---|---|
| **Lender** | Deposit MON | 5% APY annual |
| **Borrower** | Post 150% collateral | Borrow MON for gas |
| **Liquidator** | Liquidate bad loans | 5% of collateral |
| **Owner** | Protocol fees | 1% origination + 5% spread |

---

## ⚡ Protocol Functions

### For Lenders
- `deposit()` — Deposit MON, receive shares, earn 5% APY
- `withdraw(shares)` — Burn shares, receive MON + yield

### For Borrowers
- `borrow(amount)` — Send 150% collateral, borrow MON (1% fee)
- `repay()` — Repay principal + 10% annual interest, get collateral back

### For Anyone
- `liquidate(address)` — Liquidate undercollateralized loans, earn 5% bonus

### For Owner Only
- `withdrawFees()` — Pull all protocol fees to owner wallet
- `pause()` / `unpause()` — Emergency stop
- `emergencyWithdraw()` — Withdraw all funds

---

## 🔐 Security Features

- `ReentrancyGuard` on all fund-moving functions
- `Ownable` — only owner can withdraw fees or change config
- `Pausable` — emergency stop mechanism
- Share-based lender accounting (cToken style) — no insolvency
- 150% collateral ratio protection
- Minimum interest (0.1%) to prevent flash-loan abuse
- 365-day max loan duration

---

## 📊 Protocol Config

| Parameter | Value |
|---|---|
| Origination Fee | 1% (instant per borrow) |
| Borrower Rate | 10% annual |
| Lender Rate | 5% annual |
| Protocol Spread | 5% annual profit |
| Collateral Ratio | 150% |
| Liquidation Threshold | 120% |
| Liquidation Fee | 2% to protocol |
| Liquidation Bonus | 5% to caller |
| Max Loan Duration | 365 days |

---

## 🚀 Setup & Deploy

### Requirements
- [Foundry](https://foundry.paradigm.xyz)
- OpenZeppelin Contracts

### Install
```bash
git clone https://github.com/YOURUSERNAME/gasborrow.git
cd gasborrow
forge install OpenZeppelin/openzeppelin-contracts
```

### Build & Test
```bash
forge build
forge test -v
```

### Deploy to Monad
```bash
export PRIVATE_KEY="your_private_key"
export RPC_URL="https://rpc.monad.xyz"

forge script script/Deploy.s.sol:DeployGasBorrow \
  --rpc-url $RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast \
  --legacy \
  -vvvv
```

### Verify on Explorer
```bash
forge verify-contract \
  --rpc-url https://rpc.monad.xyz \
  --verifier sourcify \
  --verifier-url 'https://sourcify-api-monad.blockvision.org/' \
  --chain-id 143 \
  0xB1D6424336820D11Ba1053fE313101e4B45FE620 \
  src/GasBorrow.sol:GasBorrow
```

---

## 🔗 Links

- **Explorer:** [explorer.monad.xyz](https://explorer.monad.xyz/address/0xB1D6424336820D11Ba1053fE313101e4B45FE620)
- **Monad Network:** [monad.xyz](https://monad.xyz)
- **NEAR Wallet:** [senderwallet.io](https://senderwallet.io)
- **Token Bridge:** [rainbowbridge.app](https://rainbowbridge.app)

---

## ⚠️ Disclaimer

This protocol is provided as-is. Always audit smart contracts before depositing significant funds. The owner holds admin keys — use at your own risk.

---

<p align="center">Built with ❤️ on <b>Monad Network</b></p>
