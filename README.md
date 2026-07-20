<p align="center"><img src="icon.svg" alt="Giveaway Roulette" width="88"></p>

# 🎡 Giveaway Roulette — for Twitch (v1.2)

A live giveaway picker for Twitch streams. Viewers type **`!join`** in chat and a sideways‑scrolling roulette picks the winner — with rewards, prize images, weighted odds, a countdown, an "Entries Open" banner, and automatic chat announcements.

**No install.** It runs entirely as OBS browser sources from a hosted page.

## 📖 Full setup guide (share this with people)
👉 **https://abdulazizjhk.github.io/giveaway-wheel/guide.html**

## Quick start
Add two browser sources in OBS (same page, two views):

| | URL |
|---|---|
| **On stream** (Browser Source, 1920×1080) | `https://abdulazizjhk.github.io/giveaway-wheel/wheel.html?view=stage` |
| **Your controls** (Docks → Custom Browser Docks) | `https://abdulazizjhk.github.io/giveaway-wheel/wheel.html?view=dock` |

Then in the dock: enter your channel → **Connect** → set a timer → **Open Entries**. Viewers `!join`; when the timer ends it auto‑spins and reveals the winner.

> **Stuck on an old version?** Re-copy the **On stream** URL with the **🔗 Copy source URL** button in the dock — it stamps the current version (e.g. `?view=stage&v=1.1`) so the pasted URL bypasses OBS's cache. You can also right‑click the source → Refresh, or manually bump the `&v=` number.

## Features
- `!join` chat entries (anonymous read — no login) · weighted odds · sub/VIP/mod‑only gating
- Countdown timer with 3‑2‑1 beeps · auto‑spin on timer end · "hide until spin" reveal
- Rewards with attachable **prize images** shown on the win
- Chat announcements: **🏆 @winner won {reward}!** (needs a bot token)
- Positionable "Entries Open" banner · colour glow that pulses on the win

## 💬 Feedback
Found a bug or want a feature? **[Open an issue](https://github.com/AbdulazizJHK/giveaway-wheel/issues/new)** — that's the easiest way to reach us.
