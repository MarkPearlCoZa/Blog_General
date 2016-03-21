---
layout: post
title: Installing Ubuntu on Virtual Box
tags: Ubuntu
category: Tech
---

### Step 1 - Set Virtual Box Network Cards ###

Ensure the network card settings match the following.  

Network card 1 should look like...

![Network Card 1]({{ site.url }}/assets/images/2014-10-23-Ubuntu-on-VirtualBox-Network1.png)

Network card 2 should look like...  

![Network Card 2]({{ site.url }}/assets/images/2014-10-23-Ubuntu-on-VirtualBox-Network2.png)

### Step 2 - Configure Ubuntu Network Interfaces ###

Change the network settings in the VM to have configured ip addresses for both cards. You need to edit the file in the folder

~~~
/etc/network/interfaces 
~~~

The file contents should be similar to the following

~~~
# The loopback network interface
auto lo
iface lo inet loopback

# Network Interface 1
auto eth0
iface eth0 inet dhcp

# Network Interface 2
auto eth1
iface eth1 inet static
address 192.168.56.20
netmask 255.255.255.0
network 192.168.56.0
broadcast 192.168.56.255
~~~

To restart the network interfaces type the following  

~~~
sudo ifdown eth0 && sudo ifup eth0
sudo ifdown eth1 && sudo ifup eth1
~~~

### Step 3 - Enable SSH ###

Install the OpenSSH server

~~~
sudo apt-get install openssh-server 
~~~

Edit the ssh config file for customizations if you need to.

~~~
/etc/ssh/sshd_config
~~~

For more info on OpenSHH read there [website](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

If there are issues connecting to SSH check your Windows Firewall Settings

### Step 4 - Setup Conemu ###

Create a Putty Instance to ssh

![Putty Settings]({{ site.url }}/assets/images/2014-10-23-Ubuntu-on-VirtualBox-Putty.png)


Setup ConEmu to allow you to connect via Putty

![ConEmu Settings]({{ site.url }}/assets/images/2014-10-23-Ubuntu-on-VirtualBox-ConEmu.png)



