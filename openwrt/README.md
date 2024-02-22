You need to install ```hostapd``` on your access points and use this config section in your ```/etc/config/wireless``` section:
```
config wifi-iface
        option device 'radio1'
        option mode 'ap'
        option ssid 'Corporate WiFi'
        option encryption 'wpa2'
        option server 'RADIUS_IP'
        option key 'RADIUS_secret'
        option rsn_preauth '1'
        option dynamic_vlan '2'
        option vlan_tagged_interface 'eth0'
        option vlan_bridge 'br-vlan'
        option vlan_naming '0'
        option isolate '1'
```
