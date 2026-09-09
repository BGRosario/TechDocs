# Using tuned Profiles

Kernel tunables are provided through the /proc/sys directory in the /proc pseudo file system

* Different file in the /proc/sys directory contain the current setting as its value
* Change the current value by echoing a new value into the file:

```
cat /proc/sys/vm/swappiness
echo 40 > /proc/sys/vm/swappiness
```

To make settings persistent, write them to a file in /etc/sysctl.d

```
cat >> swappiness.con << EOF
vm.swappniess = 40
EOF
```

* sysctl is responsible for managing many kernel tunables

sysctl has 1138 tuned parameters that it needs to manage; the solution is tuned

* tuned is a systemd service that works with different profiles
* Each profile contains a file with the name tuned.conf that has a wide range of performance-related settings

### How do they relate?&#x20;

* Tuned and sysctl are doing the same thing
  * In /etc/tuned/tuned-main.conf, the reapply\_sysct=1 parameter ensures that, in case of conflict, the sysctl parameter wins.



