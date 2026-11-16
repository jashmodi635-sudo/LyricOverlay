# LyricOverlay

![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11%20(x64)-0078D6?style=flat-square)
![Framework](https://img.shields.io/badge/Framework-.NET%208%20WPF%20%2B%20Win32-512BD4?style=flat-square)
![Release](https://img.shields.io/badge/Release-v1.2.0-2EA043?style=flat-square)
![License](https://img.shields.io/badge/API%20Key-Not%20Required-success?style=flat-square)

**LyricOverlay** is a lightweight, native Windows system-tray utility that floats **real-time, word-synced kinetic Spotify lyrics** over any workspace, browser, video, or full-screen game in a **PureRef-style transparent, click-through overlay**.

Zero setup friction: there is no Spotify Developer account, OAuth login, or API key required. LyricOverlay hooks directly into Windows' native media session (`SMTC`) to track local Spotify Desktop playback at sub-second precision and fetches time-synced `.lrc` lyrics from [LRCLIB](https://lrclib.net/).

---

## Key Features

### 1. PureRef-Style Transparent & Click-Through Overlay
- **Click-Through Lock Mode (Default):** Uses Win32 layered extended styles (`WS_EX_TRANSPARENT | WS_EX_LAYERED | WS_EX_TOOLWINDOW`) so every mouse click, drag, and scroll wheel event passes straight through the lyrics to the apps underneath—and stays hidden from `Alt + Tab`.
- **Interactive Edit Mode (`Ctrl + Shift + L`):** Toggle edit mode anytime to reveal a PureRef-style border with **8-directional resize handles** (all 4 corners and 4 edges), free drag repositioning anywhere across your screens, live dimension/coordinate readouts, and arrow-key micro-nudging.
- **Custom Tinted Backdrop:** Prefer higher contrast over busy wallpapers or bright websites? Toggle a rounded backdrop behind the lyric board with custom color swatches/hex codes and a **0%–100% opacity slider**.

### 2. 60fps Kinetic Typography & Smart Song Cues
Driven by `CompositionTarget.Rendering` locked to your display's refresh rate, with three switchable motion engines in the System Tray:
- **Spring Pop:** Active words scale up and illuminate with an elastic spring bounce and soft drop-shadow glow.
- **Liquid Karaoke Wipe:** A smooth left-to-right luminance gradient sweeps across each word in sync with vocal delivery.
- **Wave Cascade:** Upcoming words glide upward into focus while the active phrase rides a gentle rhythmic wave.
- **Instrumental & Section Intelligence:**
  - Displays **three animated pulsing dots (`•  •  •`)** during intros and instrumental breaks (`≥ 4.5s`).
  - Shows a subtle **`CHORUS`** pill cue right before chorus sections begin.
  - **Auto-Clear:** Automatically wipes lyrics, dots, and chorus tags the moment a song ends or playback stops so finished lyrics never linger on screen.

### 3. Drift-Free Sync Engine & Live English Translation
- **Sub-Second SMTC Tracking:** Combines Windows `GlobalSystemMediaTransportControls` event hooks with a high-resolution `Stopwatch` anchor, UTC timestamp normalization, and a track-switch reset guard so seeking or skipping snaps instantaneously without drift.
- **Smart LRCLIB Matching & Local Caching:** Filters candidates by exact track duration (`±2.5s`), strips noisy suffixes (`- Remastered`, `(feat. ...)`, `- Radio Edit`), supports Enhanced LRC inline word timestamps, and caches lyrics locally in `%LocalAppData%\LyricOverlay\cache\` for instant offline-ready replays.
- **Live Sync Nudging:** Press `Ctrl + Shift + ←` or `Ctrl + Shift + →` anytime to adjust timing by `±50ms` on the fly.
- **Optional English Translation:** Toggle automatic translation from the System Tray to display **English Only** or **Original + English Subtitle** for songs in any language, cached locally after the first play.

### 4. Hover-Aware Mini-Player Bar
- **Left Corner:** Displays the active **Song Title** and **Artist Name** with clean ellipsis truncation.
- **Right Corner:** Shows live **elapsed / remaining time** alongside interactive **Previous (`⏮`)**, **Play / Pause (`▶` / `⏸`)**, and **Next (`⏭`)** buttons.
- **Smart Hover Hit-Testing:** Even while the lyric board is locked in click-through mode, moving your cursor over the bottom mini-player bar smoothly illuminates a dark rounded pill backdrop (`#DE101014`) and temporarily unlocks pointer input just for that bar—re-locking automatically the moment your cursor moves away.

### 5. System Tray Control Center & Friend Sharing
- **Dark & Light Mode:** Switch the entire System Tray control popover, dropdowns, sliders, and context menus between Dark and Light themes.
- **Multi-Monitor & Mixed-DPI Support:** Enable or disable independent, synchronized overlay windows per monitor—accurately scaled across mixed DPI setups (e.g., `100%` laptop + `150%` external monitor).
- **System Utilities:** Built-in toggles for **Keep Screen Awake** (`SetThreadExecutionState`) and **Launch at Windows Startup**.
- **One-Click Style Share Codes:** Export your current visual setup (layout, kinetic motion, font, size, colors, and backdrop opacity) as a compact Base64 code to paste in Discord or group chats so friends can import your exact look in one click.

---

## Installation & Quick Start

Portable Single-File `.exe` 
1. Open the **[Releases](../../releases/latest)** page and download **`LyricOverlay.exe`** *(self-contained x64 build—no `.NET` runtime installation required)*.
2. Double-click **`LyricOverlay.exe`** to launch it in the background.
   > **Note on Windows SmartScreen:** Because this is an independent unsigned build, Windows may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** (this only appears once).
3. Click the **`^`** arrow in your Windows System Tray (bottom-right near the clock) and click the **LyricOverlay** icon to choose your monitors, theme, and kinetic motion.
4. Play any track on the **Spotify Desktop app** *(Windows Store or standalone installer; Spotify inside a web browser tab does not expose full SMTC metadata)*.

