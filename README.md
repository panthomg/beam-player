# 🎧 BEAM Player

![Beam Player Banner](https://via.placeholder.com/1000x300/121212/1db954?text=BEAM+Player)

**Beam Player** is a beautiful, offline-first, open-source local music player built for the web. It uses IndexedDB to store your audio files locally, meaning once you upload them, you never need an internet connection to listen again.

🌐 **[Live Demo & Web App](#)** *(Replace this with your live link)*  
👨‍💻 **Created by:** [Panthomg](https://tintool.netlify.app/itzpanth) | [TinTool](https://tintool.netlify.app/)

---

## ✨ Features
* **📶 Offline First:** Audio files are stored entirely in your browser (`localForage` / IndexedDB).
* **📱 PWA Ready:** Installable on iOS, Android, and Desktop as a native app.
* **🔀 Smart Autoplay:** Auto-shuffles playlist tracks or plays random library songs when the queue ends.
* **🎧 Hardware Sync:** Full support for lock screen controls, AirPods, and media keys via the MediaSession API.
* **🎨 Color Extraction:** Automatically extracts album art and colors from MP3 ID3 tags.
* **💾 Backup & Restore:** Export your entire music library and playlists as a single JSON file.
* **⚡ Zero Build Tools:** Pure HTML, CSS, and Vanilla JavaScript. No React, no Webpack, no `npm install`.

## 🚀 How to Use (Local Setup)
Because Beam Player uses zero build tools, running it is incredibly simple:

1. Clone the repository:
   ```bash
   git clone https://github.com/panthomg/beam-player.git
