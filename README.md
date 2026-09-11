<div align="center">
  <img src="https://i.ibb.co.com/B5w8YpQQ/quality-restoration-20260911171625806.jpg" alt="VenForce" width="100%">
</div>

<div align="center">

<a href="https://sfl.gl/zrLiDYoa"><img src="https://img.shields.io/badge/Download-TapHere-0A84FF?style=flat-square&logo=android&logoColor=white" alt="Download Ven26Emoji" style="border:2px solid #0A84FF;border-radius:8px;padding:2px;"></a>
<a href="https://t.me/Vennec"><img src="https://img.shields.io/badge/Telegram-@VENNEC-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Support Channel" style="border:2px solid #0A84FF;border-radius:8px;padding:2px;"></a>

</div>

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
| Version         | E.O.L_HOTFIX                      |
| Version Code    | 1229                                      |
| Author          | [@vennec](https://t.me/vennec)            |
| Status          | Stable - A10-17 Support |
| Minimum Magisk  | 20200                                     |
| Emoji base      | Noto Color Emoji + iOS-style glyph set    |

## Compatibility

|      Manager     |
| -----------------|
| All Root Manager | 

Root access is required. This module relies on runtime bind-mounts into other apps' private data directories, which is not achievable without root.

## Structure

```
ven26-emoji-eol/
├─ ven_ios_emoji/                  
   ├── META-INF/            
   ├── system/fonts/        
   ├── bind_helpers.sh      
   ├── config.sh            
   ├── fallback.xml         
   ├── module.prop          
   ├── post-fs-data.sh      
   └── service.sh           
```

## Installation

1. Download the latest release from the link above.
2. Open Magisk → **Modules** → **Install from storage**.
3. Select the downloaded zip and wait for installation to finish.
4. **Reboot** the device.
5. Open Facebook / Facebook Lite / Messenger / Messenger Lite. If an app was already running before the reboot, force-stop and reopen it.

If emoji still don't change inside a specific app, check `/sdcard/Ven26_Emoji_debug.log` and see [`docs/TROUBLESHOOTING.md`](docs/TROUBLESHOOTING.md).

## Changelog

### E.O.L_HOTFIX

- Fixed: Facebook and Facebook Lite not receiving the emoji patch — bind-mounted files weren't retaining a usable SELinux context inside those apps' sandboxes
- Fixed: missing `fallback.xml` referenced by `post-fs-data.sh`
- Facebook Lite / Messenger Lite now patched at early boot (`post-fs-data.sh`), not only at late_start
- Fix Black Emoji
- Added on-device debug logging
- Added CI build/release workflow and full documentation

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
