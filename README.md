# Boof Boof

**A free clipboard history for macOS.** Keep copied text, links, and images close at hand in a small menu bar popover.

> **Free to download. No subscription, account, cloud history, or sync.** Clipboard history stays on this Mac.

[Download Boof Boof](docs/downloads/BoofBoof.dmg) · [Product page](docs/index.html)

![Boof Boof app icon](docs/assets/boof-icon.png)

## What it does

- Keeps a local history of copied plain text, web links, and supported images.
- Opens from the macOS menu bar; there is no separate main history window.
- Search text and links, then click an entry to put it back on the system clipboard.
- Pin useful entries, remove individual items, clear unpinned entries, or clear all history.
- Pause and resume clipboard capture at any time.
- Choose a history limit of 50, 100, 250, or 500 unpinned entries and a retention period of 10, 30, 90, or 365 days, or indefinitely. Pinned entries are excluded from these count and age limits.

## Images

Boof Boof can save and restore PNG, JPEG, HEIC, WebP, and TIFF images copied from supported apps, including browsers and Finder. Finder image files are copied into Boof Boof's own local storage; the original file path is not used as the saved image.

Image limits are **10 MiB per image**, **100 MiB total image storage**, and **40 megapixels per image**. Images that exceed a limit or cannot be safely decoded are skipped. Supported image payloads are restored to the system clipboard as images, ready to paste.

Animated GIF, SVG, PDF, video, arbitrary files, rich-text fidelity, and arbitrary clipboard formats are not supported in this release.

## Privacy and storage

- History is stored locally under `~/Library/Application Support/BoofBoof/` (`history.json` plus an `Images` folder when needed).
- The app does not upload, sync, or send clipboard history to a server.
- No account, analytics service, cloud database, or background sync is included.
- The local history is **not separately encrypted**. Protect your macOS account and use FileVault if you want disk encryption.
- The app skips recognized concealed or temporary clipboard markers when present. These markers are best-effort; they are not a guarantee that every sensitive item can be detected.
- Clipboard changes are checked approximately every 0.75 seconds. Rapid successive copies or app-specific clipboard behavior can cause gaps; Boof Boof does not claim to capture every format or every copy.

## System requirements

- macOS 13 or newer
- Intel Macs (`x86_64`) and Apple Silicon Macs (`arm64`); the download is a universal app
- No Xcode installation is required to run the downloaded app

## Install

1. Download `BoofBoof.dmg` from the link above.
2. Open the disk image and drag **Boof Boof.app** into **Applications**.
3. Eject the disk image and launch Boof Boof from Applications.

### First-launch security notice

The currently prepared build is ad-hoc signed and has not been notarized by Apple. Gatekeeper may show a warning when the downloaded app is opened. This is a personal distribution build, not an Apple-notarized release. For a smoother public installation, the app should be signed with a Developer ID certificate and notarized before the release is published.

## Technical notes

- **Language/UI:** Swift, SwiftUI, and AppKit.
- **Clipboard monitoring:** reads the public `NSPasteboard.general` pasteboard and checks its change count on a 0.75-second timer; reads clipboard contents only after a detected change.
- **Text size cap:** 1 MiB per item.
- **History defaults:** 50 unpinned items and 10 days. Both can be changed in Settings.
- **Image representations:** PNG, JPEG, HEIC, WebP, and TIFF; Finder file copies are read and stored as local image bytes.
- **No synthetic paste:** selecting an entry restores it to the system clipboard. The app does not send Command-V to another application.
- **Distribution:** universal `x86_64` + `arm64` `.app` in a compressed `.dmg`.

## Price

Boof Boof is free. If you find it useful, you can optionally [buy the developer a coffee](https://www.donationalerts.com/r/atticusrock).

## Project status

This is an early, evolving macOS utility. Clipboard formats and behavior vary across apps and macOS releases. Please report a reproducible issue with the macOS version and the source app; do not include private clipboard contents in a report.
