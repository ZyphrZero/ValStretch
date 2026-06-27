# ValStretch

[简体中文](README.md) | English

A true stretched resolution tool for VALORANT.

It automatically applies and restores stretched-resolution settings when the game launches and exits, saving you the hassle of manually switching resolutions and repeatedly editing config files.

> This software is completely free. Beware of paid knock-offs that just repackage it.

## Features

- Apply / restore a true stretched resolution in one click.
- Auto mode: applies on game launch, restores on game exit.
- Common 4:3 resolution presets plus a custom target resolution.
- 16:9-to-4:3 mouse sensitivity conversion.
- On-screen notifications, system tray, start-on-boot, and minimize-to-tray.
- Separate config paths for CN (Tencent) and Global (Riot) servers.

## Download & Run

1. Download `valstretch-<version>-windows-x64.zip` from the official release channel.
2. Extract it and run `valstretch.exe`.
3. On first launch, read and accept the notice.
4. Follow the on-screen prompts to pick your VALORANT install or config directory, or use "Auto-detect".

Releases also ship a `SHA256SUMS.txt`. To verify file integrity in PowerShell:

```powershell
Get-FileHash .\valstretch.exe -Algorithm SHA256
```

## How to Use

1. Open the app, go to "Advanced Settings", choose your current server, and fill in your VALORANT install or config directory.
2. Click "Auto-detect" or "Detect config" to confirm the tool found the config file.
3. Pick your target resolution on the main screen.
4. Recommended: turn on "Auto stretch" — it applies on game launch and restores on game exit.
5. For one-off use, click "Manual apply", then "Restore" when you're done.

## Notice

### Background

The 16:9 vs 4:3 debate has been done to death in community videos and threads. Stretched comes with UI crosshair misalignment, cropped visuals, and so on — not going to rehash it here. Players who didn't come from CS generally shouldn't bother.

If you're used to native 16:9 and care about account safety, just stick with native. Nobody's forcing you to switch, and nobody's begging you to use this tool. Save the broken-record takes — "isn't this just editing a file? people got 10-year bans for less", "practice your aim instead of changing ratios" — the kind of zero-thought filler. Use it or don't.

### Risk

On the risk of editing config files: if you're scared, don't use it; if you use it, don't be scared. If you get banned, don't come to me — treat it as a false positive and move on.

The tool does exactly what you'd do by hand: edit the config file and tweak the NVIDIA Control Panel. All I can guarantee is: how you'd do it manually is exactly how the tool does it.

### About the Project

This project exists purely for personal need. I like the 4:3 ratio, so I built the tool. If the logic looks simple to you, just write your own — no need to use this little project.

### Commitments

The tool is free, cloud-free, account-free, and telemetry-free — fully local.

The project is closed-source for now; whether it goes open-source later is to be determined.

## FAQ

### Still seeing black bars?

First make sure the target resolution is a common 4:3 mode your monitor and GPU support, e.g. `1440x1080`, `1280x960`, `1280x1024`.

If you still get black bars, set the scaling mode to "Full" in your GPU control panel or monitor OSD.

### Auto mode not responding?

Check these:

- The correct server is selected.
- The config file was detected.
- The game process actually launched.
- The tool isn't being blocked by antivirus / security software.

### Do I need to manually restore before closing the tool?

If the tool is in an applied state, closing it or turning off auto mode will try to restore automatically. To be safe, in manual mode, click "Restore" once after the game closes.
