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

Community song store for **BluuHub Piano** (Roblox), powered by **[midi2lua](https://bethebluu.com/midi2lua)**. Turn any MIDI into a playable song on the web, then play it in game or share it with everyone.

<br />

## Usage

**1. Convert a MIDI**
Open **[midi2lua](https://bethebluu.com/midi2lua)**, drop a `.mid` file, choose your options, and hit Generate.

**2. Play it in BluuHub Piano**
Copy the generated script into **BluuHub Piano → Add Songs**, or open the **loadstring** tab to grab a ready hosted link, no setup needed.

**3. Share with the community** *(optional)*
Hit **Share to BluuHub**. After a quick review it shows up in the in-game **Community** genre for every player.

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

---

<div align="center">

<br />

Part of **BluuHub**. Songs are reviewed before going live.

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8a4fff,100:7C3AED&height=100&section=footer" />

</div>
