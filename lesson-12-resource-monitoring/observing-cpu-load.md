# Observing CPU Load

CPU Loads are revised through **uptime**

```
rhel-serverA:/proc#uptime
 16:10:01 up 151 days, 15:33,  2 users,  load average: 0.00, 0.00, 0.00
```

* CPU load is expressed as the average number of runnable processes over the last 1, 5 and 15 minutes.
* As a rough guideline, this number should not exceed the number of CPU cores on a system, as the CPU loads relate to the number of cores in the system.&#x20;

***

### Linux Kernel Scheduler

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

