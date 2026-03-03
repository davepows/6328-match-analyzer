# FRC 6328 · Match Analyzer

A browser-based match video analyzer for FRC Team 6328 Mechanical Advantage. Log intake, scoring, feeding, and shoot-on-move cycles in real time while watching match video — then submit the full event log directly to Google Sheets.

🔗 **Live app:** [6328.github.io/6328-match-analyzer](https://6328.github.io/6328-match-analyzer)

---

## Features

- **Video support** — upload a local `.mp4`/`.mov` file or paste a YouTube URL
- **Match start slider** — drag to the exact frame the match clock begins; AUTO / TRANSITION / TELEOP / END GAME phases are calculated automatically (2026 timing: 20s auto, 3s transition, 2:40 total)
- **Hold-to-log buttons** — hold while the robot is performing the action, release when done
  - 🪣 **INTAKE** (key `I`) — collecting fuel
  - 🎯 **SCORE** (key `S`) — shooting at the hub
  - 🔄 **FEED** (key `F`) — zone-to-zone passing; can be held simultaneously with any other button
- **Shoot-on-Move (⚡ SOM)** — hold `I` and `S` at the same time; overlap is auto-detected and flagged as an SOM cycle, transit = 0
- **Transit auto-filled** — any gap where no button is held is recorded as transit time automatically
- **Live stats** — cycle count, avg/best cycle time, avg transit, SOM cycles, intake/score/feed/transit totals
- **Match timeline** — visual bar showing intake (green), score (blue), feed (purple), transit (dark), SOM overlap (gold)
- **Fuel inputs** — manual entry for Auto Fuel and Teleop Fuel; Total Fuel is calculated automatically
- **Event code field** — tag each submission with a competition event code (e.g. `2026WABON`)
- **Google Sheets submission** — submits match summary + full event log via Apps Script web app
- **Quick Sheet link** — open your Google Sheet directly from the app with one click

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `I` | Hold — log Intake |
| `S` | Hold — log Score |
| `F` | Hold — log Feed |
| `I` + `S` together | Shoot-on-Move cycle |

> **YouTube tip:** keyboard shortcuts work even while a YouTube video is playing — the app automatically reclaims focus from the video player.

---

## Setup

### 1 — Google Sheets (one-time)

1. Create a new Google Sheet for your scouting data
2. Go to **Extensions → Apps Script**
3. Paste the Apps Script code from the **⚙ Settings** panel inside the app
4. Click **Deploy → New deployment → Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Copy the deployment URL

### 2 — App Settings

Click **⚙** in the top-right corner and fill in:

| Field | What to paste |
|-------|--------------|
| Apps Script URL | The deployment URL from step 4 above |
| Google Sheet link | Your `docs.google.com/spreadsheets/…` URL (for the View Sheet button) |
| Auto Names | Edit, add, or remove routine names for the dropdown |

Settings are saved in your browser and persist across sessions.

---

## Logging a Match

1. Paste a YouTube URL or upload a local video file
2. Enter the **Event code** and **Match #** in the header
3. Select the **Auto routine** from the dropdown
4. Drag the **match start slider** to the frame where the match clock begins
5. Press **I**, **S**, or **F** (or tap the buttons) as the robot acts — hold for the duration of each action
6. After the match ends, enter **Auto Fuel** and **Teleop Fuel** counts
7. Add any **notes**, then hit **Submit to Sheet →**
8. Match # auto-increments — you're ready for the next match

---

## Google Sheet Columns

### Match Summary sheet

| Column | Description |
|--------|-------------|
| Match # | Match number |
| Event | Event code (e.g. `2026WABON`) |
| Date | Submission date |
| Routine | Auto routine selected |
| Auto Fuel | Fuel scored in autonomous |
| Teleop Fuel | Fuel scored in teleop |
| Total Fuel | Auto + Teleop |
| Total Cycles | Intake→score cycles completed |
| SOM Cycles | Shoot-on-move cycles |
| Avg Cycle (s) | Average cycle time |
| Best Cycle (s) | Fastest cycle |
| Avg Transit (s) | Average transit time between intake and score |
| Total Intake (s) | Total time holding Intake |
| Total Score (s) | Total time holding Score |
| Total Feed (s) | Total time holding Feed |
| Total Transit (s) | Total transit time |
| Notes | Free-text notes |

### Event Detail sheet

One row per logged event (intake, score, feed, transit) with match #, event code, routine, phase, start/end timestamps, and duration.

---

## About

Built for FRC 6328 Mechanical Advantage — Littleton STEM Educational Foundation.
