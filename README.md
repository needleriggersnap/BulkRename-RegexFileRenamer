<p align="center">
  <img src="https://i.postimg.cc/WzyBsSg5/banner.png" alt="BulkRename Pro — Windows Batch File & Photo Renamer With Live Preview & Undo" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Batch%20File%20Renamer-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-bulkrename--v1.4-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# BulkRename Pro — Windows Batch File & Photo Renamer With Live Preview & Undo

**Stuck with folders full of IMG_9482.JPG, Screenshot (412).png, or messy episode filenames? Windows Explorer only lets you add basic numbers in parentheses. Rename thousands of files cleanly with live before/after preview, EXIF dates, and instant Undo.**

BulkRename Pro combines visual rule stacking with safety guarantees on Windows: **showing every new filename in green before touching disk, extracting EXIF `Date Taken` timestamps for camera photos, supporting Regex find/replace, and logging every batch for 1-click rollback**.

This project is aimed at **Windows 10 and Windows 11 (64-bit) photographers, video editors, modders, and power users** organizing large file collections offline.

## Quick Use-Case & Troubleshooting Reference

| Scenario / Issue | Cause | Solution |
| --- | --- | --- |
| Camera & phone photos have generic `IMG_XXXX` names | Mixing photos from multiple cameras breaks chronological sorting | Prefix filenames with EXIF `Date Taken` (`YYYY-MM-DD_HH-MM_001.jpg`) |
| Windows Explorer batch rename adds ugly `(1), (2)` parentheses | Built-in Explorer rename lacks zero-padded numbering (`001, 002`) | Apply custom zero-padded counters (`001`–`999`) with prefix/suffix |
| Need to strip website tags or brackets from 200 downloads | Manual F2 renaming takes 30+ minutes per folder | Run Find & Replace or Regex (`\[.*?\]`) with live preview |
| Afraid a wrong rename rule will ruin a folder of assets | Command-line PowerShell rename scripts have no built-in undo | Inspect every filename diff first and revert anytime with **Undo Last Batch** |

## Download for Windows

[**Download BulkRenamePro.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/BulkRenamePro.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why use `BulkRenamePro.exe`? (Key features)

- Real-time side-by-side **Original Name → New Name** preview highlights collisions before renaming.
- Extracts EXIF `Date Taken` and file modification dates (`{YYYY}-{MM}-{DD}`) for chronological photo sorting.
- Supports Find & Replace, Regular Expressions (Regex), Case Conversion (`lowercase` / `Title Case`), and padded numbering.
- Logs every rename batch so you can revert all changes in one click with **Undo Last Batch**.

### Sample Output

```text
[BulkRenamePro] Previewing 84 files in D:\Photos\Tokyo_Trip
[OK]   DSC_0104.JPG  -->  2026-11-18_Tokyo_001.jpg  (EXIF Date Applied)
[OK]   DSC_0105.JPG  -->  2026-11-18_Tokyo_002.jpg  (EXIF Date Applied)
[OK]   Collision Check: 0 filename conflicts | Undo log saved
```

The release ZIP is named `BulkRenamePro.zip`; the Windows executable inside is named `BulkRenamePro.exe`.

1. Close BulkRename Pro before updating or replacing executable files.
2. Click **Download BulkRenamePro.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `BulkRenamePro.exe`.
5. Review the options and output paths before processing files.

**Requirements:** Windows 10 or 11 (64-bit).

### Verification & Windows SmartScreen Note

- **Offline & standard user permissions:** `BulkRenamePro.exe` runs locally without uploading your files and does not require disabling Windows Defender.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project solves

### Chronological sorting across multi-camera photo shoots

Renaming by EXIF `Date Taken` aligns iPhone, Sony, and GoPro files into one timeline.

### Collision detection before applying changes

Automatically prevents overwriting existing files if two rules produce the same target name.

### Reversible batch operations

Built-in Undo journal lets you roll back accidental bulk renames cleanly.

### Zero shell script debugging

Stack simple visual rules instead of writing complex PowerShell regex one-liners.

## Default folders and configuration paths

BulkRename Pro operates directly on your selected folders and stores its Undo journal in `%APPDATA%\BulkRenamePro`:

```text
%APPDATA%\BulkRenamePro\undo_history.json
```

Typical directory layout:

```text
BulkRename Pro Rule Pipeline:
├── [1] Find / Replace or Regex
├── [2] Insert EXIF Date ({YYYY}-{MM}-{DD})
├── [3] Add Zero-Padded Counter (001, 002...)
└── [4] Live Preview Diff -> Apply (with 1-Click Undo)
```

Always review the green preview column for the first and last items before clicking Apply.

## Quick start guide

Follow these steps to get started:

1. **Extract `BulkRenamePro.zip` and launch `BulkRenamePro.exe`.** No installation required.
2. **Drag files or folders into the file list.** Reorder items manually or sort by EXIF Date / Name / Size.
3. **Enable the rename rules you need (Replace, Date Prefix, Counter, Case).** Verify the **New Name** preview column.
4. **Click **Apply Rename**.** Use **Undo Last Batch** if you want to revert any change.

### Data safety note

BulkRename Pro checks for duplicate target filenames before executing any rename.

## What the status summary shows

BulkRename Pro displays **total queued files, active rule stack, collision warnings, and renamed file count**.

## FAQ

**Can I undo a batch rename if I make a mistake?**

Yes—click 'Undo Last Batch' to restore all original filenames from the session journal.

**Does it read EXIF Date Taken from JPG and HEIC photos?**

Yes—it reads camera capture timestamps directly from EXIF metadata.

**Can I rename file extensions as well?**

Yes, via the Extension rule toggle (disabled by default to prevent accidental extension changes).

## Useful reading

- [Microsoft Docs — Naming Files, Paths, and Namespaces](https://learn.microsoft.com/en-us/windows/win32/fileio/naming-a-file)

## More Windows Desktop Utilities

- [DupeSweep-HashFileCleaner](../DupeSweep-HashFileCleaner) — Fast SHA-256 duplicate photo, video & download cleaner
- [MP3Tag-BatchCoverEditor](../MP3Tag-BatchCoverEditor) — Batch audio ID3/FLAC metadata & cover art editor
- [ExifScrub-PhotoMetadataCleaner](../ExifScrub-PhotoMetadataCleaner) — Strip GPS, EXIF & camera metadata from photos offline
- [SnapFormat-BatchMediaConverter](../SnapFormat-BatchMediaConverter) — Offline batch HEIC/WebP/MKV to JPG/PNG/MP4 converter

*Independent open-source desktop utility for Windows.*
