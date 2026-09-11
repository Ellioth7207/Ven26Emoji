[![Ven26 iOS Emoji+](module/iOS.jpg)](module/iOS.jpg)

[![Download Ven26 Emoji+](https://img.shields.io/badge/Download-Ven26Emoji%2B-0A84FF?style=flat-square&logo=android&logoColor=white)](../../releases)
[![Support Channel](https://img.shields.io/badge/Telegram-%40vennec-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://t.me/vennec)

---

## Overview

Ven26 Emoji+ is a lightweight, root-based system module for Android that replaces the system emoji set with an iOS 26–style color emoji font. Beyond the standard system-wide font swap, it includes targeted patching for apps that render emoji from their own bundled/cached assets instead of the shared Android font system — most notably the Facebook app family — so the iOS-style emoji actually show up inside those apps as well, not just in the keyboard and native UI.

## Highlights

- System-wide emoji font replacement (`NotoColorEmoji.ttf`) with an iOS 26 emoji set
- OEM-specific font handling for Samsung, LG, and HTC devices
- Dedicated patching for the Facebook app family:
  - Facebook
  - Messenger
  - Facebook Lite
  - Messenger Lite
- SELinux-context-aware font binding, so sandboxed apps can actually read the replaced font instead of silently ignoring it
- Blocks Facebook/Messenger from re-downloading their own bundled emoji font over the patch
- Disables the GMS font provider services that can otherwise overwrite the patch
- On-device debug log for troubleshooting which apps did or didn't get patched
- Minimal footprint, no persistent background overhead

## Module Information

| Field           | Value                                    |
| --------------- | ----------------------------------------- |
| Name            | Ven26 iOS Emoji+                          |
| Module ID       | `ven_ios_emoji`                           |
| Version         | E.O.L_EXTENDED_FBfix                      |
| Version Code    | 1230                                      |
| Author          | [@vennec](https://t.me/vennec)            |
| Status          | Stable (Facebook/Facebook Lite fix build) |
| Minimum Magisk  | 20200                                     |
| Emoji base      | Noto Color Emoji + iOS-style glyph set    |

## Compatibility

| Manager  | Notes                                  |
| -------- | --------------------------------------- |
| All Root Manager | 

Root access is required. This module relies on runtime bind-mounts into other apps' private data directories, which is not achievable without root.

## Repository Structure

```
ven26-emoji-eol/
├── module/                  # Module source — this is what gets zipped for flashing
│   ├── META-INF/            # Magisk installer, do not edit
│   ├── system/fonts/        # NotoColorEmoji.ttf, FacebookEmoji.ttf
│   ├── bind_helpers.sh      # Shared helpers: SELinux-safe bind_font()
│   ├── config.sh            # Magisk install-time configuration
│   ├── fallback.xml         # Emoji fallback entry for system fonts.xml
│   ├── module.prop          # Module metadata
│   ├── post-fs-data.sh      # Runs at early boot, before Zygote
│   └── service.sh           # Runs at late_start, after boot completes
├── docs/
│   └── TROUBLESHOOTING.md
├── .github/workflows/       # CI: builds & publishes the flashable zip on tag push
├── CHANGELOG.md
└── LICENSE
```

## Installation

1. Download the latest release from the link above.
2. Open Magisk → **Modules** → **Install from storage**.
3. Select the downloaded zip and wait for installation to finish.
4. **Reboot** the device.
5. Open Facebook / Facebook Lite / Messenger / Messenger Lite. If an app was already running before the reboot, force-stop and reopen it.

If emoji still don't change inside a specific app, check `/sdcard/Ven26_Emoji_debug.log` and see [`docs/TROUBLESHOOTING.md`](docs/TROUBLESHOOTING.md).

## Changelog

### 1230 — E.O.L_EXTENDED_FBfix

- Fixed: Facebook and Facebook Lite not receiving the emoji patch — bind-mounted files weren't retaining a usable SELinux context inside those apps' sandboxes
- Fixed: missing `fallback.xml` referenced by `post-fs-data.sh`
- Facebook Lite / Messenger Lite now patched at early boot (`post-fs-data.sh`), not only at late_start
- Added on-device debug logging
- Added CI build/release workflow and full documentation

### 1229 — E.O.L_EXTENDED

- Original release

See [`CHANGELOG.md`](CHANGELOG.md) for full details.

## Attribution and Redistribution Policy

Re-uploading, mirroring, or redistributing this module is permitted under the following terms.

**Attribution is required.** Every redistribution must clearly and visibly credit the original source:
> Source: @vennec

This attribution must not be removed, hidden, or replaced.

**Not permitted:**

- Claiming this module as original work
- Removing, hiding, or replacing the `@vennec` attribution
- Presenting a modified build as an official, unmodified release
- Removing the original source or download information

This repository is an independently fixed build (see Changelog); it is not an official release channel for the original author.

## Disclaimer

This module modifies Android system behavior and binds files into other apps' private storage. The maintainers of this repository assume no responsibility for bootloops, system instability, data loss, device malfunction, incompatibility with specific devices, conflicts with other modules, or any other damage resulting from its use. Install and use at your own risk.

`system/fonts/FacebookEmoji.ttf` is an asset originally extracted from the Facebook app and remains the property of Meta; it is not covered by this repository's license (see [`LICENSE`](LICENSE)).

## Credits

| Role                         | Handle                          |
| ---------------------------- | -------------------------------- |
| Original module & concept    | [@vennec](https://t.me/vennec)   |
| Base emoji font               | [Noto Color Emoji](https://github.com/googlefonts/noto-emoji) (Google) |
| Facebook/Facebook Lite fix, docs, CI | this repository's contributors |

---

Copyright © vennec. Attribution terms above apply to any redistribution of this project.

[![Donate](https://img.shields.io/badge/Donate-QRIS-FF9500?style=flat-square)](https://i.ibb.co.com/SDvYYW78/qr-ID1026576754000-26-08-26-1787677910-1787677910913.jpg)
