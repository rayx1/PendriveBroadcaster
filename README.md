# Pendrive Broadcaster v3.2.1

Pendrive Broadcaster is a Windows desktop app for copying the **contents** of one source folder directly to the root of every reviewed removable USB drive. It is developed by Rashmiranjan Behera and released under the MIT License.

## What v3.2.1 includes

- Removable drives appear immediately while model, serial, physical hub, port, and negotiated speed are enriched in the background.
- Source contents are copied directly to each drive root. For example, `source\autorun.inf` becomes `H:\autorun.inf`; the containing source-folder name is not created on the drive.
- The destination field is fixed to **Root of each drive**.
- The pre-copy review uses an Include checkbox for every pendrive. Clear it to exclude that device from copying and formatting.
- Start remains locked for a five-second safety delay. No keyboard phrase is requested.
- Format-first additionally requires an explicit warning checkbox acknowledging permanent erasure of every included drive.
- Safe eject first invokes the Windows Explorer/System Eject action, then requests removal of the physical USB parent device, then uses the lock/dismount/media-eject fallback.
- Eject errors now show the actual drive letter and meaningful fallback details instead of the literal `{drive.root.drive}` placeholder.

## Retained features

- All detected pendrives are selected by default.
- Mounted/ejected status, filesystem, free space, model, and hardware/volume serial.
- USB controller → hub → port → pendrive topology with negotiated USB link class.
- Adaptive Maximum is the default, with Gentle, Balanced, and immediate Maximum manual modes.
- Per-drive progress, current file, MB/s and ETA; overall and per-hub throughput/utilization.
- Smart update, Replace all, and Skip existing root conflict policies.
- Validated `.usbcopy-part` resume and Retry failed drives.
- Optional SHA-256 verification.
- Saved presets; formatting is never saved or automatically enabled.
- Optional exFAT, NTFS, or FAT32 format-first workflow with serial-aware revalidation.
- Formatting is attempted with normal Windows permissions first; Administrator guidance appears only if Windows denies the operation under the PC's removable-media policy.
- Safe eject per drive and Eject all.
- Scrollable How-to, About, MIT License, glowing-folder icon, application splash, and boot splash.

## Run from source

```powershell
python .\pendrive_broadcaster_v32.py
```

Python 3.10 or newer is recommended. The app uses Python's standard library and built-in Windows management interfaces.

## Build the portable Windows executable

Install PyInstaller, then run:

```powershell
.\build-v321.ps1
```

The executable is written to `dist\PendriveBroadcaster-v3.2.1.exe`.

## Basic workflow

1. Choose a source folder. Its contents—not the containing folder—will be copied to every included drive root.
2. Insert pendrives. They appear quickly; wait until identification and topology enrichment says Ready.
3. Choose conflict, speed, verification, and optional format settings.
4. Start, review model/serial/hub/port, clear Include for unwanted drives, and wait five seconds.
5. If formatting is enabled, also select the permanent-erasure warning checkbox.
6. Monitor progress and use Safe eject or Eject all only after completion.

## Autorun note

The app places `autorun.inf` at the drive root when it exists in the selected source. Modern Windows versions commonly restrict or ignore AutoRun commands on removable USB storage for security, so root placement does not guarantee automatic execution on every computer or policy configuration.

## Root-copy safety

- Smart update skips unchanged root paths and replaces changed files.
- Replace all recopies every source file but does not delete unrelated files already on the drive.
- Skip existing never overwrites an existing path.
- Review carefully if a source filename matches an important file already at the drive root.
- Formatting is off by default and permanently erases only the drives still marked Include.

## Author and license

Developed by **Rashmiranjan Behera**  
Website: <https://rbehera.in>  
Email: <me@rbehera.in>

MIT License. See `LICENSE-Rashmiranjan-Behera.txt`.

