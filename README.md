<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:7C3AED,100:8a4fff&height=200&section=header&text=BLUUHUB%20SONGS&fontSize=56&fontColor=ffffff&animation=twinkling&fontAlignY=38&desc=Community%20song%20store%20%C2%B7%20midi2lua&descAlignY=60&descSize=16&descColor=cbb8ff" />

<br />

[![readme-typing-svg](https://readme-typing-svg.demolab.com?font=Inter&weight=500&size=15&duration=2800&pause=900&color=A78BFA&center=true&vCenter=true&width=540&lines=Community+songs+for+BluuHub+Piano;MIDI+to+Lua%2C+hosted+for+you;Structured+note-data%2C+never+executable;Reviewed+before+it+goes+live.)](https://bethebluu.com/midi2lua)

<br />

![Status](https://img.shields.io/badge/status-live-7C3AED?style=flat-square&labelColor=0a0a14)
![Data](https://img.shields.io/badge/data-json%20only-8a4fff?style=flat-square&labelColor=0a0a14)
![Tool](https://img.shields.io/badge/midi2lua-bethebluu.com-7C3AED?style=flat-square&labelColor=0a0a14)
![Discord](https://img.shields.io/discord/180865380632363008?style=flat-square&logo=discord&logoColor=white&label=discord&color=8a4fff&labelColor=0a0a14)

<br />

[![Open midi2lua](https://img.shields.io/badge/%E2%86%92%20Open%20midi2lua-7C3AED?style=for-the-badge&logo=lua&logoColor=white&labelColor=0a0a14)](https://bethebluu.com/midi2lua)
[![Discord](https://img.shields.io/badge/%E2%86%92%20Discord-8a4fff?style=for-the-badge&logo=discord&logoColor=white&labelColor=0a0a14)](https://discord.gg/HKvZjPfNTH)

<br />

</div>

---

<br />

## Overview

Backing store for **BluuHub Piano** (Roblox) community songs and hosted **[midi2lua](https://bethebluu.com/midi2lua)** scripts. Convert a MIDI on the web, share it here, and approved songs flow straight into the in-game **Community** library.

Every song is stored as **structured note-data (JSON)**, never executable Lua, so an approved song can never run code on a player's machine.

<br />

## How it works

```
midi2lua (web)  >> Share >>  Cloudflare Worker  >>  pending/
  (Turnstile + validation, off-VPS)                   |
                                                 review (approve)
                                                       v
piano-ui.lua  << fetch <<  index.json  << build <<  approved/
  Community genre              GitHub Action
```

| Step | What happens |
|---|---|
| **Share** | midi2lua posts structured events and a title to the Worker (with Turnstile) |
| **Validate** | Worker verifies the captcha, checks the data, dedupes, writes `pending/` |
| **Review** | A maintainer approves (move to `approved/`) or rejects (delete) |
| **Build** | A GitHub Action compiles `approved/*.json` into `index.json` |
| **Serve** | `piano-ui.lua` fetches `index.json` and renders the Community genre |

<br />

## Structure

```
bluuhub-songs/
├── pending/      submissions awaiting review (not live)
├── approved/     approved songs (one .json each)
├── index.json    built live manifest, fetched by piano-ui.lua
├── scripts/      hosted .txt for loadstring links
└── .github/workflows/build-index.yml
```

<br />

## Data format

A song is structured events, never code:

```json
{
  "title": "Song Name",
  "bpm": 120,
  "events": [
    { "t": "n", "k": "tyu", "b": 0.25 },
    { "t": "r", "b": 0.5 },
    { "t": "v", "v": 0.8 },
    { "t": "p", "d": true }
  ]
}
```

`n` note (keys, hold beats) · `r` rest (beats) · `v` velocity · `p` pedal (down / up)

<br />

## Tech

```
Upload        Cloudflare Worker (off-VPS, free tier)
Anti-abuse    Cloudflare Turnstile + content validation
Storage       GitHub repository (this one)
Build         GitHub Actions
Delivery      raw.githubusercontent.com to Roblox HttpGet
Tool          bethebluu.com/midi2lua
```

<br />

---

<div align="center">

<br />

Part of **BluuHub**. Songs are reviewed before going live.

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8a4fff,100:7C3AED&height=100&section=footer" />

</div>
