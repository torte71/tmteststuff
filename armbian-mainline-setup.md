---
title: Rebuilding on Armbian-mainline
layout: page
nav_order: 18
has_toc: false
---
# Rebuilding on Armbian-mainline
{: .no_toc }
### Contents:
{: .no_toc }
- TOC
{:toc}
----

Since December 2024, the Makerbase kernel patches from Maxim Medvedev (redrathnure) have been included into mainline Armbian.  
That makes it possible to keep the kernel up-to-date (and probably even upgrading the distribution).

It is still required to replace the DTB file with a special one tailored for the Klipad50, but that may change in the future.  
For now I have added a dpkg hook that simply replaces the DTB file, whenever a dtb-package install/remove has been detected.

## Different image options

You have the choice between the [community-builds](https://github.com/armbian/community/releases) and [Maxim's images](https://github.com/redrathnure/armbian-mkspi/releases).

### Maxims image
- Comes with more preinstalled packages (e.g. NetworkManager, aptitude, mc, vim, ...)
- Allows WiFi setup right after boot (if you replaced the DTB file beforehand)

### Community image
- Comes with just a minimal set of preinstalled packages
- Requires additional steps to get NetworkManager play together with networkd
- WiFi setup directly after boot is not working
- Requires at least 25.2.0-trunk.195 to support MKSPI boards (select one with "Mkspi" in the name)

<!--
## Problems:

Armbian v25 changed from NetworkManager to networkd (managed by netplan), but as KlipperScreen depends on NetworkManager, they need to be changed.

Changing the network config over a network connection is not exactly fun, so use the serial console for the first steps, until you have correctly set up and switched to NetworkManager.  
(You may as well plug in a keyboard and work directly on the touchdisplay, but you'll need good eyesight and the last line is almost impossible to see.)
-->

## Steps to create a "sovolish" Klipper installation based on these images:

<!--
Nightly builds: <https://github.com/armbian/community/releases>  
(stable is first, scroll down for latest/nightly)

Image used: <https://github.com/armbian/community/releases/download/25.2.0-trunk.293/Armbian_community_25.2.0-trunk.293_Mkspi_bookworm_current_6.12.8_minimal.img.xz>
-->

### Downloading and flashing the image
- Choose an image file from the above links. I recommend Maxim's images, as they are easier to set up.  
  Images used for testing:
  Maxim (recommended): [1.0.1-25.2.0-trunk](https://github.com/redrathnure/armbian-mkspi/releases/download/mkspi%2F1.0.1-25.2.0-trunk/Armbian-unofficial_25.02.0-trunk_Mkspi_bookworm_current_6.12.8.img.xz)
  Community: [25.2.0-trunk.293](https://github.com/armbian/community/releases/download/25.2.0-trunk.293/Armbian_community_25.2.0-trunk.293_Mkspi_bookworm_current_6.12.8_minimal.img.xz)
- Extract the image (e.g. using [7zip](https://www.7-zip.org/))
- Write the extracted .img file to the eMMC card (e.g. using [Balena Etcher](https://www.balena.io/etcher/))

### Preparing the image
- Don't remove the eMMC card
- Use the Explorer to navigate to the "/boot/rockchip/" folder of the eMMC card
- Replace `/boot/rockchip/rk3328-mkspi.dtb` with this [rk3328-mkspi.dtb](files/rk3328-mkspi.dtb) to get WiFi access directly after booting

### Accessing the screen
- You can either use a serial connection (recommended) or work directly on the screen
  - Option 1) Serial access:
    - Power up the device without the eMMC inserted
    - Keep the power button pressed for some seconds until the device goes into soft-off state (which has serial access enabled)
    - Open the devicemanager to see, which COM-ports are already on your system
    - Connect the USB-C-port (on the bottom right of the device) with your PC
    - Look into the devicemanager again, a new COM-port should have been created
    - Use a terminal program (e.g. Putty) to connect to this port  
      Settings:
      - Speed (Baud rate): 1500000 (that's 5 zeroes after the "15")
      - Data bits: 8
      - Stop bits: 1
      - Parity: None
      - Flow control: None
  - Option 2) Direct access:
    - Plug an USB-keyboard into any of the device's USB ports
    - Disadvantages:
      - Very small
      - Keyboard uses US-Layout
      - Last row on screen is barely visible (use `clear` to clear the display and move the cursor to top)

### Initial setup
- Press the power button to boot the device
- Answer the account setup questions:
  - enter root password (e.g. "makerbase"), repeat once more
  - enter username (e.g. "mks")
  - enter user password (e.g. "makerbase"), repeat once more
  - enter real name (e.g. "Mks")

### Network setup
The next steps are slightly different, depending if you use a) an USB-Ethernet adapter, b) WiFi with Maxim's image or c) WiFi with a community image
- a) USB-Ethernet adapter:
  - Will continue right at "Set user language based on your location?"
- b) Wifi with Maxim's image:
  - Answer "y" to "connect via wireless?" (or just press ENTER)
  - Select your access point in the dialog
  - Enter your WiFi password
- a) and b)
  - When asked "Set user language based on your location?":
    - Choose what you want. I prefer "no", because untranslated error-messages give better online search results
  - When asked for generating locales:
    - If you use a user language other than english, you may want to select a different encoding from the list
    - Otherwise just use "330" to skip locale generation
  - Continue at [Preparing Klipper setup]

The next steps are **only required for the community image**:
- c) WiFi with a community image:
  - Answer "y" to "connect via wireless?" (or just press ENTER)  
    (Sadly, this just continues without asking to connect it to an access point, so no internet yet)
  - Set up Wifi using "armbian-config"
    - Execute `armbian-config`
    - Select "Network"
    - Select "NE001 - Configure network interfaces"
    - Select "NE002 - Add / change interface"
    - Select "wlan0 unassigned[wifi]"
    - Select "sta Connect to access point"
    - Select your access point from the list
    - Use "OK" to accept and "Yes" to confirm the settings
    - Quit armbian-config
  - Install NetworkManager:  
    Execute `apt update && apt install network-manager`
  - Disable networkd:
    - Execute `systemctl disable systemd-networkd.service`
  - Switch to NetworkManager:
    - Execute `armbian-config`
    - Select "Network"
    - Select "NE001 - Configure network interfaces"
    - Select "NE003 - Revert to Armbian defaults"  
      (this step changes /etc/netplan/10-dhcp-all-interfaces.yaml from networkd to NetworkManager)
  - Set up WiFi using NetworkManager:
    - Execute `nmtui`
    - Activate connection
      - select accesspoint
	- enter password
  - Troubleshooting network:
    - Check this, if the screen has a long boot delay waiting for "systemd-networkd-wait-online.service"
    - List the contents of "/etc/netplan/":  
      Execute `ls -l /etc/netplan/`
      - There should be no other file but "10-dhcp-all-interfaces.yaml".
      - Edit this file using `nano /etc/netplan/10-dhcp-all-interfaces.yaml`
      - Make sure it reads "renderer: NetworkManager" and not "renderer: networkd"  
	(otherwise change that line in the editor and save it).
