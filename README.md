# SSTVRx

Browser-based HF SSTV decoder for KiwiSDR streams.

`SSTVRx` is a single-file web app (`sstv-decoder.html`) that connects to public/private KiwiSDR receivers, demodulates SSTV audio, and renders received images live.

## Features

- Live SSTV decode over KiwiSDR WebSocket audio
- VIS detection + mode auto-detect
- Supported modes:
  - Robot 36
  - Robot 72
  - Martin M1 / M2
  - Scottie S1 / S2 / DX
- Spectrum + waterfall + live tone/status panel
- Auto squelch toggle with manual threshold slider
- Received image gallery
- Demo mode (synthetic Robot 36 signal)
- Public receiver browser + host preflight checks
- Small 20m propagation side panel

## Requirements

- Modern Chromium/Edge/Firefox browser
- Network access to KiwiSDR hosts
- Audio output enabled in browser/tab

## Quick Start

1. Open `sstv-decoder.html` in a browser.
2. Enter a KiwiSDR host (or pick one from the receiver browser).
3. Set:
   - Frequency: `14230` kHz
   - Mode: `USB`
4. Click `CONNECT`.
5. Wait for VIS lock and image decode.

You can also click `DEMO` to validate the decoder/UI without RF conditions.

## Important Connection Note

Many KiwiSDR endpoints are plain `ws://` only.  
If you open this app from an `https://` page, your browser may block mixed-content WebSocket audio.

Use one of these:

- Local file (`file://.../sstv-decoder.html`)
- Local plain HTTP server (`http://localhost:...`)

## Controls

- `AUTO SQUELCH`: enable/disable gate control
- Squelch slider: set open threshold in dBm
- `DEMO`: run built-in synthetic transmission
- `CLEAR`: clear received image gallery

## Troubleshooting

- Stuck on `Waiting for VIS leader`:
  - Verify strong SSTV audio on 14.230 MHz USB
  - Try another KiwiSDR host
  - Lower squelch threshold or disable auto squelch
- Repeated disconnects:
  - Receiver may be full/offline/locked
  - Try another host from the browser list
- No audio/decoding:
  - Confirm browser audio permission/output
  - Refresh page and reconnect

## Project Structure

- `sstv-decoder.html`: full app (UI + decoder + KiwiSDR client + visualization)

No build step is required.

## License

This project is licensed under the **MIT License** (OSI-approved, permissive open source).
See `LICENSE` for the full text.
