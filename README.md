# FRC 6328 · Match Analyzer

A browser-based match video analyzer for FRC Team 6328 Mechanical Advantage. Log intake, scoring, feeding, and shoot-on-move cycles in real time while watching match video — then submit the full event log directly to Google Sheets.

## Features

- **Video support** — upload a local `.mp4`/`.mov` file or paste a YouTube URL
- **Match start slider** — drag to the exact frame the match clock begins; AUTO/TELEOP phases are calculated from that point automatically
- **Hold-to-log buttons** — hold while the robot is performing the action, release when done
  - 🪣 **INTAKE** (key `I`) — collecting fuel
  - 🎯 **SCORE** (key `S`) — shooting at the hub
  - 🔄 **FEED** (key `F`) — zone-to-zone passing; can be held simultaneously with any other button
- **Shoot-on-Move (⚡ SOM)** — hold `I` and `S` at the same time; the app auto-detects the overlap and flags it as an SOM cycle, no extra button needed
- **Transit auto-filled** — any time no button is held, transit time is recorded automatically
- **Live stats** — cycle count, avg/best cycle time, avg transit, SOM cycles, feed time
- **Match timeline** — visual bar showing intake (green), score (blue), feed (purple), transit (dark), and SOM overlap (gold)
- **Google Sheets submission** — submits match summary + full event log via Apps Script

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `I` | Hold — log Intake |
| `S` | Hold — log Score |
| `F` | Hold — log Feed |
| `I` + `S` together | Shoot-on-Move cycle |


## Google Sheets Setup

1. Open your Google Sheet and go to **Extensions → Apps Script**
2. Paste the Apps Script code from the **⚙ Settings** panel inside the app
3. Click **Deploy → New deployment → Web app**
   - Execute as: **Me**
   - Who has access: **Anyone**
4. Copy the web app URL and paste it into the Settings panel in the app
5. Each match submission creates/updates two sheets:
   - **Match Summary** — one row per match with aggregate stats
   - **Event Detail** — one row per event (intake, score, feed, transit) with timestamps

## Data Tracked Per Match

| Field | Description |
|-------|-------------|
| Match # | Match number (auto-increments) |
| Routine | Selected auto routine |
| Auto Fuel | Prompted on submission |
| Cycles | Total intake→score cycles completed |
| SOM Cycles | Cycles where intake and score overlapped (shoot-on-move) |
| Avg / Best Cycle | Cycle time stats |
| Avg Transit | Average time between intake and score |
| Total Feed Time | Total seconds holding the Feed button |
| Events | Full timestamped log of every action |

## About

Built for FRC 6328 Mechanical Advantage — Littleton STEM Educational Foundation.
