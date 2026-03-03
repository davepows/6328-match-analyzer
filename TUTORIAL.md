# Match Analyzer — Quick Start Guide

We built a browser-based tool for logging match video in real time. Here's how to use it.

🔗 **[Open the app →](https://6328.github.io/6328-match-analyzer)**

---

## What it does

While you watch a match replay, you hold down keys (or tap buttons on screen) to log what the robot is doing. The app tracks how long each action takes, calculates cycle times, and sends everything to our Google Sheet automatically.

---

## Step-by-step

**1. Open the app and load a video**
Paste a YouTube match link into the box and hit Load, or upload a local video file with the 📁 button.

**2. Fill in the match info**
At the top of the page, enter:
- **Event** — the event code (e.g. `2026WABON`)
- **Match #** — the match number
- **Routine** — which auto the robot ran (select from the dropdown)

**3. Set the match start**
Drag the slider at the bottom of the video to the exact moment the match clock starts. The app uses this to figure out what phase (Auto / Teleop / End Game) each action happened in.

**4. Log actions while watching**
Hold the buttons (or keys) for as long as the robot is doing that action — release when it stops:

| Button | Key | What it tracks |
|--------|-----|----------------|
| 🪣 INTAKE | `I` | Robot collecting fuel |
| 🎯 SCORE | `S` | Robot shooting at the hub |
| 🔄 FEED | `F` | Zone-to-zone passing |

**Shoot-on-Move:** Hold `I` and `S` at the same time — the app automatically flags it as an SOM cycle.

Any time you're not holding a button, that time is logged as **transit** automatically. You don't need to do anything extra for it.

**5. Enter fuel counts**
After the match, look up the auto hub counter and enter:
- **Auto Fuel** — fuel scored during autonomous
- **Teleop Fuel** — fuel scored during teleop

Total Fuel is calculated automatically.

**6. Add notes and submit**
Type any observations in the Notes box (defense, mechanism issues, anything worth remembering), then hit **Submit to Sheet →**. The match number increments automatically so you're ready for the next one.

---

## Reading the timeline

After logging, the colored bar at the bottom of the app shows the full match broken down visually:

- 🟢 **Green** — Intake
- 🔵 **Blue** — Score
- 🟣 **Purple** — Feed
- ⚡ **Gold** — Shoot-on-Move overlap
- ⬛ **Dark** — Transit

---

## Tips

- **YouTube keyboard issue?** Make sure you've clicked somewhere on the page outside the video before using key shortcuts — the app handles this automatically but clicking the stats panel is a safe bet.
- **Watching the same match twice?** Just submit again with the same match number — you can filter duplicates in the sheet later.
- **Wrong action logged?** Hit **+ New Match** to clear everything and start that match over before submitting.
- **View the sheet** anytime by clicking **📊 View Sheet** next to the Submit button.

---

## Questions?

Reach out to Dave or check the full README in the [GitHub repo](https://github.com/6328/6328-match-analyzer).
