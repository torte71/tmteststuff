---
title: Sovolized Armbian-mainline Klipper Image v25.2
layout: page
parent: Rebuilding on Armbian-mainline v25.2
nav_order: 17
---
# Sovolized Armbian-mainline Klipper Image v25.2
{: .no_toc }
### Contents:
{: .no_toc }
- TOC
{:toc}
----

## For SV06/SV06+/SV07/SV07+ KlipperScreen (Makerbase MKS KLIPAD50)

A ready-to-use replacement image for Sovol's KlipperScreen can be downloaded at:  

<https://drive.google.com/file/d/1qZes9nlnvvQR_9BVPbI9lHu7wbLTkyp-/view?usp=drive_link>

(Extract it using [7zip](https://www.7-zip.org/))

It is based on Maxims Medvedevs image for Makerbase boards and using a recent armbian-bookworm.
(Sovol's image based on armbian-buster is outdated, there are no packages available for it any longer. So you can't easily add any additional packages.)

Maxims image: [1.0.1-25.2.0-trunk; Armbian-unofficial_25.02.0-trunk_Mkspi_bookworm_current_6.12.8.img.xz](https://github.com/redrathnure/armbian-mkspi/releases/download/mkspi%2F1.0.1-25.2.0-trunk/Armbian-unofficial_25.02.0-trunk_Mkspi_bookworm_current_6.12.8.img.xz)


Please note that the **printer itself ("mcu") needs to be updated as well** (not just the KlipperScreen), otherwise it will complain about an outdated klipper version on the mcu and not be able to print.
For convenience, there is a **ready compiled mcu_firmware.bin** in the image (which you can easily access directly after flashing, it's located in the root of the eMMC/USB-stick).


If you have an eMMC adapter, you can use these guides to flash the image:
  * Complete backup and restore with eMMC adapter: <https://www.youtube.com/watch?v=PrC8zaVCHys>
  * Flash with eMMC adapter: <https://github.com/Sovol3d/SOVOL_KLIPAD50_SYSTEM>

If you don't have that adapter, you can follow these guides for flashing using USB-sticks:
  * Flash using one USB-stick: <https://github.com/TomasOlsson/BrickedSv07-Sv07Plus>
  * Flash using two USB-sticks(\*): <https://github.com/vasyl83/SV07update>

(\*) Vasyl's version allows creating a full backup before overwriting the original eMMC:
Just follow its step to point 6 "Flashing the image onto EMMC" and switch the source ("if=") and destination ("of="),
so it reads `dd of=backup.img if=/dev/mmcblk1 status=progress`.


Instructions for updating the "mcu_firmware.bin" can be found in the following link (scroll down to "RENAME THE FILE", just before the photos of the printer).
  * <https://github.com/3DPrintDemon/How-to-Update-Sovol-Klipper-Screen-To-Latest-Klipper-SV06-and-SV07/tree/main#updating-the-host-mcu-rpi--mcu-firmware>


The image was created as described here: [Rebuilding on Armbian-mainline v25.2](armbian-mainline-setup.html)

Contents of the image:
  * [Maxims image](https://github.com/redrathnure/armbian-mkspi/releases) (1.0.1-25.2.0-trunk; Armbian-unofficial_25.02.0-trunk_Mkspi_bookworm_current_6.12.8.img.xz)
  * [Customized dtb](files/rk3328-mkspi.dtb) for enabling wifi & spidev
  * Default Klipper install: KIAUH, Klipper (v0.12.0-410-gcf3b0475), Moonraker (v0.9.3-4-ga4604e33), Mainsail (v2.13.2), Fluidd (v1.31.4), KlipperScreen (v0.4.5-40-g7ed39038), Crowsnest (v4.1.10-1-gdd390b60), G-Code-Shell-Command
  * Numpy for input shaper (see [Vasyl's guide](https://github.com/vasyl83/SV07update#15-accelerometer-input-shaper))
  * Makerbase/Sovol [additions](sovol_mods#services): makerbase-beep-service, makerbase-automount-service, Powerloss recovery/plr-klipper
  * Sovol's original [printer.cfg for SV06](https://github.com/Sovol3d/SOVOL_KLIPAD50_SYSTEM/blob/main/klipper_configuration/SV06/printer.cfg)
  * Screen [rotation](screen#rotation) (portrait mode)
  * g-code-macro ["BEEP"](beeper) (needs to be activated in printer.cfg, as it is not part of Sovol's original file)
  * [Klipad50-dtb-fix](files/klipad50-dtb-fix.deb) (restores DTB file whenever a dtb-package install/removal is detected)
  * Packages and files of the Makerbase/Sovol additions can be found in "/root/sovolize/" for easy install/deinstall using dpkg.


Settings you might want to change (or at least know):
  * Password for user "root": `makerbase`
  * Password for user "mks": `makerbase`
  * Location/Timezone: Europe/Germany

To change the timezone, execute `sudo armbian-config` and select "Personal" and then "Timezone".

The language has to be changed in KlipperScreen, Mainsail and Fluidd separately.

----

Thanks to all who helped testing, bug chasing and documenting.
Special thanks to Vasyl Gontar for his support and of course to Maxim Medvedev for his work re-creating the build-system for the Makerbase boards.

----
Back to [start](index.html)
