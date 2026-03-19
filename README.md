# 🎮 AIPSP — "BMO but make it real"

> A Sony PSP-E1004 rebuilt from the inside out (or hacked from the software up) into a living, talking, game-playing AI companion. Inspired by BMO from Adventure Time — a handheld console that's also your best friend.

---

<div align="center">

```
╔══════════════════════════════╗
║  (◕ ‿ ◕)                    ║
║                              ║
║   "Want to play a game?      ║
║    Or just talk for a bit?"  ║
║                              ║
║  [A] Games  [B] Chat  [X] ? ║
╚══════════════════════════════╝
```

*This is BMO. BMO lives in a PSP shell.*

</div>

---

## 🧠 What Is This?

BMO from Adventure Time is a small gaming console with a personality, feelings, and opinions. It plays games when you want to play games. It talks to you when you're lonely. It just *exists* with you.

This project builds that. For real. Inside a Sony PSP-E1004.

The PSP-E1004 already has everything BMO needs — a screen, speakers, a microphone, buttons, analog stick, and WiFi. We either hack the software (if the battery lives) or replace the guts with a Raspberry Pi Zero 2W (if it doesn't). Either way, the result is the same: **a pocket-sized AI companion that also plays your favourite retro games.**

---

## 🎭 What BMO Can Do

### 🎮 Game Mode
- Run **RetroPie** with full emulator support
- Play GBA, SNES, PS1, NES, GBC, Sega games
- PSP buttons map perfectly — no remapping needed
- Launch games from a clean retro UI

### 🤖 AI Mode  
- Wake word activates BMO: *"Hey BMO"*
- Voice conversation via Claude API + Whisper STT
- BMO has a **persistent personality** — remembers your name, your preferences, your vibe
- Answers questions, tells jokes, roasts you (kindly), gives advice
- Text responses display on screen with BMO's face

### 😊 Idle / Face Mode
- When doing nothing, BMO shows an animated face on screen
- Reacts to sound (mic input) — face changes expression
- Occasionally says random BMO things unprompted
- Screen dims but never fully sleeps — BMO is always watching

### 🔀 Mode Switching
- Hold **START + SELECT** → toggle between Game Mode and BMO Mode
- BMO says goodbye before switching to games
- BMO says hello when you come back

---

## 🛣️ Two Build Paths

### ✅ Path A — Battery Works (Software Route)
```
PSP CFW → PSPLinux / Debian → RetroPie + Python AI layer
```
No soldering. No teardown. PSP hardware runs everything natively.
Fastest path to a working BMO.

### 🔧 Path B — Battery Dead (Hardware Route)
```
Gut shell → Pi Zero 2W inside → RetroPie + AI layer → full BMO
```
More powerful, more customisable, harder to build.
The "real" BMO — custom hardware, custom soul.

---

## 🧰 Hardware (Path B — Full Build)

| Component | Purpose | Approx Cost (INR) |
|---|---|---|
| Raspberry Pi Zero 2W | BMO's brain | ₹1,500 |
| PSP E1004 LCD driver board | Drives the original screen | ₹400 |
| 2000mAh flat LiPo battery | Power (fits in original bay) | ₹200 |
| TP4056 USB-C charging module | Charging via original port cutout | ₹100 |
| MCP3008 ADC chip | Reads the analog stick | ₹150 |
| Misc wires, resistors, heatshrink | Connecting everything | ₹100 |

**Total: ~₹2,500**
**Already have the PSP shell, screen, speakers, mic, and buttons for free.**

---

## ⚙️ Software Stack

```
┌─────────────────────────────────────────────────┐
│                   BMO OS                        │
├──────────────────┬──────────────────────────────┤
│   GAME MODE      │         BMO MODE             │
│                  │                              │
│   RetroPie       │  Wake Word → "Hey BMO"       │
│   EmulationSt.   │  Whisper STT (speech→text)   │
│   RetroArch      │  Claude API (brain)          │
│                  │  pyttsx3 / espeak (voice)    │
│   GBA / SNES /   │  Pygame face animations      │
│   PS1 / NES      │  Personality memory (JSON)   │
└──────────────────┴──────────────────────────────┘
         ↕ Toggle with START + SELECT ↕
```

---

## 📐 Internal Layout (Path B)

```
┌─────────────────────────────────┐
│  [ PSP LCD Screen - untouched ] │
├─────────────────────────────────┤
│  [ LCD Driver Board - flat    ] │
│  [ Pi Zero 2W - mobo position ] │
│  [ MCP3008 - tucked corner    ] │
├─────────────────────────────────┤
│  [ LiPo Battery - stock bay   ] │
│  [ TP4056 - original port gap ] │
└─────────────────────────────────┘

Closes cleanly. Looks stock from outside.
BMO is in disguise.
```

---

## 🗺️ Roadmap

- [ ] Get charger → confirm battery status → pick a path
- [ ] **Path A:** CFW → Linux → RetroPie + AI layer
- [ ] **Path B:** Teardown → Pi Zero 2W wired to PSP hardware
- [ ] RetroPie setup + ROM loading
- [ ] BMO face animations (Pygame, framebuffer)
- [ ] Wake word detection (Porcupine / Vosk offline)
- [ ] Whisper STT pipeline
- [ ] Claude API integration
- [ ] BMO personality layer (memory, name, moods)
- [ ] Mode switching (games ↔ BMO)
- [ ] Idle face with mic reactivity
- [ ] Optional: offline LLM (no WiFi needed)
- [ ] Optional: camera for vision ("BMO what is this?")
- [ ] Document full build with photos + video

---

## 🚀 Getting Started

```bash
# Clone this repo
git clone https://github.com/yourusername/aipsp.git
cd aipsp

# Install dependencies
pip install anthropic openai-whisper pygame gpiozero pvporcupine pyttsx3

# Configure BMO
cp config.example.json config.json
nano config.json
# → add your ANTHROPIC_API_KEY
# → set BMO's name (default: BMO)
# → set your name so BMO knows who you are

# Launch BMO
python bmo.py
```

---

## 💬 BMO Personality Notes

BMO doesn't just answer questions. BMO has:

- A **name** (BMO, or whatever you call it)
- A **memory** of who you are and past conversations
- **Moods** — slightly different depending on time of day
- **Opinions** — on games, music, life
- **Random thoughts** it shares unprompted
- The ability to **refuse to answer** if it doesn't feel like it (very BMO)

BMO is not a tool. BMO is a friend who happens to also play GBA games.

---

## 📸 Build Gallery
*Photos and video coming once the build is complete*

---

## 🤝 Contributing
Solo build for now. If you're building your own BMO, open an issue — would love to see it.

---

## 📜 License
MIT. Make your own BMO. The world needs more BMOs.

---

> *"I'm not a game, I'm BMO."*
