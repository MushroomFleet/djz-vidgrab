# djz-vidgrab

A lightweight Windows desktop screen-region recording utility that lives in the system tray. Capture any rectangular area of your screen with desktop audio, saved immediately as a WebM video clip.

## Features

- **System Tray App** — runs quietly in the background with no main window
- **Global Hotkey (CTRL+F7)** — press anywhere to start region selection
- **Click-and-Drag Region Select** — full-screen overlay with crosshair cursor, live size readout, and neon green selection border
- **Instant Recording** — recording begins the moment you release the mouse
- **Desktop Audio Capture** — WASAPI loopback captures system audio alongside video
- **Floating Stop Bar** — always-visible recording timer with stop button, positioned outside the capture area
- **Clip Library** — browse, play, and locate all your recordings from a simple built-in window
- **Settings** — video quality (High/Medium/Low), output folder, audio toggle, start-with-Windows option
- **WebM Output** — VP8 video + Vorbis audio in a widely supported container
- **Portable** — single self-contained `.exe` with bundled FFmpeg, no installer needed

## Download

Head to [**Releases**](https://github.com/MushroomFleet/djz-vidgrab/releases) and download the latest `djz-vidgrab-portable.zip`.

Extract the zip and run `djz-vidgrab.exe` — that's it. No installation or .NET runtime required.

```
djz-vidgrab-portable/
├── djz-vidgrab.exe      ← run this
└── tools/
    └── ffmpeg.exe       ← bundled, required
```

## Usage

| Action | How |
|---|---|
| Start region select | `CTRL+F7` (global hotkey) |
| Draw capture area | Click and drag on the overlay |
| Cancel selection | `ESC` |
| Stop recording | Click **STOP** on the floating bar, or press `ESC` |
| Open Clip Library | Left-click the tray icon |
| Access menu | Right-click the tray icon |

Recordings are saved to the `output/` folder next to the exe (configurable in Settings).

## Requirements

- Windows 10/11 (x64)
- No additional runtime or dependencies needed

## Building from Source

```bash
# Clone
git clone https://github.com/MushroomFleet/djz-vidgrab.git
cd djz-vidgrab

# Place ffmpeg.exe in the tools/ directory
# Download from https://www.gyan.dev/ffmpeg/builds/

# Run in development
dotnet run

# Publish portable exe
dotnet publish djz-vidgrab.csproj -c Release -r win-x64 --self-contained true --property:PublishSingleFile=true --property:IncludeNativeLibrariesForSelfExtract=true -o ./dist/
```

## Tech Stack

| Component | Technology |
|---|---|
| Framework | .NET 8, Windows Forms |
| Screen Capture | GDI+ (CopyFromScreen) |
| Audio Capture | NAudio (WASAPI loopback) |
| Video Encoding | FFmpeg (VP8 + Vorbis → WebM) |
| Global Hotkey | Win32 RegisterHotKey P/Invoke |
| Settings | System.Text.Json |

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{djz_vidgrab,
  title = {djz-vidgrab: Lightweight Windows Screen-Region Recording Utility},
  author = {Drift Johnson},
  year = {2025},
  url = {https://github.com/MushroomFleet/djz-vidgrab},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)

---

## Support This Project

If you found this useful, please **star the repo** — it helps others discover it!

[![Star on GitHub](https://img.shields.io/github/stars/MushroomFleet/djz-vidgrab?style=social)](https://github.com/MushroomFleet/djz-vidgrab)