---
layout: post
title: "Troubleshooting NAND install on A20"
categories: [news]
tags:
---
Cubian-nandinstall is a universal tool which can migrate the rootfs on the SD-card to NAND automatically, but your board refused to start up sometimes, even the installation process was normal and smooth.

#boot0 and boot1

One known reason of this problem is the boot0 and boot1 code on the device, boot0 and boot1 code is located at a special area, only livesuit can access them AFAIK. They might **NOT** made for linux. For example, Cubieboard will install an android system on the NAND at factory.

To solve the problem is pretty easy. You just need to use livesuit burn a [lubuntu system](http://cubieboard.org/download/) to nand first, then use cubian-nandinstall afterward.

**Note, everytime your burn an android system to nand, and you want change to linux, you need to perform this step, otherwise the board won't start after running cubian-nandinstall.**

#root setting in uEnv.txt
Another common pitfall is the root device parameter is not setted correctlly in uEnv.txt. The nand install script will set `root=/dev/nandb` in uEnv.txt, it should be okay with Cubian's kernel. It should be `/dev/nand2` if you use patwood's kernel. The device name is determined by whether you set **CONFIG_SUNXI_NAND_COMPAT_DEV** in kernel config.

Please let me know, if you still have problems about nand-install.
