---
layout: post
title: "Cubian r7 for A10 and r4 for a20 released"
categories: [news]
tags:
---
Compares to the release at [08 Nov,2013](/2013/11/08/cubian-r6-for-a10-and-r3-for-a20-released), This release added

* Auto expand rootfs to your fit your SD card at first boot
* Using system wide automount script(devmon)

# Note
The first boot takes longer time than usual. It needs to regenerate SSH keys, Ajenti private key and resize your partition to fit your SD card. It will reboot one time automatically on first boot to take effect for changes.

# Cubietruck
r4 for a20 can work on cubietruck. But ethernet is not working due to the driver change.
