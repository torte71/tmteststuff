---
title: Upgrading from MKS-PI images
layout: page
parent: Custom firmware options
nav_order: 4
has_toc: false
---
# Upgrading from MKS-PI images
{: .no_toc }
### Contents:
{: .no_toc }
- TOC
{:toc}
----

## Unsupported
- Original Sovol/Makerbase image

## Supported
- Images based on MKS-PI

- Images based on pre-release MKS-KLIPAD50

### Images based on MKS-PI

{: .warning }
> Make an image of your eMMC card before trying to upgrade!

{: .note }
> The next steps need to be done as root. Execute
>
````
sudo su
cd
```
>
> And when you are done, execute `exit` to switch back to the default user (or do a reboot).

- Switch to rolling repository
  - Execute `sed -i "s/apt\.armbian\.com/beta.armbian.com/" /etc/apt/sources.list.d/armbian.list`

- Allow board updates
  - Execute `apt-mark unhold armbian-bsp-cli-mkspi-current armbian-config armbian-firmware armbian-plymouth-theme armbian-zsh base-files linux-dtb-current-rockchip64 linux-headers-current-rockchip64 linux-image-current-rockchip64 linux-u-boot-mkspi-current`

- Update board packages (and others)
  - Execute `apt update && apt -y upgrade`

- Replace BSP (board-support-package) and bootloader package
  - Execute `apt -y remove armbian-bsp-cli-mkspi-current`
  - Execute `apt -y install armbian-bsp-cli-mksklipad50-current linux-u-boot-mksklipad50-current`

- Force updating bootloader
  - Execute `sed -i "/^FORCE_UBOOT_UPDATE/ s/=.*/=yes/" /etc/armbian-release`
  - Execute `dpkg-reconfigure linux-u-boot-mksklipad50-current`
  - Execute `sed -i "/^FORCE_UBOOT_UPDATE/ s/=.*/=/" /etc/armbian-release`

- Load rk805 module at boot (makes status-LEDs work)
  - Execute `echo "pinctrl-rk805" >> /etc/modules`

- Clean up old DTB workaround
  - This will throw some error messages. Simply ignore them.
  - Execute `apt -y remove klipad50-dtb-fix`

- Reboot
  - Execute `reboot`

### Images based on pre-release MKS-KLIPAD50

{: .warning }
> Make an image of your eMMC card before trying to upgrade!

{: .note }
> The next steps need to be done as root. Execute
>
````
sudo su
cd
```
>
> And when you are done, execute `exit` to switch back to the default user (or do a reboot).

{: .note }
> This only applies to images downloaded from
>
> https://github.com/torte71/armbian-mksklipad50/releases
>
> (Klipad50 images downloaded from armbian.com do not need any changes.)

- Switch to rolling repository
  - Execute `sed -i "s/apt\.armbian\.com/beta.armbian.com/" /etc/apt/sources.list.d/armbian.list`

- Allow board updates
  - Execute `apt-mark unhold armbian-bsp-cli-mkspi-current armbian-config armbian-firmware armbian-plymouth-theme armbian-zsh base-files linux-dtb-current-rockchip64 linux-headers-current-rockchip64 linux-image-current-rockchip64 linux-u-boot-mkspi-current`

- Update board packages (and others)
  - Execute `apt update && apt -y upgrade`

- Reboot
  - Execute `reboot`


