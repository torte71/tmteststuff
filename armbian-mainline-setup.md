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

## Problems:

Armbian v25 changed from NetworkManager to networkd (managed by netplan), but as KlipperScreen depends on NetworkManager, they need to be changed.

Changing the network config over a network connection is not exactly fun, so use the serial console for the first steps, until you have correctly set up and switched to NetworkManager.  
(You may as well plug in a keyboard and work directly on the touchdisplay, but you'll need good eyesight and the last line is almost impossible to see.)


## Steps to create a "sovolish" Klipper installation based on these images:

Nightly builds: <https://github.com/armbian/community/releases>  
(stable is first, scroll down for latest/nightly)

Image used: <https://github.com/armbian/community/releases/download/25.2.0-trunk.293/Armbian_community_25.2.0-trunk.293_Mkspi_bookworm_current_6.12.8_minimal.img.xz>

- write image to emmc
- replace boot/rockchip/rk3328-mkspi.dtb with this [rk3328-mkspi.dtb](files/rk3328-mkspi.dtb) to enable wifi
- enable serial access:
  - power up without emmc
  - keep power button pressed for soft-off
  - connect serial: use USB-C-port, find COM port in devicemanager ; Baud=1500000 (5 zeroes after "15")
- press powerbutton to power up
- answer the account setup questions:
  - enter root password (e.g. "makerbase"), repeat once more
  - enter username (e.g. "mks")
  - enter user password (e.g. "makerbase"), repeat once more
  - enter real name (e.g. "Mks")
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
- if you didn't generate locales, you may want to set your timezone:
  - tzselect
    (just follow the prompts)

The following steps require a working internet connection

- automatically fix dtb after each install:  
  FOR FUTURE - DONT USE --- `wget https://torte71.github.io/InsideSovolKlipperScreen/files/klipad50-dtb-fix.deb`  
  `wget https://torte71.github.io/tmteststuff/files/klipad50-dtb-fix.deb`  
  `sudo dpkg -i klipad50-dtb-fix.deb`  
  Idea based on <https://askubuntu.com/questions/63717/execute-command-after-dpkg-installation>  
  [rk3328-mkspi.dtb](files/rk3328-mkspi.dtb)  
  (this is exactly the same as previous "rk3328-roc-cc.dtb", just renamed)

- install "git" for downloading kiauh:
```
  sudo apt install git
  cd
  git clone https://github.com/dw-0/kiauh
```

- set up Klipper using kiauh:
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
  - `sudo nano /etc/X11/xorg.conf.d/01-armbian-defaults.conf`
  - copy this text:
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
    - press \<CTRL-X\ to quit
    - press "Y" to save
    - press ENTER to confirm filename
    - restart KlipperScreen:  
      `sudo service KlipperScreen restart`

- set up numpy (for input shaping)
```
sudo apt install python3-numpy python3-matplotlib libatlas-base-dev libopenblas-dev
~/klippy-env/bin/pip install -v numpy
```

- Set up secondary mcu: (see <https://www.klipper3d.org/RPi_microcontroller.html>) ```cd ~/klipper ; make menuconfig```
  - select "Micro-controller Architecture" (press <ENTER>)
  - select "Linux process" (press <ENTER>)
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

