# Monitoring Memory Usage



Linux caches as many files as possible to guarantee fast access.&#x20;

* For that reason, Linux memory often shows as saturated
* **Swap** is used as an overflow buffer of emulated RAM on disk (this is what you use when running out of memory)
* The Linux kernel moves inactive applications' memory to swap first
* Inactive cache memory will just be dropped&#x20;
* Use **free -m** to get details about current memory usage&#x20;
* More detailed memory information is in /proc/memifo

***



RAM has to be balanced between the application and cache memory. These can be used or unused; they are known as: <br>

* Active&#x20;
* Inactive&#x20;

If you have a shortage of RAM, you may drop RAM from the cache, making it available for the application. \
\
However, nowadays we have what is called SWAP memory. This is emulated RAM on disk (disk space pretending to be RAM). In fact, if you have inactive memory from the application, and you move it to swap space, then it won't matter since it's just free memory.&#x20;



```
root@rhel-serverA:/proc#free -mh
               total        used        free      shared  buff/cache   available
Mem:           1.7Gi       575Mi       510Mi        11Mi       834Mi       1.1Gi
Swap:          2.0Gi        46Mi       2.0Gi

```



***

### GRUB with Memory

You can boot the machine to GRUB, and add on the end of the 'linux' line "Mem=(insert amount)Gb" - Ctrl-x will save changes. This will boot the machine with the desired amount you specified.&#x20;
