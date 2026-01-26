# Understanding NIC naming

Network interfaces need a device name, because IP address configuration needs to be connected to a specific network device.&#x20;



* Use **ip link show** to see current devices, and **ip addr show** to check their configuration
* Every system has an **Io** device, which is for internal networking
* Apart from that, you'll see the name of the real network device, which is presented as a BIOS name

***

### BIOS Device Names

Classical naming is using device names like eth0, eth1 and so on&#x20;

* These device names don't reveal any information about physical device location&#x20;
* BIOS naming is based on hardware properties to gie more specific information in the device name&#x20;
  * en\[1-N] for embedded NICS
  * eno\[nn] for embedded NICS
  * p\<slot>p\<port> for NICs oon the PCI bus&#x20;
* If the driver doesn't reveal network device properties, classic naming is used&#x20;

