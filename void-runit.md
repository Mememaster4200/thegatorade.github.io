---
layout: default
title: void-runit base guide
---

This is a noob mini-guide to [runit](smarden.org/runit/), and specifically to the runit used in [Void Linux](http://voidlinux.eu), which uses different directories.  
  
This little guide also contains references to *systemctl*, to help people who just switched from systemd to a **real** init system understand what they are doing.  
  
I use **servicename** as the service I'm handling with the commands; Obviously change it to what you need to manage.  
  
<h2>basic usage</h2>

*sv* is runit's program to handle services.  
*Services* are stored in two directories on Void:  
*/etc/sv/* is where services end after being installed by *xbps*.  
*/var/service/* contains symlinks to services in */etc/sv/*.  
*sv* actually considers the services in the second directory as those "enabled" (they are also run at boot)  

To see which services are **available**:  
> ls /etc/sv/  
  
To see what modules are **enabled**:  
> ls /var/service/  
  
To enable a service, just create a symlink:  
> ln -s /etc/sv/<b>servicename</b> /var/service/ 
This is the same as doing *systemctl enable* ***servicename*** on systemd.  
Please note that doing this also starts the service.  

To disable (**and stop**) a service, it's just the opposite: remove the symlink.  
> rm -r /var/service/<b>servicename</b>  
  
In order to know the status, start, stop, or restart a service, like you do with systemd using `systemctl status/start/stop/restart servicename` just use `sv status/start/stop/restart servicename`  
Yes, it's the same.  
  
<h2>Runlevels</h2>
  
I will write this later. ***Now is the time of lunch.***
