# Monitoring Memory Usage



Linux caches as many files as possible to guarantee fast access.&#x20;

* For that reason, Linux memory often shows as saturated
* **Swap:** emulated swap on disk, a disk that pretends to be RAM (this is what you use when running out of memory)
* The Linux kernel moves inactive applications' memory to swap first
* Inactive cache memory will just be dropped&#x20;
* Use **free -mh** to get details about current memory usage&#x20;
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

You can boot the machine to GRUB and add on the end of the 'linux' line "Mem=(insert amount)Gb" - Ctrl-x will save changes. This will boot the machine with the specified amount.&#x20;

***

### Memory in Depth (proc/meminfo)

Let's use my RHEL machine as an example

```
Active:           175616 kB
Active(anon):     118612 kB   →  ~116 MB — app memory in active use
Inactive(anon):    51552 kB   →  ~50 MB  — app memory not touched recently
Active(file):      57004 kB   →  ~56 MB  — recently accessed cached files
Inactive(file):   767492 kB   →  ~750 MB — cached files sitting idle, first to go
```

### Write Cache

Is used while writing files; if you are writing files, it is first committed to memory, and from memory to disk.&#x20;

* This cache is periodically committed to disk by **pdflush** kernel thread - if you see this a lot, it means your machine is writing a lot.&#x20;
* As a result, after committing a file write, it's not immediately secure.&#x20;
  * That means, if you write a file, it will temporarily be stored in the server write cache, and if at that moment the server crashes, the file will be gone.&#x20;
* To ensure that a file is committed to disk, use the **sync** command
