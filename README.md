# 🍪 Farcaster Mini App: Fortune Cookie (One-Page Example)

This is a simple **one-page Farcaster Mini App** that simulates a crypto fortune cookie experience. It's built with **plain HTML, CSS, and JavaScript** — no React, no frameworks — making it easy to understand, test, and remix.

---

## 🔮 What It Does

- Loads inside the Farcaster Mini App environment  
- Lets the user send a crypto transaction  
- After the “payment,” a randomly selected **fortune** and **lucky number** is revealed  
- Fully works inside the Farcaster Mini App preview tool (once hosted and configured correctly)

---

## 🛠️ Files Overview

- `index.html` – The **complete one-page app**, including all JavaScript and styles  
- `farcaster.json` – The **Mini App manifest**, used by Farcaster to identify and display your app  
- `assets/` – Icons, background images, or logos used in the app (optional)

---

## ✏️ What You Can Edit

### 1. 🪙 Wallet Address

Inside `index.html` (search for `"RECEIVING_ADDRESS"` in the JavaScript), find the transaction configuration:

```js
RECEIVING_ADDRESS: '0x1234567890ABCDEF...', // Replace with your actual wallet address
```

Replace with your preferred EVM-compatible wallet address.

---

### 2. 🔗 Chain Encoding

In the `farcaster.json` file, update the `requiredChains` field to match your target blockchain:

```json
"requiredChains": ["eip155:10143"]
```

This format uses [CAIP-2](https://github.com/ChainAgnostic/CAIPs/blob/main/CAIPs/caip-2.md):

- `eip155` = for EVM-based chains  
- `10143` = Chain ID (examples below)

| Chain        | Chain ID |
|--------------|----------|
| Ethereum     | `1`      |
| Base         | `8453`   |
| Optimism     | `10`     |
| Sepolia Testnet | `11155111` |

Find more at [chainlist.org](https://chainlist.org/).

---

### 3. 💸 Token Value (Quantity)

In the same `index.html` script, adjust the amount of tokens to send:

```js
value: ethers.utils.parseEther("0.001"), // Change to desired ETH/token amount
```

Set it to `"0.0"` for no-cost testing.

---

### 4. 🎨 Assets

Update URLs for the icon and splash image in `farcaster.json`:

```json
"iconUrl": "https://yourdomain.com/assets/icon.png",
"splashImageUrl": "https://yourdomain.com/assets/splash.png",
```

Ensure assets are:
- Hosted over HTTPS  
- Publicly accessible  
- Sized appropriately (e.g. 512x512px for icons)

---

## 🧪 How to Test It

### ✅ 1. Upload Files

Host your `index.html`, `farcaster.json`, and any `assets/` on a public domain or subpath, such as:

```
https://example.com/
```

### ✅ 2. Use the Farcaster Preview Tool

Go to:

```
https://miniapps.farcaster.xyz/preview?url=https://example.com/
```

You'll see how it loads inside Farcaster’s Mini App viewer.

---

## 📄 farcaster.json – Mini App Manifest

Must be placed **in the same path as your Mini App**, such as:

```
https://example.com/farcaster.json
```

Example:

```json
{
  "frame": {
    "version": "1",
    "name": "Fortune Cookie",
    "iconUrl": "https://example.com/icon.png",
    "homeUrl": "https://example.com/",
    "splashImageUrl": "https://example.com/splash.png",
    "splashBackgroundColor": "#FFF5CC",
    "subtitle": "Crack your crypto fortune",
    "description": "Send a tiny transaction to unlock your fortune!",
    "primaryCategory": "entertainment",
    "requiredChains": ["eip155:10143"],
    "requiredCapabilities": ["wallet.getEvmProvider"]
  }
}
```

---

## ✅ Verifying Ownership (Optional but Recommended)

To verify your domain and become eligible for rewards:

1. Add a second manifest file here:

```
https://example.com/.well-known/farcaster.json
```

2. It must contain a valid **accountAssociation** object with:

```json
{
  "accountAssociation": {
    "header": "...",
    "payload": "...",
    "signature": "..."
  }
}
```

Generate this using [the Farcaster Manifest Tool](https://miniapps.farcaster.xyz/manifest-tool).

---

## 🚀 Registering Your Mini App

Once hosted and tested:

1. Go to: [https://explorer.farcaster.xyz/mini-apps](https://explorer.farcaster.xyz/mini-apps)
2. Click “Submit Mini App”
3. Enter:
   - App Name  
   - Hosted App URL (e.g. `https://example.com/`)  
   - Manifest URL (same path + `/farcaster.json`)  
   - FID if verified

Once approved, it can be embedded or shared on Warpcast and other clients.

---

## 📢 Sharing Your App

You can share it using:

```
https://miniapps.farcaster.xyz/app?url=https://example.com/
```

Or integrate it into a Farcaster Frame or post on Warpcast.

---

## 👨‍💻 Remix and Extend

This project is intentionally:

- ✅ Lightweight  
- ✅ Educational  
- ✅ Ready for remixing

Fork it, extend it, or build your own flow with Farcaster Mini App SDKs.

If you create something cool, share it with @twoguysonecat or the Farcaster dev community!

---

## 🧠 Credits

- Powered by [ethers.js](https://docs.ethers.org/)
- Built for [Farcaster Mini Apps](https://miniapps.farcaster.xyz/)
- Designed with simplicity in mind
- By TwoGuysOneCat (https://www.twoguysonecat.com)
