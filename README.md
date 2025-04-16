# 🚀 PumpSwap Volume Generator Bot

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Solana](https://img.shields.io/badge/Solana-362783?style=flat&logo=solana&logoColor=white)
![Version](https://img.shields.io/badge/version-1.2.0-blue)

A high-performance, multi-pool trading bot designed to generate volume on PumpSwap and Raydium protocols. This tool supports both traditional OpenBook markets and the newer CPMM pools, with special optimization for PumpSwap pools.

## 📑 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Advanced Features](#advanced-features)
- [Common Issues & Troubleshooting](#common-issues--troubleshooting)
- [Performance Optimization](#performance-optimization)
- [Contributing](#contributing)
- [License](#license)
- [Disclaimer](#disclaimer)

## 🔍 Overview

This bot creates legitimate trading volume on PumpSwap and Raydium pools through a series of automated buy and sell transactions. It uses ephemeral wallets and Jito bundles to execute transactions efficiently, supporting multiple DEX protocols including:

- PumpSwap (Primary focus)
- Raydium CPMM pools
- Raydium OpenBook markets

Whether you're a token developer looking to increase visibility or a market maker supporting new projects, this tool provides a customizable and efficient solution for generating sustainable trading volume.

## ✨ Features

- **Multi-Protocol Support**: Works with PumpSwap, Raydium CPMM, and OpenBook markets
- **Transaction Bundling**: Uses Jito for efficient transaction bundling
- **Volume Customization**: Set minimum and maximum transaction amounts
- **Concurrency Control**: Run multiple wallet transactions per bundle
- **Token-2022 Compatible**: Full support for Token-2022 standard tokens
- **Auto Token Detection**: Automatically identifies token program (SPL/Token-2022)
- **USD Volume Estimation**: Real-time calculation of expected USD volume
- **Error Handling**: Comprehensive error logging and retry mechanisms
- **Randomized Amounts**: Natural-looking volume with randomized transaction sizes

## 🔄 How It Works

The bot creates a series of ephemeral Solana wallets, funds them, and then executes paired buy and sell transactions on your chosen pool:

1. **Setup Phase**: Generates ephemeral wallets and prepares Jito tips
2. **Pool Detection**: Automatically identifies whether the pool is PumpSwap, CPMM, or OpenBook
3. **Transaction Bundling**: Groups transactions for efficient processing
4. **Volume Generation**: Executes buy and sell transactions with randomized amounts
5. **Cleanup**: Returns remaining funds to the main wallet

Each cycle can include multiple wallets executing transactions simultaneously, creating natural-looking trading patterns that benefit token visibility.

## 🛠️ Prerequisites

- Node.js v16+ 
- Solana CLI (for wallet management)
- At least 1 SOL for initial funding (more recommended for higher volume)
- Jito bundles access
- A configured `.env` file (see Configuration section)

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/pumpswap-volume-bot.git
cd pumpswap-volume-bot

# Install dependencies
npm install

# Set up your environment variables
cp .env.example .env
# Edit .env with your wallet path and other configuration
```

## 🚀 Usage for PumpSwap Volume Generation

To run the PumpSwap Volume Generator Bot and start creating trading volume on PumpSwap:

# Start the PumpSwap volume bot with the main interface
npm start

# Or run the PumpSwap volume extender function directly
node src/extender.js

When prompted in the PumpSwap volume generation interface:
1. Select "y" to target PumpSwap for volume generation
2. Enter your token mint address to generate volume on the specific PumpSwap pool
3. Set the number of wallets per bundle (1-4 recommended) for parallel PumpSwap volume
4. Define how many PumpSwap volume bundles to perform (higher = more total volume)
5. Set min/max transaction amounts in SOL to control PumpSwap volume size
6. Configure delay between PumpSwap volume cycles
7. Set Jito tip amount for reliable PumpSwap volume transaction processing

Example PumpSwap volume generation session:

Is it PumpSwap?: y
Enter your TOKEN mint for PumpSwap volume: 7xKXtg2CW87d97TXJSDpbD5jBkheTqA83TZRuJosgAsU
Number of wallets per PumpSwap volume bundle (max. 4): 2
Number of PumpSwap volume bundles to perform (Ex. 50): 25
Minimum random amount for PumpSwap volume (in SOL): 0.05
Maximum random amount for PumpSwap volume (in SOL): 0.15
Delay between PumpSwap volume cycles in seconds (Ex. 3): 3
Jito tip for PumpSwap volume transactions in Sol (Ex. 0.001): 0.001

## ⚙️ Configuration for PumpSwap Volume Bot

Create a `.env` file with the following variables to optimize your PumpSwap volume generation:

# Required for PumpSwap volume generation
WALLET_PATH=/path/to/your/wallet.json
RPC_URL=https://your-rpc-provider.com

# Optional PumpSwap volume settings
DEBUG=false
JITO_AUTH_KEY=your_jito_auth_key

## 🔧 Advanced PumpSwap Volume Features

### Multiple DEX Support for Volume Generation

The PumpSwap volume bot intelligently detects which DEX type you're using:

- For PumpSwap volume: Provide the token mint address
- For Raydium CPMM volume: Provide the pool ID 
- For OpenBook volume: Provide the market ID

### Token-2022 Handling in PumpSwap Volume Generation

The PumpSwap volume system includes special handling for Token-2022 tokens:

// The PumpSwap volume bot automatically detects Token-2022 tokens and adjusts closing behavior
if (tokenProgramId.equals(spl.TOKEN_2022_PROGRAM_ID)) {
   // Special handling for Token-2022 in PumpSwap volume
   console.log("Token-2022 detected - skipping account closing");
} else {
   // Regular token closing in PumpSwap volume
   closeTokenAccountIx = spl.createCloseAccountInstruction(...);
}

### Custom PumpSwap Volume Patterns

To create more natural PumpSwap trading volume patterns, adjust these parameters:

- Small, frequent PumpSwap volume trades: Low amounts, high bundle count
- Large, infrequent PumpSwap volume trades: Higher amounts, lower bundle count
- Mixed PumpSwap volume pattern: Wide min/max range, moderate bundle count

## 🛑 Common PumpSwap Volume Issues & Troubleshooting

### PumpSwap Volume Transaction Errors

If you see PumpSwap volume transaction errors:

1. Check your RPC provider's rate limits for PumpSwap volume generation
2. Ensure you have sufficient SOL for all PumpSwap volume transactions
3. Verify the PumpSwap pool or market ID exists
4. For Token-2022 tokens on PumpSwap, ensure you've updated to the latest SPL library

### PumpSwap Volume Bundle Dropped Errors

When seeing "Bundle Dropped, no connected leader up soon" during PumpSwap volume generation:

1. Increase your Jito tip amount for PumpSwap volume transactions
2. Reduce the number of wallets per PumpSwap volume bundle
3. Check Jito network status before generating PumpSwap volume

## ⚡ PumpSwap Volume Performance Optimization

For maximum PumpSwap volume performance:

1. Use a premium RPC provider for PumpSwap volume generation
2. Limit PumpSwap volume bundles to 2-3 wallets for best reliability
3. Set reasonable delays between PumpSwap volume cycles (3-5 seconds)
4. Increase Jito tips during high network congestion for reliable PumpSwap volume

## 🤝 Contributing to the PumpSwap Volume Bot

Contributions to improve PumpSwap volume generation are welcome! Please feel free to submit a Pull Request.

1. Fork the PumpSwap volume repository
2. Create your feature branch for PumpSwap volume improvements (git checkout -b feature/amazing-pumpswap-feature)
3. Commit your PumpSwap volume changes (git commit -m 'Add some amazing PumpSwap volume feature')
4. Push to the branch (git push origin feature/amazing-pumpswap-feature)
5. Open a Pull Request for your PumpSwap volume enhancements

## 📄 License for PumpSwap Volume Bot

This PumpSwap volume project is licensed under the MIT License - see the LICENSE file for details.

## ⚠️ PumpSwap Volume Bot Disclaimer

This PumpSwap volume tool is designed for legitimate market making and liquidity provision. Users generating PumpSwap volume should:

1. Ensure compliance with all applicable laws and regulations when generating PumpSwap volume
2. Understand PumpSwap protocol rules and guidelines for volume generation
3. Use responsibly to support project growth rather than manipulation of PumpSwap markets
4. Be aware that improper use of PumpSwap volume generation could violate exchange terms of service

THE PUMPSWAP VOLUME SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED.
