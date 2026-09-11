# ValStretch

[简体中文](README.md) | English

🎮 A true stretched resolution tool for VALORANT.

It automatically applies and restores stretched-resolution settings when the game launches and exits, saving you the hassle of manually switching resolutions and repeatedly editing config files.

> ⚠️ This software is completely free. Beware of paid knock-offs that just repackage it.

## ✨ Features

- ⚡ Apply / restore a true stretched resolution in one click.
- 🔁 The default disable-monitor route supports auto stretch: bind the CN or Global server on the Auto page, track the local game PID, and restore the Monitor devices and original desktop mode after the game exits.
- 🖥️ NVIDIA / AMD driver-mode management, common 4:3 presets, and custom resolutions.
- 🛠️ Enabling auto stretch automatically checks and repairs every detected game config — no separate config-fix step. You can also turn off "Allow cfg modification" on the Auto page to manage displays and resolutions only.
- ⌨️ Per-resolution global hotkeys in the Manual view of the disable-monitor route.
- 🖱️ 16:9-to-4:3 conversion and bidirectional CS2 / VALORANT mouse-sensitivity conversion.
- 🔔 On-screen notifications, system tray, start-on-boot, and minimize-to-tray.
- 📂 Separate config paths for CN (Tencent) and Global (Riot) servers.
- 🚀 A Windows performance page for Game Mode, controller-launched Game Bar, background capture, and the High Performance power plan.
- 🌍 UI available in Simplified Chinese, Traditional Chinese (TW / HK), English, Japanese, Korean, and Russian.

## 📥 Download & Run

