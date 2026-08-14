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

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

***

To put some load on the CPU, I decided to run the following command:&#x20;

```
root@rhel-serverA:~#dd if=/dev/zero of=/dev/null &
```

The command `dd if=/dev/zero of=/dev/null &` continuously reads infinite zero bytes from `[/dev/zero]` and writes them into `[/dev/null]` where they are instantly thrown away. The trailing ampersand (`&`) forces this useless data loop to run forever in the background, locking up one entire CPU core at 100% usage.&#x20;

Basically, reading nothing and writing nowhere

* Good for stress test&#x20;
* Practice viewing Procs in a Running state with htop or top

I'm going to learn a bit more with top in [monitoring-system-activity-with-top.md](monitoring-system-activity-with-top.md "mention")
