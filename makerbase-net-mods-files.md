---
title: makerbase-net-mods.service files
layout: page
parent: Modifications by Sovol
---
### makerbase-net-mods.service files

#### /usr/lib/systemd/system/makerbase-net-mods.service
```
[Unit]
Description=Copy user wpa_supplicant.conf
ConditionPathExists=/boot/wpa_supplicant-wlan0.conf
Before=dhcpcd.service
After=systemd-rfkill.service

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/bin/cp /boot/wpa_supplicant-wlan0.conf /etc/wpa_supplicant/wpa_supplicant-wlan0.conf
ExecStartPost=/bin/chmod 600 /etc/wpa_supplicant/wpa_supplicant-wlan0.conf
ExecStartPost=/usr/sbin/rfkill unblock wifi

[Install]
WantedBy=multi-user.target
```

----
Back to [start](index.md)