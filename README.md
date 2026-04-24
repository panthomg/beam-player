# BEAM Player

<div align="center">
  <img src="https://img.shields.io/badge/version-2.3.0-brightgreen" alt="Version">
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="License">
  <img src="https://img.shields.io/badge/platform-web%20%7C%20PWA-purple" alt="Platform">
  <img src="https://img.shields.io/badge/made%20with-vanilla%20JS-yellow" alt="Made with Vanilla JS">
</div>

<br>

<p align="center">
  <strong>A beautiful, offline-first, open-source music player for the web.</strong><br>
  Installable as a native app on iOS, Android, and Desktop. No ads. No tracking. Just your music.
</p>

<br>

<p align="center">
  <a href="#-live-demo">Live Demo</a> •
  <a href="#-features">Features</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-api-documentation">API Docs</a>
</p>

---

## 🎧 Live Demo

[Launch BEAM Player](https://beamplay.netlify.app/app.html)

> **Pro Tip:** On mobile, tap "Add to Home Screen" to install BEAM as a native app!

---

## ✨ Features

### 🎵 Core Music Experience

| Feature | Description |
|---------|-------------|
| **Local Music Library** | Import your MP3 files — they're stored securely in your browser's IndexedDB |
| **Album Organization** | Automatically groups tracks by album using ID3 tags |
| **Playlists** | Create, edit, and manage custom playlists |
| **Queue System** | See what's playing next, reorder tracks on the fly |
| **Smart Autoplay** | When queue ends, BEAM intelligently continues with random tracks from your library or current playlist |
| **Shuffle & Repeat** | Standard playback controls with visual feedback |

### 🎨 User Experience

- **Offline First** — No internet? No problem. Everything works offline after initial load.
- **Installable PWA** — Works like a native app on any device
- **Hardware Media Controls** — Works with media keys, headphones, and lockscreen controls
- **Keyboard Shortcuts** — Space for play/pause, arrow keys for next/previous
- **Touch Optimized** — Built for mobile with swipe gestures
- **Dynamic Color Themes** — Album art influences the accent color of the player

### 📁 Library Management

- **Import as Album** — Group imported files into albums automatically
- **Create Playlists** — Build custom collections from your library
- **Edit Track Metadata** — Change titles, artists, and album names after import
- **Custom Album Art** — Upload custom covers for albums and playlists
- **Bulk Import** — Select multiple files at once

### 💾 Backup & Restore

- **Export Library** — Download a complete backup of your music, playlists, and metadata as a JSON file
- **Import Library** — Restore your entire collection from a backup

### 🎮 Full Player Features

- **Seekable Scrubber** — Drag to any point in the song
- **Queue View** — See and manage upcoming tracks
- **Now Playing Screen** — Fullscreen immersive player with animated controls
- **Mini Player** — Persistent bar at the bottom for quick control

### 🔧 Developer Friendly

- **No Build Step** — Pure HTML/CSS/JS, open and run
- **Vanilla Stack** — No React, no Vue, no Angular — just the web platform
- **Self-Contained** — All logic in a single HTML file
- **Cache-First PWA** — Service worker for offline capability

---

## 🚀 Installation

### For Users (Web App)

1. Visit the [BEAM Player web app](https://beamplay.netlify.app/app.html)
2. Tap the share/options button in your browser
3. Select **"Add to Home Screen"** or **"Install App"**
4. Launch BEAM from your home screen like a native app

### For Developers (Local Setup)

```bash
# Clone the repository
git clone https://github.com/panthomg/beam-player.git

# Navigate into the directory
cd beam-player

# No dependencies! Just open the file
open app.html   # macOS
# or
start app.html  # Windows
# or serve with any static server
npx serve .
```

### Deploy to Netlify / Vercel

1. Push this repository to GitHub
2. Connect your repo to Netlify or Vercel
3. Set the publish directory to root (`/`)
4. Deploy — that's it!

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **HTML5 / CSS3** | Structure and styling with custom properties |
| **Vanilla JavaScript** | All application logic — no frameworks |
| **IndexedDB (localforage)** | Persistent local storage for audio files and metadata |
| **jsmediatags** | ID3 metadata extraction from MP3 files |
| **Phosphor Icons** | Clean, consistent icon set |
| **Web Audio API** | Audio playback and control |
| **Media Session API** | Hardware buttons and lockscreen integration |
| **Service Workers** | Offline caching and PWA functionality |

---

## 📚 API Documentation

### Storage Schema

BEAM uses IndexedDB via `localforage`. The data structure is:

| Key Pattern | Value Type | Description |
|-------------|------------|-------------|
| `meta_track_{id}` | Object | Track metadata (title, artist, album, artworkId) |
| `blob_{id}` | Blob/File | The actual audio file |
| `art_{id}` | String (base64) | Album artwork image |
| `beam_playlists` | Object | All user playlists |
| `beam_albumMeta` | Object | Custom album metadata (descriptions, custom covers) |
| `beam_settings` | Object | User preferences (autoplay, etc.) |

### Key Functions

#### Playback Control

```javascript
// Play a queue of tracks
playQueue(tracks, startIndex)

// Load and play a specific track by index
loadTrack(index)

// Toggle play/pause
togglePlay()

// Next/Previous track
nextTrack()
prevTrack()
```

#### Library Management

```javascript
// Import audio files
importFiles(files)

// Get all tracks
getAllTracks()

// Get albums (grouped by album name)
getAlbums()

// Create/update playlist
createPlaylist(name)
addToPlaylist(playlistId, trackId)
removeFromPlaylist(playlistId, trackId)
```

#### Backup System

```javascript
// Export all data as JSON
exportBackup()  // Triggers download

// Import from backup JSON
importBackup(jsonFile)
```

### Events

| Event | Listener | Description |
|-------|----------|-------------|
| `AudioEngine.onplay` | `AudioEngine.onplay = () => {}` | Fired when audio starts playing |
| `AudioEngine.onpause` | `AudioEngine.onpause = () => {}` | Fired when audio pauses |
| `AudioEngine.onended` | `AudioEngine.onended = () => {}` | Fired when track ends (triggers next) |
| `AudioEngine.ontimeupdate` | `AudioEngine.ontimeupdate = () => {}` | Fired every frame for scrubber updates |

---

## 🎮 Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play / Pause |
| `→` (Arrow Right) | Next Track |
| `←` (Arrow Left) | Previous Track / Restart current |

> *Note: Works when no input/textarea is focused*

---

## 🧪 Browser Support

| Browser | Version | PWA Install |
|---------|---------|-------------|
| Chrome / Edge | 90+ | ✅ |
| Safari (iOS) | 15+ | ✅ (via Add to Home Screen) |
| Firefox | 90+ | ⚠️ (Limited PWA support) |
| Samsung Internet | 16+ | ✅ |

---

## 📁 Project Structure

```
beam-player/
├── app.html            # Main player application
├── manifest.json       # PWA manifest
└── README.md           # This file
```

> **Note:** The entire app is contained in `app.html` — no separate CSS or JS files needed!

---

## 🔧 Customization

### Changing Colors

Edit the CSS custom properties in the `<style>` block:

```css
:root {
    --accent: #1db954;    /* Change to your brand color */
    --bg: #050505;         /* Background color */
    --surface: #121212;    /* Card/surface background */
}
```

### Changing App Name

Modify the `<title>` tag in both `index.html` and `app.html`, and update `manifest.json`.

### Adding New Features

The code is organized into logical sections:

- **State Management** — Top of the script
- **Storage & Loading** — `loadLibrary()`, `processAudioFile()`
- **Rendering** — `renderLibrary()`, `renderPlaylists()`
- **Playback Engine** — `playQueue()`, `loadTrack()`
- **UI Handlers** — Event listeners in `setupEventListeners()`

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Bug Reports** — Open an issue describing the problem and steps to reproduce
2. **Feature Requests** — Suggest improvements via issues
3. **Code Contributions** — Fork the repo, make changes, and submit a PR

### Development Guidelines

- Make it yours, personalize it to you needs.
- Maintain offline-first philosophy
- Test on both desktop and mobile before submitting
- Keep the app self-contained in `app.html`

---

## 📝 License

MIT License — feel free to use, modify, and distribute this software. Attribution is appreciated but not required.

---

## 🙏 Acknowledgments

- [Phosphor Icons](https://phosphoricons.com/) for the beautiful icon set
- [localforage](https://localforage.github.io/localForage/) for IndexedDB wrapper
- [jsmediatags](https://github.com/aadsm/jsmediatags) for ID3 parsing
- The open-source community for endless inspiration

---

## 📬 Contact

Built with ❤️ by **Panthomg**

- Portfolio: [TinTool](https://tintool.netlify.app/)
- GitHub: [@panthomg](https://github.com/panthomg)

---

<div align="center">
  <sub>BEAM Player — Your Music. Your Rules. Completely Open Source.</sub>
</div>
