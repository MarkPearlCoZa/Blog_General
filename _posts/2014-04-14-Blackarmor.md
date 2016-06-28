---
layout: post
title: BlackArmor NAS 440 is a disappointment
tags: Disappointment
category: Misc
---
I have had a [BlackArmor NAS 440](http://www.seagate.com/external-hard-drives/network-storage/business/blackarmor-nas-440/) for the last two years. Originally I bought the drive with the goal of getting "peace" of mind that my most critical data was backed up at RAID level 5. I have been sorely disappointed with my overall experience with the NAS drive.

My latest disappointment happened last month. I had a single drive fail in my RAID array. At the time I thought 'no problem let me put my clean backup drive in that bay and rebuild the cluster'. No such luck.

In spite of numerous attempts to get the drive to be detected and the process initiated to rebuild the array I failed. After trolling the internet and reading all the forum posts on the drive I am was not only still stuck, but also not impressed with the rest of the world's experience with the drive.

Eventually I took the three remaining drives and placed them in a different machine running Windows Server 2008. I then installed [UFS Explorer Raid Recovery](http://www.ufsexplorer.com/download_stdrr.php), which detected the drives and made it possible to recover my files. Luckily I didn't lose any data and the recovery worked fine. I would have expected this functionality to be built in the NAS drive without having to purchase third party software at an extra R12000.

I would give this drive a 2 out of 5 stars.

#### References ####

[Cracking Seagate Black Armor NAS 110](http://crapnas.blogspot.co.za/)  
[How to install latest U-Boot & Linux Kernel on BlackArmor](http://wiki.ccc-ffm.de/projekte:diverses:seagate_blackarmor_nas_220_debian)  
[GNU ARM Eclipse](http://gnuarmeclipse.github.io/toolchain/install/)  
