---
title: Backlight
layout: page
parent: Hardware
---
# Backlight
{: .no_toc }
### Contents:
{: .no_toc }
- TOC
{:toc}
----

## Backlight switching (for screensaver)

By default, the screensaver does not turn off the backlight on this device,
but that can be achieved with a modification of the devicetree config.

## Initialization bug

Due to a kernel bug, the backlight starts in OFF state (even though the devicetree tells it otherwise).

It gets switched on, when Xorg (KlipperScreen) starts and it also seems to start up in ON state when added as an overlay instead of embedding it directly into the devicetree.

Unless this bug is resolved, the setting will not be included in the images for the MKS-Klipad50.

*When running KlipperScreen, you will probably not notice that initialization problem, so it is safe to use the backlight modification.*

## Backlight fix

I've written a script that installs/remove the required devicetree settings.

### Supported image versions

The script supports the old buster version (original Sovol image)
and recent Armbian images for MKS-PI or MKS-Klipad50 (bookworm, trixie, noble, jammy).

### Installation

To enable backligh switching:
- Download the script: `wget https://torte71.github.io/InsideSovolKlipperScreen/files/backlight-fix`
- Install: `sudo bash backlight-fix install`
- Uninstall:  `sudo bash backlight-fix remove`

