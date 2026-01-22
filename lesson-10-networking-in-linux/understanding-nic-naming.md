# Understanding NIC naming

Network interfaces need a device name, because IP address configuration needs to be connected to a specific network device.&#x20;



* Use **ip link show** to see current devices, and **ip addr show** to check their configuration
* Every system has an **Io** device, which is for internal networking
* Apart from that, you'll see the name of the real network device, which is presented as a BIOS name

***

### BIOS Device Names

Classical naming is using device names like eth0, eth1 and so on&#x20;

* These device names don't reveal&#x20;

