# Torlink for Windows

**A simple, portable BitTorrent search and download client for Windows.**

Torlink brings torrent searching and downloading into a clean, straightforward desktop application. It is designed to be easy to use, portable, and practical: search from one screen, review results, start downloads, monitor progress, pause and resume transfers, and keep your download location under your control.

> **Legal notice:** Torlink is a tool for downloading and sharing files through BitTorrent. Use it only for content you have the legal right to download, access, or share. The author does not endorse copyright infringement or unlawful use.

![Torlink desktop app](screenshot.png)

## What is Torlink?

The original Torlink project was built primarily around a terminal-based torrent search and download experience. This version takes that underlying functionality and develops it into a **Windows-first graphical application**.

The aim was to make Torlink much easier to use for everyday desktop users without requiring them to work from a command line.

### What I have added and developed

This Windows version includes a substantial desktop layer around the original project, including:

- **Windows desktop GUI** built with Electron
- **Search interface** for finding torrent results without using the terminal
- Searching across multiple configured torrent sources
- Automatic **result deduplication** using torrent info hashes
- Results ranked using **seed availability**
- Magnet-link and torrent download handling
- A dedicated **Downloads** view
- Download queue management
- **Pause and resume** downloads
- Persistent download state between application sessions
- Download history
- Persistent seeding information
- Queue reconciliation when Torlink starts again
- Configurable default download folder
- Windows folder browser for selecting download locations
- Automatic creation of the selected download directory
- Tracker configuration
- WebRTC support and setup handling
- A portable Windows executable
- No installer required for the released application
- No Node.js, npm, or PowerShell required by users running the portable release
- Automated tests and TypeScript type checking
- Build and CI support
- Seeding verification tooling

The goal has been to turn Torlink into a **self-contained Windows application rather than simply providing a terminal interface**.

## Features

### 🔎 Search

Search for titles and keywords from the Torlink interface and receive results from the configured torrent sources.

Results include useful information such as:

- Torrent name
- Source
- File size
- Seeder availability
- Magnet information

Duplicate results are removed using the torrent's info hash, with the strongest result retained.

### 📥 Downloads

Start a download directly from the search results and manage active transfers from the Downloads screen.

Torlink maintains a download queue and allows transfers to be paused and resumed rather than requiring them to be started again from scratch.

### 💾 Persistent downloads

Torlink saves its download state so that the application can restore and reconcile downloads when it is started again.

Download history and seeding information are also persisted rather than disappearing when the application closes.

### 📁 Choose where files are saved

You can choose your preferred download directory from Settings.

For example:

```text
E:\Torrents
```

The folder can be entered manually or selected using the Windows folder browser.

### 🌐 Peer-to-peer networking

Torlink uses peer-to-peer connections to download and seed torrent data. Depending on your Windows and network configuration, Windows Firewall or Windows Security may ask for permission when networking is first used.

Only allow network access when you trust the application and understand your network's policies.

If downloads remain at `0 peers`, the network may restrict peer-to-peer traffic.

## Download Torlink

The easiest way to use Torlink is to download the latest Windows portable release from the GitHub Releases page.

urlDownload Torlink Releaseshttps://github.com/quinnuk/torlink/releases

Look for the latest:

```text
Torlink 1.6.0.exe
```

### Portable application

Torlink is distributed as a portable Windows executable.

You do **not** need to install:

- Node.js
- npm
- PowerShell
- A separate torrent client

Download the executable, run it, choose your download folder, and start searching.

### Windows SmartScreen

Because the executable is distributed independently rather than through the Microsoft Store, Windows SmartScreen may display a warning.

If Windows shows a warning, only choose **More info → Run anyway** when you have obtained the release from the official repository and trust the source.

## First-time setup

1. Start Torlink.
2. Open **Settings**.
3. Under **Default download folder**, select **Browse…** or enter a folder manually.
4. Choose **Save folder**.
5. Open **Search** and enter a title or keyword.
6. Review the available results.
7. Select **Download** on the result you want.
8. Open **Downloads** to monitor the transfer.

That's it. There is no installer or complicated configuration required for the portable release.

## Network access and Windows Security

Torlink needs network access because BitTorrent downloads communicate with other peers.

On a personal Windows PC, Windows may ask whether Torlink should be allowed to communicate on private networks.

A few things to keep in mind:

- Only allow access when you trust the application and the network you are using.
- Organisation-managed computers may prevent you from allowing the connection.
- Downloads can sometimes work with restricted connectivity, but peer availability may be reduced.
- A download showing `0 peers` can be caused by network restrictions as well as a torrent having no currently available peers.

The temporary application path that Windows may display for the portable version is normal.

## Building from source

If you want to build Torlink yourself, you will need **Node.js 22 or later**.

Clone the repository and install the dependencies:

```powershell
npm install
```

Run the graphical application during development:

```powershell
npm run gui
```

Run the test suite:

```powershell
npm test
```

Run TypeScript type checking:

```powershell
npm run typecheck
```

Create the portable Windows application:

```powershell
npm run package:win
```

The resulting Windows executable is placed in:

```text
release
```

## Project structure

The project is organised into separate areas for the desktop interface, downloading, torrent sources, configuration, persistence, and supporting build tools.

Some of the main areas include:

```text
src/
├── cli/              Original command-line functionality
├── config/           Application configuration
├── download/         Download queue and persistence
├── gui/              Windows desktop application
├── sources/           Torrent search sources
└── ...

scripts/
├── ensure-webrtc.cjs
├── postbuild.cjs
├── verify-seeding.ts
└── ...
```

The project also contains automated tests, CI configuration, packaging configuration, preview assets, and the supporting files required to produce the portable Windows build.

## Development focus

This project is not intended to be an attempt to reinvent BitTorrent from scratch.

The focus has been on taking the existing Torlink functionality and building a **better Windows desktop experience around it**:

**Search → choose a result → download → monitor → pause/resume → continue later → seed**

The application is deliberately kept straightforward rather than trying to become an overly complicated all-in-one torrent client.

## Credits

Torlink for Windows builds on the work of the original **[baairon/torlink](https://github.com/baairon/torlink)** project, which provides the underlying torrent search and download functionality.

This repository develops that foundation into a Windows-focused graphical application and adds the desktop interface, download management, persistence, Windows packaging, and supporting functionality described above.

Please see the upstream project for its original implementation and history.

## License

This project retains the upstream **MIT License**.

See [LICENSE](LICENSE) for the full license text.

## Disclaimer

Torlink is general-purpose software for BitTorrent and peer-to-peer file transfers. The software does not determine whether content is legal to download or share.

You are responsible for complying with copyright law, licensing terms, and the rules applicable to the content and networks you use.

---

**Torlink for Windows — simple torrent searching and downloading, without the command line.**
