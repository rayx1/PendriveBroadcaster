# Pendrive Broadcaster

Pendrive Broadcaster is a portable Windows application for copying the contents of one folder in parallel to multiple USB pendrives. It provides removable-drive identification, progress monitoring, hub-aware speed management, optional formatting, retry/resume controls, and safe eject.

This repository distributes the compiled Windows application only. The Python source code is not included in the public release.

## Check Latest Version
The latest Windows release is available from the
[release page](https://github.com/rayx1/PendriveBroadcaster/releases/tag/v3.2.1).


### 

The application is portable: download the executable and run it without installation.

## Main features

- Detects removable USB drives and selects all detected pendrives by default.
- Displays mounted/ejected status, filesystem, capacity, model, serial number, USB hub, port path, and negotiated USB connection speed.
- Copies the **contents** of the selected source folder directly to each included drive root.
- Copies to multiple drives concurrently, with per-drive and overall progress bars, transfer speed, ETA, and hub-utilization information.
- Includes Smart update, Replace all, and Skip existing conflict options.
- Supports retry and validated resume after an interrupted copy.
- Provides optional SHA-256 verification.
- Supports saved copy presets. Destructive formatting is never saved or enabled automatically.
- Optionally formats included drives as exFAT, NTFS, or FAT32 before copying.
- Provides individual Safe eject controls and an Eject all button.
- Includes a five-second pre-copy safety review with an Include checkbox for every drive.

## System requirements

- Windows 10 or Windows 11, 64-bit
- One or more removable USB storage drives
- No Python installation required

## How to use

1. Download and run `PendriveBroadcaster-v3.2.1.exe`.
2. Choose the source folder whose contents you want to distribute.
3. Connect the USB pendrives and wait for device identification to finish.
4. Review the selected conflict, speed, verification, and optional format settings.
5. Select **Copy to selected drives**.
6. In the review screen, clear **Include** beside any drive that must be excluded.
7. Wait for the five-second safety timer, approve the format warning when applicable, and start copying.
8. After copying finishes, use **Safe eject** or **Eject all** before removing the drives.

## Formatting warning

Formatting permanently erases every included drive. Use expendable media for initial testing and verify each model, serial number, drive letter, hub, and port before approving the operation.

The app first attempts formatting with normal Windows permissions. If the computer's removable-media policy denies the operation, Windows may require the application to be reopened using **Run as administrator**.

## Root-copy

The selected folder's contents are copied directly to the drive root. For example, `source\` is copied as `H:\`; an additional `source` folder is not created.

## Windows security notice

The executable is currently unsigned. Microsoft Defender SmartScreen may display a warning because the application does not yet have a commercial code-signing certificate. Download releases only from this official repository.

SHA-256 for `PendriveBroadcaster-v3.2.1.exe`:

```text
20A1A31ADE05E266A5CE772EBA8F3A75BB4AEA4F4E615E66124FB62553571EAF
```

## Author

Developed by **Rashmiranjan Behera**  
Website: <https://rbehera.in>  
Email: <me@rbehera.in>

## License

Distributed under the MIT License. See the included license notice for details.

Copyright © Rashmiranjan Behera.
