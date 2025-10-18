# 🛍️ Merchandise NFT Marketplace

A lightweight, efficient NFT marketplace specifically designed for physical goods and merchandise. Built with Solidity and optimized for low gas costs.

<img width="1710" height="888" alt="Screenshot 2025-10-18 at 12 47 45 PM" src="https://github.com/user-attachments/assets/a78f150e-f760-4cda-ae4e-e506f990604f" />

## 📋 Overview

This smart contract enables creators to mint NFTs representing physical merchandise, list them for sale, and handle secure transactions with automatic payment distribution and platform fees.

## 🔗 Contract Details

**Contract Address:** `0xd1093124BE7F81119d07539C04608db148d7E0cE`

**Network:** [Specify your network - e.g., Ethereum Mainnet, Polygon, etc.]

**Contract Name:** SimpleMerchNFT

**Token Symbol:** MERCH

## ✨ Features

- 🎨 **Easy NFT Minting** - Create NFTs for physical goods with metadata
- 💰 **Built-in Marketplace** - List, unlist, and sell items directly
- 🔒 **Secure Transactions** - Automatic payment splitting and refunds
- 💸 **Platform Fees** - Configurable marketplace commission (default 2.5%)
- ⚡ **Gas Optimized** - Lightweight contract for lower transaction costs
- 🛡️ **OpenZeppelin Standards** - Built on battle-tested, secure libraries

## 🚀 Quick Start

### For Sellers

1. **Mint your merchandise NFT:**
   ```solidity
   mint(tokenURI, priceInWei)
   ```
   - `tokenURI`: IPFS or HTTP link to your item's metadata (image, description)
   - `priceInWei`: Listing price in wei

2. **Manage your listings:**
   ```solidity
   list(tokenId, newPrice)  // Update price or relist
   unlist(tokenId)          // Remove from marketplace
   ```

### For Buyers

1. **Purchase an item:**
   ```solidity
   buy(tokenId) payable
   ```
   - Send exact amount or more (excess will be refunded)
   - NFT transfers to you automatically
   - Payment splits between seller and platform

## 📦 Contract Functions

### Public Functions

| Function | Description | Parameters |
|----------|-------------|------------|
| `mint()` | Create new merchandise NFT | `uri` (string), `price` (uint256) |
| `buy()` | Purchase listed NFT | `tokenId` (uint256) |
| `list()` | List NFT for sale | `tokenId` (uint256), `price` (uint256) |
| `unlist()` | Remove NFT from marketplace | `tokenId` (uint256) |
| `tokenURI()` | Get token metadata URI | `tokenId` (uint256) |

### View Functions

| Function | Description | Returns |
|----------|-------------|---------|
| `items()` | Get item details | Price, seller, sale status |
| `platformFee()` | Get current platform fee | Fee in basis points (250 = 2.5%) |

### Owner Functions

| Function | Description | Access |
|----------|-------------|--------|
| `setPlatformFee()` | Update marketplace fee | Owner only |

## 💡 Usage Examples

### Minting an NFT

```javascript
// Using ethers.js
const uri = "ipfs://QmYourMetadataHash";
const price = ethers.utils.parseEther("0.1"); // 0.1 ETH

const tx = await contract.mint(uri, price);
await tx.wait();
```

### Buying an NFT

```javascript
const tokenId = 1;
const itemPrice = await contract.items(tokenId).price;

const tx = await contract.buy(tokenId, { value: itemPrice });
await tx.wait();
```

### Listing an NFT

```javascript
const tokenId = 1;
const newPrice = ethers.utils.parseEther("0.2");

const tx = await contract.list(tokenId, newPrice);
await tx.wait();
```

## 🎨 Metadata Format

Your token URI should point to a JSON file with this structure:

```json
{
  "name": "Cool T-Shirt",
  "description": "Limited edition merchandise",
  "image": "ipfs://QmImageHash",
  "attributes": [
    {
      "trait_type": "Category",
      "value": "Apparel"
    },
    {
      "trait_type": "Size",
      "value": "Large"
    }
  ]
}
```

## 🔐 Security

- ✅ Built with OpenZeppelin contracts
- ✅ Reentrancy protection via CEI pattern
- ✅ Owner-only administrative functions
- ✅ Input validation on all functions
- ✅ Automatic refund for overpayment

## 📊 Platform Economics

- **Platform Fee:** 2.5% (250 basis points)
- **Seller Receives:** 97.5% of sale price
- **Buyer Pays:** Listed price (no hidden fees)

## 🛠️ Development

### Prerequisites

```bash
npm install @openzeppelin/contracts
```

### Deployment

```bash
# Using Hardhat
npx hardhat run scripts/deploy.js --network <your-network>

# Using Foundry
forge create SimpleMerchNFT --rpc-url <RPC_URL> --private-key <PRIVATE_KEY>
```

## 📝 License

MIT License - see LICENSE file for details

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## 📞 Support

- **Issues:** [GitHub Issues](https://github.com/your-repo/issues)
- **Documentation:** [Full Docs](https://your-docs-url.com)
- **Community:** [Discord/Telegram Link]

## ⚠️ Disclaimer

This smart contract is provided as-is. Always conduct thorough testing and audits before deploying to mainnet. Use at your own risk.

---

**Built with ❤️ for the Web3 community**

![Footer](https://via.placeholder.com/1200x200/6366f1/ffffff?text=Secure+•+Simple+•+Efficient)
