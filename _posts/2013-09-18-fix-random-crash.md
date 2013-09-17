---
layout: post
title: "Fix random crash"
categories: [news]
tags:
---

I've recieved some reports about randomly crashes on Cubian. It seems that the randomly crashes is caused by cpu overlocking. Thanks to [346L3](https://github.com/cubieplayer/Cubian/issues/109).   

Cubian sets the maximum cpu frequency to 1.2GHz to get better performance. But the drawback is cpu will hang sometimes which causes kernel crash. **Benn Huang** who is from cubieteam suggest me set it to 1008Mhz.  

# Solution

* Manually  
  Edit `etc/init.d/cubian-ondemandcpufreq` , find
  > echo -n 1200000 > /sys/devices/system/cpu/${cpu}/cpufreq/scaling_max_freq  

  Replace with  
  > echo -n 1008000 > /sys/devices/system/cpu/${cpu}/cpufreq/scaling_max_freq

* Automaticlly  
  This requires you got the newest version of cubian-update which is v1.1.1 for current  
  >  apt-get update   
  >  apt-get install cubian-update  

  Then execute `cubian-update` should fix the problem. The cubian-update aslo fix a [SATA driver problem](https://github.com/cubieplayer/Cubian/issues/100) on A10.
