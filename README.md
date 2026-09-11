<div align="center">
  <img src="https://i.ibb.co.com/B5w8YpQQ/quality-restoration-20260911171625806.jpg"
 alt="VenForce" width="100%">
</div>

<div align="center">

<a href="https://sfl.gl/zrLiDYoa"><img src="https://img.shields.io/badge/Download-TapHere-0A84FF?style=flat-square&logo=android&logoColor=white" alt="Download Ven26Emoji" style="border:2px solid #0A84FF;border-radius:8px;padding:2px;"></a>
<a href="https://t.me/Vennec"><img src="https://img.shields.io/badge/Telegram-@VENNEC-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Support Channel" style="border:2px solid #0A84FF;border-radius:8px;padding:2px;"></a>

</div>

# Ven26 Emoji

**Ven26 Emoji** is a root module that brings the iOS 26 emoji style to Android devices. It replaces the system emoji font at the OS level and patches emoji rendering inside select messaging apps, so iOS-style emoji appear consistently across the system keyboard, notifications, and supported apps — without needing per-app workarounds.

## Overview

| | |
|---|---|
| **Module ID** | `ven_ios_emoji` |
| **Name** | Ven 26 Emoji+ |
| **Version** | 18.0 |
| **Author** | [@vennec](https://t.me/Vennec) |
| **Minimum Magisk** | 20200 |

## Features

- **System-wide emoji replacement** — Bind-mounts the iOS-style emoji font over the system emoji font at `/system/fonts`, `/system/product/fonts`, and `/product/fonts`, so the new style applies system-wide without directly overwriting the partition.
- **OEM font alias coverage** — Automatically generates aliases for the font (Samsung, LG, HTC, DCM, and other OEM-specific emoji font filenames), ensuring the replacement applies correctly across different device brands and skins.
- **In-app emoji patching** — Replaces the bundled emoji font used by Facebook, Messenger, Facebook Lite, and Messenger Lite, targeting both known font paths and any additional emoji font files discovered automatically within app data.
- **Automatic cache cleanup** — Clears system and Google Play Services font caches so the new emoji style is picked up without manual intervention.
- **Boot-time automation** — Applies all changes automatically once the device finishes booting, and can be re-triggered manually at any time via the module's Action button.
- **Custom WebUI** — An animated, interactive module interface with quick-access Donate and Telegram support buttons.

## Installation

1. Download the module using the **Download** button above.
2. Flash the ZIP file through your root manager (Magisk, KernelSU, or a compatible alternative).
3. Reboot your device.
4. Emoji replacement is applied automatically after boot. If any app still shows the old emoji style, force-stop or restart that app.

## How It Works

On first boot after installation, and on every subsequent boot, the module's service script waits for the system to finish starting, then:

1. Bind-mounts the iOS-style emoji font over the relevant system font paths.
2. Replaces the bundled emoji font inside Facebook and Messenger app data (including Lite variants).
3. Clears cached font data so changes take effect immediately.
4. Force-stops the affected apps so they reload with the new font on next launch.

The same routine can be re-run at any time through the module's **Action** button in your root manager, without requiring a full reboot.

## Compatibility

Ven26 Emoji+ follows the standard Magisk module format and is compatible with:

- Magisk
- KernelSU (including KernelSU Next)
- APatch and other managers supporting the standard root module format

## Attribution and Redistribution Policy

Re-uploading, mirroring, or redistributing Ven26 Emoji+ is permitted under the following terms.

Attribution is required. Every redistribution must clearly and visibly credit the original source:

```
Source: @vennec
```

This attribution must not be removed, hidden, or replaced.

**Not permitted:**

- Claiming Ven26 Emoji+ as original work
- Removing, hiding, or replacing the `@vennec` attribution
- Presenting an unofficial build as an official Ven26 Emoji+ release
- Removing the original source or download information
- Changing, shortening, redirecting, or hiding the official links without authorization
- Using modified links in a way that misleads users about the project's origin

## Link Policy

Official links associated with Ven26 Emoji+ (download, source, and release links) must not be changed, replaced, shortened, redirected, or hidden without prior written permission from Telegram: **@ellioth7207**. This applies to links in redistribution posts and repackaged copies of the module alike.

## Disclaimer

Ven26 Emoji+ modifies system-level emoji fonts and patches font files within select app data. The author assumes no responsibility for bootloops, system instability, data loss, device malfunction, incompatibility with specific devices, emoji rendering issues, conflicts with other modules, or any other damage resulting from use of this module. Install and use at your own risk.

## Credits

| Role | Handle |
|---|---|
| Development and maintenance | [@vennec](https://t.me/Vennec) |
| Link authorization | @ellioth7207 |

---

<div align="center">

Copyright © vennec. Attribution terms above apply to any redistribution of this project.

[![Donate](https://img.shields.io/badge/Donate-QRIS-FF9500?style=flat-square)](https://i.ibb.co.com/SDvYYW78/qr-ID1026576754000-26-08-26-1787677910-1787677910913.jpg)

</div>
