---
layout: post
title: "Resolve stability issue on cubieboard 2"
categories: [news]
tags:
---
There is some reports [1](http://www.cubieforums.com/index.php/topic,952.msg13152.html#msg13152) [2](http://www.cubieforums.com/index.php/topic,2472.msg17784.html#msg17784) [3](http://www.cubieforums.com/index.php/topic,2696.msg17764.html#msg17764) on stability problem on cubieboard2. See [issue #319](https://github.com/cubieplayer/Cubian/issues/319), as explains by [Siarhei Siamashka](https://github.com/ssvb), I quote:

<pre>
It has been confirmed that a substantial percentage of cubieboard2 and cubietruck users are having stability issues. These issues are caused by having various voltages optimistically configured way too low. Because each unit has its own tolerances, not everyone can easily reproduce these problems.
</pre>

A very detailed discussion can be found [here](https://groups.google.com/forum/#!searchin/linux-sunxi/dcdc3/linux-sunxi/1Orj-ukBb6s/qjfAh_NrL3YJ).

#Resolve the problem
1. Plan A  
apply [this patch](http://cubieplayer.github.io/static_files/temp/script.patch) manually to your script.bin.
2. Plan B  
Download script.bin already patched from [here](https://github.com/mmplayer/cubian-updates/blob/a20-3.4.79_2/boot/script.bin?raw=true) then overwrite yours.
3. Plan C  
Run <code>cubian-update --update-board-cfg</code>

#Verify if the problem resolved
1. Install latest kernel  
<code>apt-get update && apt-get install linux-image</code>
2. Install hardware tester  
<code>apt-get install cpuburn-sunxi lima-memtester</code>
3. Run hardware tester  
<code>cpuburn-sunxi</code> to test if the CPU will overheat while doing heavy work.  
<code>cpufreq-stress-test-sunxi</code> to test if the CPU is stable at every frequency.  
<code>lima-memtester</code> to test if memory is working fine.

#Screenshots
![cpuburn-sunxi screenshot](http://cubieplayer.github.io/static_files/images/cpuburn-sunxi.png)
![cpu-freq-stress-test screenshot](http://cubieplayer.github.io/static_files/images/cpu_freq_stress_test.png)
![lima-memtester screenshot](http://cubieplayer.github.io/static_files/images/lima-memtester.png)
