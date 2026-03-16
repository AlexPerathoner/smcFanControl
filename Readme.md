# smcFanControl Community Edition

**Community-maintained fork of smcFanControl for Intel Macs**

This is a community fork of [hholtmann/smcFanControl](https://github.com/hholtmann/smcFanControl) (2,494 stars), which was abandoned in December 2022. The goal is to keep smcFanControl working on Intel Macs, especially those running [OpenCore Legacy Patcher (OCLP)](https://dortania.github.io/OpenCore-Legacy-Patcher/) on unsupported macOS versions.

smcFanControl lets you set a minimum speed for your Mac's built-in fans to keep it running cooler. It will not let you set fan speeds below Apple's defaults.

## What changed from upstream

- **Stripped Apple Silicon code** -- this fork is Intel-only
- **Fixed 16 deprecated macOS APIs** -- OSSpinLock, IOMasterPort, NSAlert (old-style), NSArchiver/NSUnarchiver, and others
- **Removed dead code** -- SystemVersion parsing, StatusItemWindow, donation prompts, Sparkle auto-updater framework
- **Merged community PRs** -- #143 (SYMROOT fix), #146 (exit if no fans), #108 (floating-point fan speed for newer models)

## Requirements

- Intel Mac (any model)
- macOS 10.7 or higher (tested through macOS Sequoia via OCLP)

## Building

You can build with just Command Line Tools installed -- no full Xcode required.

### GUI app

```bash
clang -fobjc-arc -arch x86_64 \
  -mmacosx-version-min=10.13 \
  -I./smc-command -I./Classes \
  -framework Cocoa -framework IOKit -framework Security \
  main.m smc-command/smc.c \
  Classes/FanControl.m Classes/smcWrapper.m Classes/Power.m \
  Classes/MachineDefaults.m Classes/NSFileManager+DirectoryLocations.m \
  -o smcFanControl
```

This produces a standalone binary. To run as a menu bar app, assemble a `.app` bundle with the binary, Info.plist, and compiled `.nib` resources from the repo.

### smc CLI tool

A standalone command-line tool for reading SMC sensors and setting fan speeds is in `smc-command/`:

```bash
cd smc-command
make
sudo ./smc -l    # list all SMC keys
sudo ./smc -f    # show fan speeds
```

## License

GPL v2 (inherited from upstream).

## Credits

Original by [Hendrik Holtmann](https://github.com/hholtmann). Community fork maintained by [wolffcatskyy](https://github.com/wolffcatskyy).
