# Pendrive Broadcaster v3.2 hardware acceptance

Use expendable test media for root-copy and formatting tests. Inventory checks are read-only.

## 1. Fast discovery

1. Start the app with no pendrive inserted.
2. Insert one drive and choose Refresh.
3. Confirm its drive row appears promptly with `Identifying device and USB path…`.
4. Confirm it later changes to Ready with model, serial, hub, port path, and link class.
5. Repeat with several drives on shared and independent hubs.

Pass: the UI remains responsive, each drive appears before enrichment completes, all detected drives are selected by default, and no drive is duplicated.

## 2. Root-content copy

Create a test source containing:

```text
autorun.inf
readme.txt
payload\nested.txt
empty-folder\
```

Copy to expendable media and confirm the result is `H:\autorun.inf`, `H:\readme.txt`, `H:\payload\nested.txt`, and `H:\empty-folder\`. There must not be an extra source-name directory. Modern Windows may ignore USB AutoRun commands by policy; this test validates placement only.

Repeat with Smart update, Replace all, and Skip existing. Cancel a large copy, choose Retry failed drives, and confirm validated `.usbcopy-part` data resumes at the root.

## 3. Five-second review and exclusion

1. Select at least three test drives and start.
2. Confirm there is no keyboard-input field.
3. Confirm Start remains disabled for five seconds.
4. Clear Include for one pendrive and start after the delay.
5. Confirm the excluded drive is neither copied nor formatted and says `Excluded at review`.

For format-first, confirm Start remains disabled after five seconds until the permanent-erasure warning checkbox is selected.

## 4. Safe eject

1. Complete a copy and close all files/Explorer windows using the target.
2. Use Safe eject in the app and compare with the Windows taskbar eject action.
3. Confirm the row becomes `Ejected • Safe to remove` only after Windows accepts removal.
4. Reinsert the drive, keep a file open, and verify a failed eject reports the actual drive letter and useful system/device/volume details.
5. Close the handle and retry.

The automated build does not eject a connected drive because that changes operator-controlled hardware state; this step must be performed manually.

## 5. Formatting

Use expendable media only.

1. Start the app normally, without **Run as administrator**, on a PC/account that previously allowed removable-drive formatting.
2. Validate exFAT, NTFS, and FAT32 where supported.
3. Confirm the app attempts formatting instead of blocking at the review screen.
4. Confirm only drives still marked Include are erased, identity is revalidated, and a format failure prevents copying to that target.
5. On a PC whose policy denies formatting to the current user, confirm Administrator guidance appears only after Windows returns the permission error and that the Windows details are included.

