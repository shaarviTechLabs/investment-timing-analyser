# 📊 Groww Investment Timing Analyser

> **Did you buy your mutual funds at the right time?**  
> Upload your Groww files and find out — using real historical NAV data.

![Tool Preview](https://img.shields.io/badge/Works%20In-Browser-blue?style=flat-square) ![No Server](https://img.shields.io/badge/No%20Server-100%25%20Local-green?style=flat-square) ![Data Source](https://img.shields.io/badge/NAV%20Data-MFAPI.in-orange?style=flat-square) ![Free](https://img.shields.io/badge/Cost-Free-brightgreen?style=flat-square)

---

## 🔍 What Does This Tool Do?

This tool analyses whether you bought your mutual funds at the **optimal time** by comparing your actual purchase NAV against the NAV available in a **±90 day window** around your purchase date.

For each of your purchases it tells you:

- ✅ Your exact purchase NAV (read directly from your Groww order history)
- 📉 The **lowest NAV available** in the ±90 day window — what you *could* have paid
- 📈 The **highest NAV** in the window — what you luckily avoided
- 🔢 How many **extra units** you would have received if you had bought at the lowest point
- 💰 The **extra profit in ₹** those units would be worth today
- 🏆 A **Timing Score (0–100%)** — how close to optimal your purchase was
- 📊 A **visual NAV chart** showing your purchase date vs the optimal entry point

---

## 🚀 How To Use

### Step 1 — Download your files from Groww

You need **two Excel files** from Groww. Both are free to download:

**File 1 — Holdings Statement**
1. Open Groww app → tap your **Profile icon** (top right)
2. Go to **Reports** → **Holdings Statement**
3. Select **Excel (.xlsx)** → Download
4. File will be named like: `Holdings_Statement_2026-03-15.xlsx`

**File 2 — Order History**
1. Open Groww app → tap your **Profile icon**
2. Go to **Reports** → **Mutual Funds Order History**
3. Select a date range (e.g. last 1–2 years) → **Excel** → Download
4. File will be named like: `Mutual_Funds_Order_History_2025-04-01_2026-03-31.xlsx`

### Step 2 — Open the tool

👉 **[Open the tool here](https://yourusername.github.io/groww-timing-analyser)**

*(Replace the link above with your own GitHub Pages URL after deployment)*

### Step 3 — Upload and analyse

1. Drop your **Holdings Statement** in the left box
2. Drop your **Order History** in the right box
3. The tool automatically detects all your purchase transactions
4. Click **"Analyse My Investment Timing"**
5. Results appear within a few seconds — one card per purchase transaction

---

## 📋 Understanding Your Results

### Timing Score
| Score | Verdict | Meaning |
|-------|---------|---------|
| 75–100% | 🟢 Excellent Timing | You bought very close to the window low |
| 40–74% | 🟡 Decent Timing | Reasonable entry, minor improvement possible |
| 0–39% | 🔴 Could Be Better | Significantly cheaper NAV was available nearby |

### Key Metrics Per Fund

| Metric | What It Means |
|--------|--------------|
| **Your NAV** | The exact NAV at which you purchased, from your Groww order |
| **Window Low** | The cheapest NAV available in ±90 days around your purchase |
| **Window High** | The most expensive NAV in the window (what you avoided) |
| **Units at Low** | How many units ₹ same money would have bought at the window low |
| **Missed Profit** | Extra value today if you had bought at the window low |

### What-if Scenario
Each fund card shows a **What-if box** — if you had bought on the best day in the window:
- How many extra units you would hold today
- What those extra units are worth at today's NAV

---

## 🔒 Privacy & Data Security

**Your data never leaves your device.**

- Both Excel files are parsed **entirely in your browser** using JavaScript
- No file contents are uploaded to any server
- The only external call made is to **[MFAPI.in](https://mfapi.in)** — a free public API that returns historical NAV data for Indian mutual funds
- MFAPI only receives the fund's scheme code (a number) — never your personal data

---

## ⚙️ How It Works (Technical)

```
Your Groww Files (local)
        │
        ▼
  Browser parses Excel files
  (SheetJS / xlsx.js library)
        │
        ├─ Holdings file  → which funds you currently hold
        └─ Order history  → purchase date, NAV, amount, units
                │
                ▼
        Cross-reference:
        Keep only PURCHASE transactions
        for currently-held, net-positive funds
                │
                ▼
        For each purchase → fetch full NAV history
        from api.mfapi.in/mf/{schemeCode}
                │
                ▼
        Analyse ±90 day window:
        min NAV, max NAV, timing score,
        extra units, missed profit
                │
                ▼
        Render results with
        charts + insights
```

### Technologies Used
- Pure HTML + CSS + JavaScript (no framework, no build step)
- [SheetJS (xlsx.js)](https://sheetjs.com/) — for reading Excel files in the browser
- [MFAPI.in](https://mfapi.in) — free public API for Indian mutual fund historical NAV data

---

## ⚠️ Important Disclaimers

- **This tool is for educational and informational purposes only.** It does not constitute financial advice.
- Mutual fund NAV is published **once per day** after market close (~6–9 PM IST). This is not intraday pricing.
- Hindsight analysis is not a guarantee of future performance. Markets are unpredictable.
- "Optimal timing" in this tool means the lowest NAV in a ±90 day window — this is a simplified metric and does not account for SIP averaging, tax implications, or long-term investment strategy.
- The tool works best for **lump sum purchases**. SIP investments are better evaluated differently.

---

## 🇮🇳 Supported Funds

This tool works with **all AMFI-registered Indian mutual funds** available on Groww, including:

- Equity funds (Large Cap, Mid Cap, Small Cap, Flexi Cap, ELSS)
- Debt funds
- Hybrid funds
- Gold / Commodity funds (ETF FoFs)
- Index funds

---

## 🐛 Known Limitations

- Funds purchased **more than ~5 years ago** may not have sufficient historical data on MFAPI
- If MFAPI cannot match a fund name, the fund will be marked as **Skipped** with a reason shown
- The tool requires an **active internet connection** to fetch NAV data from MFAPI
- Works best in **Chrome, Edge, or Firefox**. Safari on older iOS may block cross-origin API calls.

---

## 📁 Repository Structure

```
/
├── index.html       ← The entire tool (single file, open in browser)
└── README.md        ← This file
```

---

## 🤝 Contributing

Feel free to open an issue or pull request if you:
- Find a bug
- Want to add support for stocks or ETFs
- Want to add SIP-specific analysis
- Have suggestions for new metrics

---

## 📄 License

MIT License — free to use, modify, and share.

---

*Built with ❤️ for Indian retail investors. Data powered by [MFAPI.in](https://mfapi.in).*

