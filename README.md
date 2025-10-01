# Magic Eden Bitcoin Auto-Minter

A fully automated Bitcoin Launchpad minter for [Magic Eden](https://magiceden.io/).  
This tool is designed to run on **Windows** and lets you schedule and auto-execute Bitcoin Ordinals mints as soon as the phase opens.

---

## ✨ Features
- 🔗 Accepts any **Magic Eden Launchpad BTC mint link** (or slug).
- ⏱ Fetches and tracks the official **launch start time** via Magic Eden’s APIs.
- ⚡ Automatically executes the mint the moment the phase opens.
- 🔑 Uses your **WIF private key** to sign locally (you stay in control of your wallet).
- 📝 Submits the signed PSBT back to Magic Eden for confirmation.
- 🛠 Written as a **standalone Node.js CLI tool** (no extra wallet extensions required).
- ✅ Fully tested on **Windows 10/11**.

---

## 📦 Requirements
- [Node.js](https://nodejs.org/) (>= 18.x)
- NPM (ships with Node)
- A funded **Bitcoin wallet private key (WIF format)**

---

## 🚀 Installation
Clone this repository and install dependencies:

```bash
git clone https://github.com/yourusername/magiceden-btc-auto-minter.git
cd magiceden-btc-auto-minter
npm install
```

---

## ⚙️ Configuration

You’ll need:

- Magic Eden Launchpad link (example:  
  `https://magiceden.io/ordinals/launchpad/stars`)
- Your Bitcoin private key (WIF format) — this is used to sign the PSBT.
- (Optional) An API key if you want higher rate limits on Magic Eden.

Create a `.env` file in the repo root:

```
WIF=your_private_key_here
API_KEY=your_magiceden_api_key_optional
```

---

## ▶️ Usage

Run the script with the launchpad link:

```bash
node index.js https://magiceden.io/ordinals/launchpad/stars
```

The script will:

1. Query Magic Eden’s API for the project metadata.
2. Detect the start time for the mint phase.
3. Wait until the mint opens.
4. Request an unsigned PSBT.
5. Sign it locally with your WIF key.
6. Submit the signed transaction back to Magic Eden.

You’ll see logs like:

```
[INFO] Fetching launchpad details...
[INFO] Mint scheduled at 2025-10-05T18:00:00Z
[WAITING] 2m 14s until mint...
[INFO] PSBT received, signing...
[SUCCESS] Transaction submitted! TXID: abc123...
```

---

## 🛡️ Security Notes

- Your private key never leaves your machine. Signing happens locally.
- Always use a dedicated wallet for minting (do not expose your main holdings).
- This script is experimental — use at your own risk.

---

## 🗂 Repo Structure

```
magiceden-btc-auto-minter/
│
├── index.js        # Main CLI script
├── api.js          # API helper functions
├── signer.js       # PSBT signing logic
├── utils.js        # Countdown / time helpers
├── package.json    # Dependencies
├── .env.example    # Example config
└── README.md       # You are here
```

---

## 🤝 Contributing

PRs and issues are welcome. Please fork and submit improvements.

---

## 📜 License

This project is licensed under the MIT License.

---

## ⚠️ Disclaimer

This software is provided as-is without warranty.  
Magic Eden may change their API or minting process at any time, which could break functionality.  
Use responsibly and only with funds you are willing to risk.
