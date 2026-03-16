# smcFanControl Community Edition

Community-maintained fork of [smcFanControl](https://github.com/hholtmann/smcFanControl) for Intel Macs.

Set a minimum fan speed to keep your Mac running cooler. Will not let you go below Apple's defaults.

## Size Comparison

| Build | Size |
|-------|------|
| Original smcFanControl | ~5.7 MB (bundled Sparkle framework) |
| Community Edition | ~368 KB |
| **Reduction** | **~94%** |

## Download

Download the latest release from [GitHub Releases](https://github.com/wolffcatskyy/smcFanControl/releases).

### Install

1. Download the .zip from Releases
2. Extract and drag smcFanControl.app to /Applications
3. Right-click the app and choose Open (bypasses Gatekeeper on first launch)

The app runs in the menu bar (no Dock icon).

### smc CLI

A standalone command-line tool for reading SMC sensors and fan speeds is also available in the release.

## What changed from upstream

- Stripped Apple Silicon code (Intel-only fork)
- Fixed 16 deprecated macOS APIs
- Removed Sparkle auto-updater framework (5.3 MB)
- Removed dead code (donation prompts, unused classes)
- Merged community PRs #143, #146, #108
- Modern UI: SF Symbol fan icon (macOS 11+), system fonts, dark mode support
- Icon-only menu bar mode (no temp/RPM display, minimal CPU usage)
- Fixed auth error (-60007) on modern macOS

## License

GPL v2 (inherited from upstream).

## Credits

Original by [Hendrik Holtmann](https://github.com/hholtmann). Community fork by [wolffcatskyy](https://github.com/wolffcatskyy).
