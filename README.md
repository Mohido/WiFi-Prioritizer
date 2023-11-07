# WiFi-Prioritizer
A simple WiFi prioritizer script for Rocky Linux. It scans the wifi every minute and connect to the prioritised WiFi. Note, this is very unsecure for production levels. Use with caution!


# Configuration Files
Make sure to create `/etc/wifi-priorities.conf` file and write the wifi names that you would love to connect with. The order defines the priority of the wifi connection


>> /etc/wifi-priorities.conf
```
MyFirstWifi
MySecondWIfi
```

If the device is connected to the first wifi, it won't reconnect. If the devices is connected to the second wifi, it will connect to the first wifi incase it exists.


# Enabling Upon Boot
1) Copy the `wifi-prioritizerd.service` file to `/etc/systemd/system/` directory.
2) Copy the `wifi-prioritizerd` file to `/sbin/` directory
3) Change the `wifi-prioritizerd` privilages if needed (`chmod 755 wifi-prioritizerd`).
4) Reload systemd services scripts using `systemctl daemon-reload`
5) Enable the `wifi-prioritizerd` service by using `systemctl enable wifi-prioritizerd.service`
6) Start the service using `systemctl start wifi-prioritizerd`


# Notes
* Make sure that the `/etc/wifi-priorities.conf` file exist in your filesystm.
* Logs for the service can be found at `/var/log/wifi-prioritizerd.log`
* This script has been tested on Arm64 Rocky linux (on raspberry pi).


