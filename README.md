# freeradius
Windows AD and FreeRADIUS

This is a copy of the configs I used to get Windows 10/11 clients on a SAMBA AD to use machine authentication for WiFi, and also allow users to authenticate with their AD credentials on a Rocky Linux box.
The idea is that you create groups in AD for the machines and users which you then define in ```/etc/raddb/mods-config/files/authorize``` and allocate a VLAN to them.

The freeRADIUS config is in ```raddb```, and the Windows group policies are in ```windows```.

In addition to the freeRADIUS and Windows configs, you also need to make a load of certificates for the radius box to authenticate with the domain controller, which is in ```dc01```

It took me ages to figure it all out, with lots of help from the mailing list, and eventually I got it working and it was great. Then I was told to move to Microsoft's cloud and now it's all rubbish.