1. Download the latest `valstretch-<version>-windows-x64.zip` from [Releases](https://github.com/ZyphrZero/ValStretch/releases).
2. Extract it and run `valstretch.exe`.
3. On first launch, read and accept the notice.
4. Follow the on-screen prompts to pick your VALORANT install or config directory, or use "Auto-detect".

Every release also ships a `SHA256SUMS.txt`. To verify file integrity in PowerShell:

```powershell
Get-FileHash .\valstretch.exe -Algorithm SHA256
```

## 📖 How to Use

### 🎯 Recommended: Disable-monitor Route (Default)

1. Keep the default "Disable-monitor route" under Advanced Settings. Click "Auto-detect", or configure the CN and Global install/config directories separately; then pick the server to bind in "Auto region" on the Auto page. Directories assist config repair and are not a hard prerequisite for auto mode.
2. Add the final mode under "Pre-create resolutions" in the Auto view. `1440x1080` or `1920x1440` is recommended. If an exact matching driver mode already exists, ValStretch registers and reuses it.
3. Click "Set target" beside the desired entry under "Available resolutions". `1280x882` is the guide mode used by the automatic sequence and cannot be selected as the final target.
4. Adjust the guide-resolution delay when needed. `3000-5000ms` is recommended so the game window has time to finish adopting the guide mode.
5. Turn on "Auto stretch". ValStretch first repairs the detected configs, then applies the guide and target modes for the bound server via the local PID, and restores the Monitor devices and original desktop mode when the game exits.

🖥️ In the game's Video settings, set the display mode to "Fullscreen Windowed (Borderless)" and the aspect ratio method to "Fill"; other combinations may not take effect.

🔎 Multi-display users note: all monitors are temporarily stopped while auto stretch is active. Keep VALORANT on the Windows primary display, otherwise the switch times out and auto-restores.

🛠️ If you prefer the tool not to touch game configs, turn off "Allow cfg modification" on the Auto page: the auto route still manages Monitor devices and display modes but never reads or writes `GameUserSettings.ini`.

If a config file is read-only, a directory is missing, or the process path cannot be queried, auto stretch shows a warning with the exact path and cause but does not stop; Monitor and desktop-mode handling continues for the bound server. Close the game, clear the file's "Read-only" attribute or provide the directory, then re-enable auto stretch to retry the repair.

If ValStretch reports that the `[/Script/ShooterGame.ShooterGameUserSettings]` section is missing, do not add the section manually. Fully exit VALORANT and Riot Client, then rename the reported `GameUserSettings.ini` to `GameUserSettings.ini.broken` as a backup. Start VALORANT for the affected region once, enter the main menu, save any game setting, and exit normally. After the game regenerates the complete config, enable auto stretch again.

### 🖱️ Manual Use

In the Manual view, you can disable or re-enable monitor devices, apply a registered resolution, and explicitly restore the original resolution. If you enable auto stretch while a manual disable-monitor transaction is still active, ValStretch first tries to restore it. If recovery fails, return to Manual, click "Enable monitors", confirm recovery succeeds, and try again.

The legacy config-file route remains available under Advanced Settings, but the disable-monitor route is the default and recommended workflow. The two routes have independent transaction and recovery behavior.

The main window uses the same application-drawn borderless title bar on Windows 10 and Windows 11: drag the blank title-bar area to move it, drag any window edge to resize it, and the window size is remembered. Minimize and close remain in the title bar, and close still follows the "Minimize panel to tray on close" setting.

### ⚡ Performance Optimization

Open the performance page from the title bar to read four current Windows states. Toggling a switch immediately synchronizes the corresponding Windows setting in a background task and verifies it. ValStretch changes only the current user's Game Mode settings, the controller entry for Game Bar, Game DVR/background capture, and the active power plan. "Disable controller-launched Game Bar" disables the Windows "allow controllers to open Game Bar" entry but does not uninstall Game Bar or block `Win+G`.

Each switch is the target state for its Windows feature. ValStretch writes and verifies that target immediately; it does not save or restore original performance settings. If a write or verification partially fails, already written items are not rolled back. Resolve the reported issue, refresh the page, and toggle the affected switch again. Turning off the high-performance switch selects Windows' built-in Balanced plan. Settings that already match a target are never forcibly reversed, so the Windows state column may still show Game Mode on, the controller entry off, capture off, or the High Performance plan active.

### ⌨️ Disable-monitor Route Hotkeys

Click the keyboard icon beside a resolution under "Available resolutions", press the desired shortcut, and save it. Supported primary keys include `A-Z`, `0-9`, `F1-F24`, and common punctuation, with optional `Ctrl`, `Alt`, `Shift`, or `Win` modifiers. Letters follow the current keyboard layout; digits, function keys, and punctuation follow their physical main-keyboard positions. An unmodified single key becomes a system-wide hotkey and may prevent other applications from receiving it.

Hotkeys are active only while ValStretch is running, the disable-monitor route is selected, and the Manual view is open. Switching to Auto unregisters them. They still work while the window is minimized, hidden in the tray, or VALORANT is in the foreground. A hotkey changes only the primary display's resolution, color depth, and refresh rate, while retaining the snapshot needed by "Restore original resolution". It does not edit VALORANT config files or change NVIDIA scaling settings.

## ⚠️ Notice

### 📌 Background

The 16:9 vs 4:3 debate has been done to death in community videos and threads. Stretched comes with UI crosshair misalignment, cropped visuals, and so on — not going to rehash it here. Players who didn't come from CS generally shouldn't bother.

If you're used to native 16:9 and care about account safety, just stick to native. Nobody's forcing you to switch, and nobody's begging you to use this tool. Save the broken-record takes — "isn't this just editing a file? people got 10-year bans for less", "practice your aim instead of changing ratios" — the kind of zero-thought filler. Use it or don't.

### 🌐 Internet-café notice

Most internet cafés run diskless systems where game configs (cfg) cannot be modified, so auto mode may not work there. Use manual mode instead.

### 🍀 Risk

On the risk of editing config files: if you're scared, don't use it; if you use it, don't be scared. If you get banned, don't come to me — treat it as a false positive and move on. 😀

Every operation is local to your PC. Depending on the selected route, ValStretch performs the same categories of action you would do manually: edit game configuration, manage GPU display modes, and switch Windows display modes. Understand the selected route and its recovery behavior before using it. 🫡

How it works (Bilibili video, in Chinese): [BV1d6NR6wECk](https://www.bilibili.com/video/BV1d6NR6wECk)

Tutorial (Bilibili video, in Chinese): [BV1r4Ks6pEn5](https://www.bilibili.com/video/BV1r4Ks6pEn5)

### 💡 About the Project

This project exists purely for personal need. I like the 4:3 ratio, so I built the tool. If the logic looks simple to you, just write your own — no need to use this little project.

### 🤝 Commitments

The tool is free, cloud-free, account-free, and telemetry-free — fully local.

The project is closed-source for now; whether it goes open-source later is to be determined.

## ❓ FAQ

### 🖼️ Still seeing black bars?

First make sure the target resolution is a mode your monitor and GPU support, e.g. `1440x1080`, `1280x960`, or `1920x1440`.

If black bars still appear, enable the NVIDIA scaling override option under "Advanced settings" in ValStretch. This option reads and writes the NVIDIA driver setting directly, so it stays in sync with NVIDIA Control Panel / NVIDIA App, and remains unchanged when the game or ValStretch exits.

If black bars remain after enabling the override, check that the scaling mode in NVIDIA Control Panel or NVIDIA App is set to "Full", and also check your monitor's OSD scaling settings.

### 🤔 Auto mode not responding?

Check these:

- "Auto region" on the Auto page has a server selected. Directory detection assists config repair; even with no directory found, Monitor auto mode does not stop merely because configs are missing.
- A target resolution was created and explicitly selected with "Set target". `1280x882` cannot be the target.
- The game process and its window actually launched, and antivirus/security software is not blocking ValStretch.
- On multi-display setups, VALORANT is on the Windows primary display.
- The config file is not marked read-only. The error notification and log include the exact failing path.
- No manual monitor or original-resolution transaction is still waiting to be restored.

After an application failure for a specific game PID, ValStretch does not retry that PID because repeated mode switches would cause flicker. Follow the reported error, fully exit VALORANT, and launch it again.

### 🔒 Why does it report a read-only config file?

The Windows "Read-only" attribute prevents the atomic config update. Close the game, locate `GameUserSettings.ini` using the full path in the error, clear "Read-only" in the file's Properties, and enable auto stretch again. A failed repair does not stop the Monitor auto flow, and ValStretch does not misreport the write failure as a directory-detection failure.

### ↩️ Do I need to manually restore before closing the tool?

Auto mode attempts to restore the Monitor devices disabled by the current cycle and the complete original desktop mode when the game exits, auto stretch is disabled, or ValStretch closes.

Manual mode is different: closing the app attempts to re-enable the monitors disabled by the manual transaction, but it does not automatically clear or restore the manual desktop-mode snapshot. Before finishing, click "Restore original resolution" and, if needed, "Enable monitors".
