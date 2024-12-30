---
title: Updating
layout: page
nav_order: 6
---
# Updating
{: .no_toc }
### Contents:
{: .no_toc }
- TOC
{:toc}
----

See also: <https://github.com/3DPrintDemon/How-to-Update-Sovol-Klipper-Screen-To-Latest-Klipper-SV06-and-SV07>

## Update Manager

## Problems

### System / Kernel (black screen)
```
- Updating "System" breaks KlipperScreen
  (sometimes even breaks wifi-access)
  Cause: Stock armbian kernels are incompatible with KlipperScreen
    - kernel on KlipperScreen is linux-5.16.20-rockchip64 (Version: 22.05.0-trunk)
      - This kernel is not found on the armbian servers (latest version: 5.16.11-rockchip64)
    - All later kernels are incompatible:
      - "/dev/spidev*" is not created (touchscreen and accel-sensors require spidev)
      - my guess: might have to do with the devicetree files
  Temporary fix:
    - Revert to old kernel
      Image location: see https://netztorte.de/3d/doku.php?id=firmware#where_to_download
      a) Re-flash (kills all prior settings)
         - Find image online (armbian-update.deb)
	 - Flash via USB-stick
      b) Revert just kernel (keeps settings)
         - upload armbian-update.deb to your klipperscreen
           e.g. using the web-frontend: Navigate to "Machine" and use the "upload file" button
           (or use scp or whatever for uploading)
         - use ssh/putty to log into your klipperscreen
         - change into the directory where you uploaded armbian-update.deb to
           for the mainsail example: "cd ~/printer_data/config"
         - Extract kernel package:
	     "dpkg -x armbian-update.deb xtract"
         - install (downgrade) kernel:
	     "sudo dpkg -i xtract/root/system_deb/linux-image-edge-rockchip64_22.05.0-trunk_arm64.deb"
         - install (downgrade) the dtb:
	     "sudo cp xtract/home/mks/rk3328-roc-cc.dtb /boot/dtb/rockchip/"
    - Keep that kernel-version (choose one of the following options):
      a) don't update "System" at all (stinks)
      b) keep just that kernel-version (allows updating "System")
         - "sudo apt-mark hold linux-image-edge-rockchip64 linux-dtb-edge-rockchip64"
      c) freeze the kernel using "armbian-config"
         (see https://github.com/3DPrintDemon/How-to-Update-Sovol-Klipper-Screen-To-Latest-Klipper-SV06-and-SV07)
```


### Klipper-0.12.80+ (secondary mcu update)
```
- Compiling klipper for "mcu"
  # cd klipper
  # make menuconfig
  - select "Micro-controller Architecture" and set to "Linux process"
  # make clean ; make ; make flash
  - ("make flash" replaces "/usr/local/bin/klipper_mcu" with "out/klipper.elf")
- Compiling klipper for "mcu linux"
  (as from https://github.com/bassamanator/Sovol-SV06-firmware/discussions/111):
  # cd klipper
  # make menuconfig
  - change settings ("=" are unchanged defaults)
    = Enable extra low-level configuration options: [*]
    = Micro-controller Architecture: STMicroelectronics STM32
    * Processor model: STM32F103
    * Disable SWD at startup (for GigaDevice stm32f103 clones): [*]
    * Bootloader offset: 28KiB bootloader
    = Clock Reference: 8 MHz crystal
    * Communication interface: Serial (on USART1 PA10/PA9)
    = Baud rate for serial port: 250000
  # make clean ; make
  - copy "out/klipper.bin" to SD-card and rename it (must end in ".bin")
    !!! use a different name than that from prior updates !!!
```


### Armbian Buster: End Of Life
Sovol's KlipperScreen still uses the outdated Armbian "buster" version, they've not released a newer firmware version to the current day (Oct. 2024).
The repositories for this version have been taken offline in spring 2024.
  * Updating the system packages using apt (e.g. `apt-get update` or `apt-get upgrade`) does not work any longer, because these updates do not exist any more.
  * The missing system updates make it more and more difficult updating the Klipper components. E.g. recent "KlipperScreen" service versions depend on Python-3.8, but the device is stuck at Python-3.7.
  * At least one can not accidentally brick the device by updating the kernel or .dtb files any longer, as these files simply do not exist any longer.
  * It is possible to flash a recent Armbian version, but it takes more than just a few mouseclicks.  
     See these guides:
    * Rebuilding from scratch using Maxim's Armbian bookworm:
      * My guide: [Rebuilding](rebuilding.html)
      * Vasyl's guide: <https://github.com/vasyl83/SV07update>
    * You can also find a readily prepared image (built as on my guide) here: [Image](image.html)


### KlipperScreen / Python 3.8
The last version of KlipperScreen that works with python 3.7 is v0.4.1.
I guess the easiest fix is resetting KlipperScreen to that revision and never updating it afterwards. That means:
  * Log into the KlipperScreen using SSH or Putty and enter the following commands:
  * `cd ~/KlipperScreen`
  * `git reset --hard v0.4.1`
(I haven't tested this, but it is taken from the KlipperScreen FAQ at <https://klipperscreen.readthedocs.io/en/latest/FAQ/>)

Other options are:
  * Revert the whole system to its original state by flashing the emmc card with Sovol's image (and not updating afterwards): <https://drive.google.com/file/d/1A1-Rw1vDPUT4pnvMOBWTd098l2aShehC/view>
  * Flash a recent armbian image to the emmc card (then you can update afterwards).
  * Maybe its possible to manually download, compile and install python 3.8, but I'd expect many issues with that (possibly missing dependencies, too little free space on the emmc). <https://devguide.python.org/getting-started/setup-building/>


### Moonraker Timelapse
The moonraker timelapse script has a dependency check at the starts, which prevents the installation on the outdated Armbian buster version.
By removing that check, it should be possible to install the timelapse script.
See Gergo's [Youtube guide](https://www.youtube.com/watch?v=86CFV_CbrvQ&t=457s)


----
Back to [start](index.html)
