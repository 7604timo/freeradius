#Windows Clients, SAMBA AD and FreeRADIUS

This is a copy of the configs I used to get Windows 10/11 clients on a SAMBA AD to use machine authentication for WiFi, and also allow users to authenticate with their AD credentials on a Rocky Linux box.

I expect this process can be tweaked (perhaps using a Windows AD server to generate certificates for each PC client instead of using machine credentials, but that requires a Windows server - something I was trying to avoid). But, this way worked well for me.

The idea is that you create groups in AD for the machines and users which you then define in ```/etc/raddb/mods-config/files/authorize``` and allocate a VLAN to them. That way you can have one SSID that handles both machines (corporate) and users (BYOD). You obviously need to have WiFi APs that can handle dynamic VLANs - I used openWRT with hostapd and it works very well. ```hostapd``` config is in ```openwrt```.

The freeRADIUS config is in ```raddb```, and the Windows group policies are in ```windows```.

In addition to the freeRADIUS and Windows configs, you also need to make a load of certificates for the radius box to authenticate with the domain controller, which is in ```dc01```. This is one of the parts I struggled with as it's quite fiddly. I made extensive use of the 'bootstrap' script that comes with freeRADIUS in the ```certs``` directory to keep generating certificates until I had them just right.

It took me ages to figure it all out, with lots of help from the mailing list, and eventually I got it working and it was great and I hope this documentation helps someone else. Then I was told to move to Microsoft's cloud and now it's all rubbish.
