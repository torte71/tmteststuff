---
title: eMMC Card Backup
layout: page
parent: Configuring
nav_order: 3
---
# eMMC Card Backup
{: .no_toc }
### Contents:
{: .no_toc }
- TOC
{:toc}
----

## Backup the eMMC using an eMMC-USB adapter
- This is the fastest, easiest and most reliable way
- Follow [Gergo's Youtube guide](https://www.youtube.com/watch?v=PrC8zaVCHys)

## Backup eMMC to USB pen without opening the KlipperScreen

### Requirements
- USB pen drive bigger than the eMMC card\
  (the default eMMC card is 8GB, use at least a 16GB pen drive)
- KlipperScreen with active makerbase-automount.service\
  (this is the default for the original Sovol image and my klipperized Armbian images)

### Prepare the USB pen drive
- Format an USB pen drive with "exFAT"\
  (do NOT use FAT32, it doesn't support the large file;\
  do NOT use NTFS, as its implementation is very slow)
- Create an empty directory on that drive called "mksbackup"\
  (this is required to identify the correct drive).

### Download "plink.exe" from the "putty" suite
- Download location: <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>
- (if unsure, use the 32bit x86 version. If it doesn't start, use the 64bit x86 version)

### Create following file in the same directory as plink.exe
- Call it e.g. "mksbackup.cmd"
- Or download the [mksbackup.cmd](files/mksbackup.cmd)
- Make sure it is in the same directory as plink.exe

```
setlocal
set HOST=mkspi
set USER=root
set PASS=makerbase

plink %HOST% -l %USER% -pw %PASS% ^
  "for BASE in $(grep gcodes\/USB /proc/mounts|cut -d ' ' -f 2); "^
    "do BKDIR=$BASE/mksbackup; if [ -d $BKDIR ]; then "^
      "echo FOUND: $BKDIR ; "^
      "mount / -o remount,rw ;"^
      "dd if=/dev/mmcblk1 of=$BKDIR/$(date +%%Y%%m%%d-%%H%%M).img status=progress ;"^
      "poweroff ; break ;"^
    "fi ;"^
  "done"

endlocal
```

### Start the backup process
- Do NOT have any print jobs running on that KlipperScreen!
- Insert the USB pen drive into the (running) KlipperScreen.
- Execute the "mksbackup.cmd" on your local PC (e.g. with a doubleclick).
- Watch the progress of the backup process\
  (it will just bail out, if the pen drive could not be indentified).
- After the backup is done, the KlipperScreen is shut down automatically.\
  (The final line will read `FATAL ERROR: Remote side unexpectedly closed network connection`\
   this is intended behaviour, nothing to worry about).

### Wait for the backup to finish
- When the KlipperScreen has shut down, remove the USB pen drive.
- The backed up image can be found in the "mksbackup" directory.
- The filename will reflect the date and time when the backup was started.

Example output (from backing up a 16GB eMMC card):
```
d:\putty>mksbackup.cmd

d:\putty>setlocal

d:\putty>set HOST=mkspi

d:\putty>set USER=root

d:\putty>set PASS=makerbase

d:\putty>plink mkspi -l root -pw makerbase   "for BASE in $(grep gcodes\/USB /proc/mounts|cut -d ' ' -f 2); "    "do BKDIR=$BASE/mksbackup; if [ -d $BKDIR ]; then "      "echo FOUND: $BKDIR ; "      "mount / -o remount,rw ;"      "dd if=/dev/mmcblk1 of=$BKDIR/$(date +%Y%m%d-%H%M).img status=progress ;"      "poweroff ; break ;"    "fi ;"  "done"
Server refused our key
FOUND: /home/mks/printer_data/gcodes/USB/mksbackup
15627008512 bytes (16 GB, 15 GiB) copied, 1171 s, 13.3 MB/s
30535680+0 records in
30535680+0 records out
15634268160 bytes (16 GB, 15 GiB) copied, 1171.56 s, 13.3 MB/s
FATAL ERROR: Remote side unexpectedly closed network connection

d:\putty>endlocal

d:\putty>
```
