---
layout: post
title: "Enlarge Cubian rootfs partition"
categories: [news]
tags:
---
The rootfs partition on Cubian is 1GB minus 100MB. You may wants to enlarge the partition 
for more space. [Here](http://askubuntu.com/questions/24027/how-to-resize-a-ext4-root-partition-at-runtime) 
is a small tutorial.  
For convenience, I created a tool based on the tutorial named `cubian-resizefs`

# Installation

First, [Import GPG key and add apt source](http://cubian.org/2013/08/09/cubian-update-is-available). 

Then,  
> apt-get update && apt-get install cubian-resizefs

# Usage

> cubian-resizefs device [ratio]

**Ratio** is between 1 and 100, if **ratio** is not provided. It will occupy the whole SD-card.
For example, if ratio is 50, it means use the half space of your SD-card. If it's 75, it means use the 3/4 of total space, and so on.  

> cubian-resizefs /dev/mmcblk0

# Notice

We modify the partition table using `fdisk` internally. It's always risky when you
do such things.So the old partition table is backuped. You can always restore the
partition table in case of any problem happens.

> dd if=PATH_TO_MBR_BAK of=/dev/MMC_DEVICE bs=1 count=64 skip=446 seek=446
