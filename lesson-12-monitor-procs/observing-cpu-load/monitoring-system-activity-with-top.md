# Monitoring System Activity with Top

### Top Command Output

Now that I have executed those schedule task/commands, they should be running in a loop. The load average is climbing incrementally; see below:&#x20;

```
top - 10:54:31 up 153 days, 10:17,  2 users,  load average: 4.00, 3.51, 1.96
Tasks: 125 total,   5 running, 120 sleeping,   0 stopped,   0 zombie
%Cpu(s): 41.5 us, 58.1 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.3 hi,  0.0 si,  0.0 st
MiB Mem :   1707.3 total,    262.7 free,    610.1 used,   1051.0 buff/cache
MiB Swap:   2048.0 total,   2000.0 free,     48.0 used.   1097.2 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                      
 803174 root      20   0  221008   2060   1940 R  25.2   0.1   2:33.68 dd                                           
 803179 root      20   0  221008   2056   1940 R  24.9   0.1   2:31.61 dd                                           
 803189 root      20   0  221008   2052   1936 R  24.9   0.1   2:30.58 dd                                           
 803184 root      20   0  221008   2060   1940 R  24.6   0.1   2:30.97 dd     
```

To understand a bit of CPU:&#x20;

```
%Cpu(s): 42.0 us, 57.7 sy,  0.0 ni,  0.0 id,  0.0 wa,  0.3 hi,  0.0 si,  0.0 st
```

* us - user space, ordinary user procs
* sy - Kernel procs (like cloning from one device to another), e.g dd command
* id - idle loop, the % that spends in doing nothing at all&#x20;
* wa - If you have a number here, it means the CPU is waiting for IO

***

### Zombies Procs :zombie:

Although not common, they are dead processes that have already finished running, but the parent procs can't tell their current state. So they hold their place in the queue. These procs do not consume any CPU load as they are dead.&#x20;

#### How do I view Zombies?&#x20;

This is how they are marked as zombies:

```
ps aux | grep defunct
```

Sometimes, you can remove these dead procs or let the system clear them by itself.&#x20;

***

Process state can be determined based on your load; when using 'top ', you can press 1 to view your CPU cores to review load in depth.&#x20;
