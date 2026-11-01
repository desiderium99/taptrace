<h1 align="center">TapTrace</h1>
<p align="center"><strong>Your inputs. In the spotlight.</strong></p>

<p align="center">
  <img alt="Windows 10 and 11" src="https://img.shields.io/badge/Windows-10%20%2F%2011-ff6073?style=flat-square">
  <img alt="C# and WPF" src="https://img.shields.io/badge/Built%20with-C%23%20%2B%20WPF-af91ff?style=flat-square">
  <img alt="Portable" src="https://img.shields.io/badge/Portable-No%20installer-58e4bb?style=flat-square">
</p>

**TapTrace** is a lightweight Windows overlay that shows your keyboard and mouse presses in real time. Keep your movement and clicks visible with a compact layout designed around the inputs you use in VALORANT.

<p align="center">
  <img src="assets/overlay-preview.png" alt="TapTrace with W, Left Shift, and LMB highlighted in coral" width="230">
  <br>
  <sub>A preview with W, Left Shift, and LMB pressed.</sub>
</p>

## ✨ What it does

- **Live highlights** — display individual presses and combinations, with brief highlights that make quick taps easier to see.
- **Transparent, always-on-top overlay** — drag your inputs into place, then lock the overlay so clicks pass through.
- **Custom appearance** — adjust size and opacity, and choose Coral, Mint, or Lilac highlights.
- **Saved preferences** — keep your position and appearance between sessions.
- **Tray controls** — hide the settings panel while the overlay keeps running.

### Supported inputs

| Keyboard | Mouse |
| :--- | :--- |
| **W · A · S · D** | **LMB** — left click |
| **Left Shift** | **RMB** — right click |
| **Left Ctrl** | **M4** — back button |
| | **M5** — forward button |

Left and right modifiers are distinguished: Right Shift and Right Ctrl do not light the left-side indicators.

## 🚀 Get started

1. Extract the ZIP and open **`taptrace-app`**.
2. Keep `TapTrace.exe` and `TapTrace.exe.config` together, then run **`TapTrace.exe`**.
3. Press **F8** to unlock the overlay, drag it into place, then press **F8** again to lock it.
4. Press **F10** to customize its appearance.

**Requirements:** 64-bit Windows 10 or 11 with .NET Framework 4.8. Running the app does not require Node, Python, or a .NET SDK.

## ⌨️ Shortcuts

| Shortcut | Action |
| :--- | :--- |
| **F8** | Lock / unlock positioning and click-through |
| **F9** | Show / hide the overlay |
| **F10** | Open settings |

When unlocked, right-click the overlay to open settings. Closing settings leaves TapTrace in the system tray; use **Quit** to exit. If a shortcut is already in use, the tray menu provides the same controls.

## 🎮 Using it with VALORANT

Use **windowed or borderless windowed mode** so the desktop overlay can remain visible. Exclusive fullscreen may cover it.

If the overlay stays visible but stops highlighting presses, check the permission status in settings. When VALORANT runs as administrator, use **Restart as administrator** and approve the Windows prompt to run TapTrace at the same level.

The panel also shows keyboard and mouse event counts to help check whether input is arriving. TapTrace uses Windows Raw Input for background events; game compatibility still needs to be checked on your setup.

## 🔒 Local by design

TapTrace does not record typed text, send input data over the network, install a driver, or inject code into games. Event counts exist only in memory. Preferences are stored at:

```text
%LOCALAPPDATA%\TapTrace\settings.xml
```

<details>
<summary><strong>Build from source</strong></summary>

Open PowerShell in `taptrace-src` (or the repository root containing `build.ps1`):

```powershell
.\build.ps1
```

The script uses the Windows .NET Framework C# compiler and writes the app to `dist`.

Run the built-in checks:

```powershell
Start-Process .\dist\TapTrace.exe -ArgumentList '--self-test', 'tests-output' -Wait
Get-Content .\tests-output\test-result.txt
```

Checks cover background input registration, input mappings, simultaneous presses, releases, settings, and overlay rendering. They do not replace a live test inside the game.

</details>
