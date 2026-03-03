---
coverY: 0
---

# NetworkManager

NetworkManager is the systemd service that manages network configuration

* Configuration is stored in files in /etc/NetworkManager/system-connections
  * Legacy files in /etc/sysconfig/network-scripts are still supported, but deprecated
* Different applications are available to interface with NeworManager
  * **nmcli** is a powerful command-line utility
  * **nmtui** offers a convenient text user interface&#x20;

***

In NetworkManager, devices are network interfaces

* Connections are collections of configuration settings for a device, stored in the configuration file

```
/etc/NetworkManager/system-connections        
```

* Only one connection can be active for a device&#x20;

***

Permissions to modify settings in NetworkManager are applied through **dbus**

* Non-privileged users who are logged in on the console can change network settings
* Non-privileged users who are logged in through ssh cannot
* Use **nmcli general permissions** for an overview of the current permissions that apply&#x20;

