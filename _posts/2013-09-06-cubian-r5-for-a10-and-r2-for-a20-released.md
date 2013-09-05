---
layout: post
title: "Cubian r5 for A10 and r2 for a20 released"
categories: [news]
tags:
---
This release fixed several bugs and one security issue.

* SATA drivers is built into kernel
* Enabled SPI,webcam,NFS,wireless etc.
* Fix a [hang-up issue](https://github.com/cubieplayer/Cubian/issues/36) on start up.
* Regenerate SSH keys on first start up
* Nandinstall folder is removed. Please use the [separate nand installer](http://cubian.org/2013/08/18/universal-and-separate-nandinstaller-is-released) instead
* Intergrates [cubian-update](http://cubian.org/2013/08/09/cubian-update-is-available)

# Tips

To reduce the installation time, The image size of cubian sets to 1GB minus 100MB.You may wants to expand the rootfs for more available space. I recommends to use [cubian-resizefs](http://cubian.org/2013/08/12/enlarge-cubian-rootfs-partition).You don't need to add apt source now as the tutorial said, because it's included at this release.  

For example, If you have a 8GB SD-card and wants to use the half of the card.

> cubian-resizefs /dev/mmcblk0 50

Cubian is quite stable now, It gives me free time on tutorials.  

# At last
I've recieved some donations, Thanks you.
