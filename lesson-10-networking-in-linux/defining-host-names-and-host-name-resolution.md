# Defining Host Names and Host Name Resolution

It starts with the appropiate host name.&#x20;

* **hostnamectl set-hostname** is used to manage hostnames&#x20;
  * If this is not done then your hostname will be set to localhost.localdomain
* The hostnameis written to /etc/hostname
* To resolve hostnames /etc/hosts is used&#x20;
  * 10.0.0.11 server2.exmaple.com server2&#x20;
* **/**&#x65;tc/resolv.conf contains DNS client configuration
* The order of hsontame resolution is determined through **/**&#x65;tc/nsswitch.conf
