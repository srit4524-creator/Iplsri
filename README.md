# 🏏 IPL Auction System — Setup Guide

## Project Structure
```
ipl-auction/
├── host.html       ← Auctioneer screen (your laptop)
├── stage.html      ← TV broadcast screen (big display)
├── team.html       ← Friends' phones for bidding
├── css/style.css   ← All styles
└── js/players.js   ← 30 players + 10 teams data
```

---

## Step 1 — Firebase Setup (5 minutes)

1. Go to **https://console.firebase.google.com**
2. Click **"Add project"** → name it `ipl-auction` → Continue
3. Disable Google Analytics → Create project
4. In left sidebar: **Build → Realtime Database**
5. Click **"Create Database"** → choose your region → **"Start in test mode"** → Enable
6. In left sidebar: **Project Settings** (gear icon) → **"Your apps"** → click `</>` (Web)
7. Register app name → copy the `firebaseConfig` object

Your config looks like:
```js
{
  apiKey: "AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  authDomain: "ipl-auction-xxxxx.firebaseapp.com",
  databaseURL: "https://ipl-auction-xxxxx-default-rtdb.firebaseio.com",
  projectId: "ipl-auction-xxxxx"
}
```

---

## Step 2 — Deploy to Netlify (free, 2 minutes)

1. Go to **https://app.netlify.com** → Sign up free
2. Drag and drop the entire `ipl-auction/` folder onto the Netlify dashboard
3. You'll get a URL like: `https://random-name-123.netlify.app`

---

## Step 3 — Run the Auction

| Device | URL |
|--------|-----|
| 🖥️ Host Laptop | `https://your-site.netlify.app/host.html` |
| 📺 Stage / TV | `https://your-site.netlify.app/stage.html` |
| 📱 Friends' Phones | `https://your-site.netlify.app/team.html` |

All 3 screens enter the **same Firebase credentials** — they'll all sync in real-time.

---

## Step 4 — Add Player Photos (optional)

Create folder: `images/players/`

Name photos exactly like:
```
virat_kohli.png
rohit_sharma.png
ms_dhoni.png
jasprit_bumrah.png
... (lowercase, spaces → underscores)
```

If no image found, it automatically shows a colored role icon.

---

## Auction Flow

```
1. Host opens host.html → enters Firebase config → LAUNCH AUCTION
2. Stage opens stage.html → enters config → CONNECT
3. Friends open team.html → enter config → JOIN AUCTION → Select Team
4. Host clicks ▶ NEXT PLAYER → random player appears on all screens
5. Friends tap BID → price goes up live on all screens
6. Timer counts down (30 seconds)
7. Host clicks 🔨 SELL PLAYER → SOLD! animation plays on all screens
8. Purse deducted from winning team automatically
9. Repeat!
```

---

## Features

- ✅ 30 real IPL players with roles & stats
- ✅ 10 IPL teams — one per friend, exclusive selection
- ✅ ₹80 Crore purse per team, auto-deducted on purchase
- ✅ 30-second countdown timer
- ✅ SOLD! animation with confetti on stage screen
- ✅ Real-time sync across all devices via Firebase
- ✅ Sold players ticker on stage screen
- ✅ My Squad tracker on team screen
- ✅ UNSOLD button for host
- ✅ Add player photos anytime — just drop in images/players/
