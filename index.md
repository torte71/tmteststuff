---
title: Home
layout: home
nav_order: 1
---

{: .note }
> This is a private project, no guarantees or liabilities apply.  
> The author and this site are not affiliated to Sovol in any kind.  
> The information provided here has been gathered from the web and by analyzing Sovol's KlipperScreen.

# General 3D printing

## Slicing / Design

### [Orca profiles](orca_profiles.html)
  * [joescalon SV06+ profile+buildplate](orca_profiles.html#joescalon-sv06-profilebuildplate)
    * [my (based on joescalon)](orca_profiles.html#my-based-on-joescalon)
    * [Modified buildplate texture](orca_profiles.html#my-based-on-joescalon)
  * [joescalon SV07+ profile+buildplate](orca_profiles.html#joescalon-sv07-profilebuildplate)
  * [Christian Vicks profiles](orca_profiles.html#christian-vicks-profiles)
  * [Automatic z-offset adjustment per filament](orca_profiles.html#automatic-z-offset-adjustment-per-filament)

## Klipperized Sovol SV06+/SV07+ (mostly)

### [Firmware](firmware.html)
  * [Where to download](firmware.html#where-to-download)
  * [SD-card not accepted](firmware.html#sd-card-not-accepted)

### Klipper Shutdown
  * Scripts to safely shutdown.md klipper and power off using HS110 wifi.md power plug
    * [Windows version](shutdown.html)
    * [Linux version](shutdown_linux.html)

## Sovol KlipperScreen (Makerbase MKS KLIPAD50)

### [Modifications by Sovol](sovol_mods.html#modifications_by_sovol)
  * [Files in /root](sovol_mods.html#files-in-root)
  * [Services:](sovol_mods.html#services)
    * [makerbase-auto-fresh.service](sovol_mods.html#makerbase-auto-freshservice)
    * [makerbase-automount@.service](sovol_mods.html#makerbase-automountservice)
    * [makerbase-beep.service](sovol_mods.html#makerbase-beepservice)
    * [makerbase-byid.service](sovol_mods.html#makerbase-byidservice)
    * [makerbase-net-mods.service](sovol_mods.html#makerbase-net-modsservice)
    * [makerbase-soft-shutdown.md.service](sovol_mods.html#makerbase-soft-shutdownservice)
    * [makerbase-timezone-monitor.service](sovol_mods.html#makerbase-timezone-monitorservice)
    * [makerbase-wlan0.service](sovol_mods.html#makerbase-wlan0service)
  * [reverting](sovol_mods.html#reverting)
    * [power loss recovery (plr)](sovol_mods.html#power-loss-recovery-plr-1)

### [Updating](updating.html)
  * [Update Manager](updating.html#update-manager)
  * [Problems](updating.html#problems)
    * [System / Kernel (black screen)](updating.html#system--kernel-black-screen)
    * [Klipper-0.12.80+ (secondary mcu update)](updating.html#klipper-01280-secondary-mcu-update)
    * [Armbian Buster: End Of Life](updating.html#armbian-buster-end-of-life)
    * [KlipperScreen / Python 3.8](updating.html#klipperscreen--python-38)
    * [Moonraker Timelapse](updating.html#moonraker-timelapse)

### [Configuring](configuring.html)
  * [Logging, etc.](configuring.html#logging-etc)
    * [Timezone updates spamming syslog](configuring.html#timezone-updates-spamming-syslog)

### Boot loops / Black screen ("unbricking")
  * [Boot loops / Black screen](bootloop.html)
    * [Some causes for the looping boot animation](bootloop.html#some-causes-for-the-looping-boot-animation)
    * [Typical causes for the damaged files](bootloop.html#typical-causes-for-the-damaged-files)
    * [Some causes for a black screen](bootloop.html#some-causes-for-a-black-screen)
    * [Fixes](bootloop.html#fixes)
      * [Cleaning up "saved_variables.cfg"](bootloop.html#cleaning-up-saved_variablescfg)
      * [Factory reset using Sovol's "armbian-update.deb"](bootloop.html#factory-reset-using-sovols-armbian-updatedeb)
      * [Full reflash of the eMMC using Sovol's KLIPAD50_IMAGE](bootloop.html#full-reflash-of-the-emmc-using-sovols-klipad50_image)

### Expand G-Code storage space
  * [Extending storage space for gcode files](gcode_storage.html#expand-g-code-storage-space)

### Wifi
  * [Better wifi antenna](wifi.html)

### Beeper
  * [Beeper](beeper.html)

### Screen
  * [Rotation](screen.html)

### [Getting Access / Log In](access.html)
  * [Serial (over USB)](access.html#serial-over-usb)
  * [USB-Keyboard](access.html#usb-keyboard)
  * [SSH (or putty)](access.html#ssh-putty)

### Booting
  * [Booting from external device](booting.html)
    * [Boot the same image from an USB-stick](booting.html#boot-the-same-image-from-an-usb-stick)
    * [Boot image from USB-stick via serial console](booting.html#boot-image-from-usb-stick-via-serial-console)
    * [Boot from USB-stick with unbootable eMMC](booting.html#boot-from-usb-stick-with-unbootable-emmc)

### [Rebuilding](rebuilding.html)
  * [Base system](rebuilding.html#base-system)
  * [Klipper](rebuilding.html#klipper)
  * [Sovol mods](rebuilding.html#sovol-mods)
  * [Internal wifi.md + spi-dev](rebuilding.html#internal-wifi--spidev)

### Image
  * [Sovolized Armbian Klipper Image](image.html)
