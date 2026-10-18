# Attix Connector — Releases

This repository hosts the **official Attix Connector installers** and update files. It does **not contain source code**.

➡️ **[Download the latest version](../../releases/latest)**

## What is Attix Connector?

**Attix Live** is the tournament and match production platform. **Attix Connector** is a small application to install on the caster's or production team's PC, alongside **OBS Studio**. It acts as a secure bridge between Attix Live (in the browser) and OBS (on your computer):

- 🔗 **Code-based pairing**: link the application to your Attix account without ever entering your password into it.
- 🎬 **Control OBS from the Production Console**: switch scenes, show/hide a source, and (if you allow it) start/stop the stream.
- 📡 **Live status**: the website can see whether OBS is connected, which scene is active, and whether you are live.
- 🔄 **Automatic updates**, never during a production session.
- 🌗 Light/dark theme, menu bar icon.

## Installation

You need an **Attix** account and **OBS Studio 28 or later** with the WebSocket server enabled (OBS → Tools → *WebSocket Server Settings* → *Enable WebSocket server*, port `4455`).

Choose the file for your machine from the [latest release](../../releases/latest):

| System | File |
|---|---|
| macOS (Apple M1, M2, M3… chip) | `.dmg` containing `aarch64` |
| macOS (Intel Mac) | `.dmg` containing `x64` |
| Windows | `.msi` or `-setup.exe` |
| Linux | `.deb`, `.rpm` or `.AppImage` |

**macOS** — the application has not yet been notarized by Apple: macOS may block it the first time you open it. Go to *System Settings → Privacy & Security* and click **“Open Anyway”** (the wording varies depending on your macOS version). After an update, macOS may ask for keychain access again: allow it.

**Windows** — SmartScreen may display “Windows protected your PC”: click *More info → Run anyway*.

**Linux** — the application stores its secrets in the system's *Secret Service* (GNOME Keyring or KWallet), available on common desktop environments. For an `.AppImage`: run `chmod +x`, then launch it. On GNOME, the menu bar icon requires the “AppIndicator” extension.

## First launch

1. **Sign in to Attix** → a code will appear.
2. On [live.attix.gg](https://live.attix.gg): *Settings → Devices*, enter the code.
3. The application switches to “Connected”. You can name the device on the website.
4. **OBS Studio**: enter the address (`ws://127.0.0.1:4455`) and OBS's WebSocket password, then click *Connect OBS*. Check **“Remember and reconnect automatically”** if you want this to happen automatically each time you launch the application.
5. Under **Remote Production**, choose what Attix is allowed to do on this computer.

## Security and privacy

- **Your OBS password never leaves your computer.** It is stored in your system's secure keychain, just like the pairing secret. Neither is sent to Attix.
- **You're in control**: switching scenes and showing/hiding sources are allowed by default; **remotely starting/stopping the stream is disabled** until you check the box.
- A command received more than **30 seconds** after it was sent is ignored.
- **Lost device?** Revoke it from the website: the application disconnects automatically.
- Updates are **signed**: the application rejects any file that does not match the embedded public key.

**What the application sends to Attix**: its version and your operating system, OBS status (connected or not, version, active scene, scene names, whether a stream is running), what you allow remotely, and the results of received commands. **Never**: OBS password, stream key, video, or audio.

## Updates

The application checks for a new version 15 seconds after startup, then every 6 hours. You decide when to install it; installation is refused during a live production session.

> ⚠️ **Do not manually delete or modify this repository's releases.** Installed applications read the `latest.json` file from the latest release to determine whether an update is available. Releases are published automatically by the project's CI.

## Release contents

The installers, a `latest.json` file (update URLs and signatures), and the corresponding `.sig` files.

## Help

- Installation or pairing issues: *[contact or support link to be provided]*
- License and terms of use: *[to be provided]*
