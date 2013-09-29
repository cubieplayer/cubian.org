---
layout: post
title: "Install LXDE with opengles accelerated on cubian"
categories: [news]
tags: tutorial
---
Cubian doesn't provide a desktop environment by default, but you can easily install it now.  

# Requirement
Please make sure the rootfs has enough available space, over 1GB is recommended. You can use [cubian-resizefs](http://cubian.org/2013/08/12/enlarge-cubian-rootfs-partition/) to resize your rootfs partition without losing any data.

# For short
> apt-get update  
> cubian-update  
> apt-get install xserver-xorg-core xinit xserver-xorg-video-sunximali sunxi-disp-test lxde  
> usermod -a -G video cubie

If everything goes well, You'll get LXDE running with opengles accelerated

# Screenshot
![cubian with lxde screenshot](http://cubieplayer.github.io/static_files/images/cubian-lxde-gles.png)

# Step by step explanation
1.	Cubian update  
	This ensures your cubian has the latest hardware support
1.	Install **xserver-xorg-core** and **xinit**  
	We only need the xserver core packages, don't install **xserver-xorg** package, it's large and contains lots of useless files for us.
1.	Install **xserver-xorg-video-sunximali** and **sunxi-disp-test**  
	These are display drivers and the driver test program. Thanks to [ssvb](https://github.com/ssvb/).  
	The X system should working now, you can test it by  
	
	> xinit /usr/bin/sunxi_disp_test -- :0
	
	If this shows a colourful triangle in a grey background measuring 480x480 then all is fine! You can safely proceed to next step.
1.	Install lxde
1.	Add user cubie to **video** group, so it can access the mali device
1.	Run the test program again.Open a lxtermial from the start menu

	> xinit /usr/bin/sunxi_disp_test