<!--
- if you have an usb-ethernet connected:
  - "Set user language based on your location?"
    - choose what you want. I prefer "no", cause untranslated error-messages are easier to google.

- otherwise:
  - "connect via wireless?" -> "y" (or just "ENTER")  
    (that does not work yet. just ignore.)
  - generate locales (e.g. "330" to skip)
  - setup WiFi:
    - `armbian-config`
      - network
	- ne001 - Configure network interfaces
	  - ne002 - Add / change interface
	    - wlan0 unassigned[wifi]
	      - sta Connect to access point
		- select WiFi Network
		- enter password
		- choose "OK"
		- "Yes" (Changing network settings)
- install NetworkManager:  
  `apt update && apt install network-manager`
- disable networkd:  
  `systemctl disable systemd-networkd.service`
- switch to NetworkManager:
  - `armbian-config`
    - network
      - ne001 - Configure network interfaces
	- reset to default
  (this step changes /etc/netplan/10-dhcp-all-interfaces.yaml from networkd to NetworkManager)
- setup wifi using NetworkManager:  
  `nmtui`
  - Activate connection
    - select accesspoint
      - enter password
- Troubleshooting network:
  - check this, if the screen has a long boot delay waiting for "systemd-networkd-wait-online.service"
  - check /etc/netplan/
    a) there should be no other file but "10-dhcp-all-interfaces.yaml"
    b) make sure it reads "renderer: NetworkManager"
       and not "renderer: networkd"
       (otherwise edit it)
