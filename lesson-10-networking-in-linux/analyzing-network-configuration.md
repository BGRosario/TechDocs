# Analyzing Network Configuration

Let's use the IP command:&#x20;

* The **ip** tool can be used to manage all aspects of IP networking&#x20;
* It replaces the legacy ifconfig tool; do NOT use ifconfig anymore&#x20;
* Use **ip addr** to manage address properties&#x20;

```
ip addr add dev ens33 10.0.0.10/24
```

* Use **ip link** to show link properties&#x20;

```
ip -s link
```

* Use **ip route** to manage route properties

```
ip route show
ip route add default via 10.0.0.1
```

Most network packet analysis should be done on networking hardware for prod best practices. Any changes here are also not persistent, meaning that by reboot it will be gone. \
\
If you want to keep it, use network management (nmcli)