-->

### Preparing Klipper setup
- If you didn't generate locales, you may want to set your timezone:
  - Execute `tzselect`  
    (just follow the prompts to choose your timezone)

The following steps require a working internet connection

- Download and install the Klipad50 DTB fix:  
  (Automatically reinstalls [rk3328-mkspi.dtb](files/rk3328-mkspi.dtb) whenever a dtb-package install/remove has been detected.  
   Idea based on <https://askubuntu.com/questions/63717/execute-command-after-dpkg-installation>)
```
wget https://torte71.github.io/tmteststuff/files/klipad50-dtb-fix.deb
sudo dpkg -i klipad50-dtb-fix.deb
```
<!-- DONT USE YET --- wget https://torte71.github.io/InsideSovolKlipperScreen/files/klipad50-dtb-fix.deb  -->

- Install "git" (required for downloading KIAUH):
```
apt install git
cd
git clone https://github.com/dw-0/kiauh
```

### Setting up Klipper
{: .note }
> The next steps should be done as the Klipper user (these examples use "mks").
> *Do not do it as "root"!*
>
> So either use `exit` in the serial connection to log out and log in again as "mks"
> or use ssh/Putty to log into the device (as "mks").
>
> (If the command prompt reads "root@mkspi", you are using the root account)

- set up Klipper using KIAUH:
  - Execute
```
cd ~/kiauh
./kiauh.sh
```
  - Use the default setting for *every* question (i.e. just press ENTER)
  - Skip options 5 and 6 from the "Install" menu, but select all other
  - 1 (Yes) ("Try KIAUH v6?")
    - 1 (Install)
      - 1 (Klipper)
      - 2 (Moonraker)
      - 3 (Mainsail)
      - 4 (Fluidd)
      - 7 (KlipperScreen)
      - 8 (Crowsnest)
    - E (Extensions)
      - 1 (G-Code Shell Command)
        - 1 (Install)

- Screen rotation  
  - Execute `sudo nano /etc/X11/xorg.conf.d/01-armbian-defaults.conf`
  - Copy this text:
```
Section "Device"
        Identifier "default"
        Driver "fbdev"
        Option "Rotate" "CW"
EndSection
Section "InputClass"
        Identifier "libinput touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "libinput"
        Option "TransformationMatrix" "0 1 0 -1 0 1 0 0 1"
EndSection
```
    - press \<CTRL-X\> to quit
    - press "Y" to save
    - press ENTER to confirm filename
    - restart KlipperScreen:
      - Execute `sudo service KlipperScreen restart`

- Set up numpy (required for input shaping)
  - Execute
```
sudo apt install python3-numpy python3-matplotlib libatlas-base-dev libopenblas-dev
~/klippy-env/bin/pip install -v numpy
```

- Set up secondary mcu: (see <https://www.klipper3d.org/RPi_microcontroller.html>)
  - Execute `cd ~/klipper ; make menuconfig`
  - Select "Micro-controller Architecture" (press ENTER)
  - Select "Linux process" (press ENTER)
  - press "Q" and "Y" to quit and save
  - ```sudo make flash```
  - ```sudo cp ./scripts/klipper-mcu.service /etc/systemd/system/```
  - ```sudo systemctl enable klipper-mcu.service```
  - ```sudo service klipper restart```


- update mcu
```
  ...
```

- add Makerbase services/additions
  - Beep, Automount, Powerloss recovery (plr), 

- set up printer.cfg (I included the standard SV06 version)

