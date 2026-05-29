---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Understanding memory information on Linux systems - Linux Audit

* [forensics](https://linux-audit.com/tags/forensics/)
* [guide](https://linux-audit.com/tags/guide/)
* [memory](https://linux-audit.com/tags/memory/)
* [proc](https://linux-audit.com/tags/proc/)
* [processes](https://linux-audit.com/tags/processes/)
* [procfs](https://linux-audit.com/tags/procfs/)
* [ram](https://linux-audit.com/tags/ram/)
* [swap](https://linux-audit.com/tags/swap/)
* [system administration](https://linux-audit.com/tags/system-administration/)

_This article has last been updated at March 12, 2025._

Every operating system needs memory to store program code segments and data. This is also true for Linux systems. The problem: there is a lot of information available regarding memory usage and its behavior. Let’s discover how Linux manages its memory and how we can gather memory information.

After reading this guide, you will be able to:

* Show the total amount of memory
* Display all memory details
* Understand the details listed in /proc/meminfo
* Use tools like dmesg, dmidecode, free, and vmstat

### Linux memory information

#### Random access memory

When we talk about memory in this article, we usually mean _random access memory_ ( [RAM](https://en.wikipedia.org/wiki/Random-access_memory) ). This is the memory which can be used for both showing and storing data. Typically we will find in this type of memory the programs that are running on the system, including the Linux kernel itself. Besides the program code, memory also stores a lot of data. A good example is when you are running a MySQL database server. The program itself is relatively small, the data itself is huge. So we will also have a look at tuning programs and their memory usage, as this is typically a problem with memory-hungry programs.

#### Determine the amount of RAM

The first step is to discover the amount of RAM we have in the system. There are a few ways on how to achieve this, starting from the data stored in `dmesg`.

`dmesg | grep -in mem`

The output may look something like this:

![Show memory information with the dmesg command](<.gitbook/assets/linux dmesg show memory information.png>)

This information shows the number of memory available in kilobytes. The first value shows what is currently available, the second value displays the total memory in the system. These values are usually very close. This indicates that most of the memory can be used and is a good thing. The small portion “missing” is used by the initial loading of the kernel. If there is a big gap, then this might be caused by the kernel and how many memory it can allocate. Especially with 32 bits versions of Linux, this number is limited.

#### Details and information about RAM modules

The next step is learning more about the RAM modules itself. You will need the `dmidecode` utility for this, which is available for most Linux distributions. To gather memory information, tell the _dmidecode_ to only show information for device type **17**.

`dmidecode --type 17`

Depending on your hardware it may be able to extract the specifics of your modules and show detailed information. You may need to run this as root user. Normal users won’t have the right permissions to read all information.

![Screenshot of dmidecode displaying RAM module information and details on Linux system](<.gitbook/assets/linux ram module information and details.png>)

In this output above you can see the details of the first memory module. We see it is a chip of 4 GB and configured at a 1600 MHz speed. This is a great way to determine the memory available in a Linux system, together with detailed output. Unfortunately, the command does not always play well with virtual systems.

![Empty memory information with dmidecode of hardware type 17](<.gitbook/assets/dmidecode empty memory information for type 17.png>)

_No data is displayed on our virtual test system_

Let’s move on to the next set of utilities and gather details regarding memory usage.

### Available memory

After the Linux kernel is booted, it is time to start programs. The kernel itself is not responsible for the programs. Instead, it delegates this responsibility to a service manager like _init_ or _systemd_. This process is the first to be started and will get process ID 1. Its duty is to start other services and programs during the lifetime of the system. Each program will consume some amount of memory, depending on the program size and the related data. Let’s have a look at some ways to see available memory on Linux and retrieving related details.

#### See available memory with free command

The first command to obtain available memory information is the perfectly named tool `free`.

![Free memory details on Linux](<.gitbook/assets/free memory details on linux.png>)

This utility shows two different types of memory: normal memory and swap memory. Swap is a type of memory that you want to avoid needing as much as possible. If it would be used, then it means your normal memory is full. The system will then leverage the swap memory to temporarily store data, at the cost of disk operations. As they are much slower than normal RAM, your system will be impacted. In this screenshot, we see the swap is not used, which is good.

The _free_ utility retrieves this memory information from a file named **/proc/meminfo**. Let’s have a look at that as well.

#### Details from /proc/meminfo

The next step to obtain everything available regarding memory is found in the procfs tree, usually mounted under /proc. This file is very extensive, so have a look at it on your system:

`cat /proc/meminfo`

![A partial output listing showing how memory is used from /proc/meminfo](<.gitbook/assets/linux memory information from proc meminfo.png>)

_A partial output listing showing how memory is used_

Memory management under Linux is extensive and changed over time to what it is now. This results in a delicate system that optimizes memory usage as much as possible. Let’s get into some of these fields and understand better how Linux does its job.

**Cached, SwapCached**

The system does a lot of repetition, including reading the same files or data. Everything that goes into memory and is no longer needed, will be kept for a little bit longer. If you then request the same data while it is in memory, you will get it almost instantly. This is what happens when you run a _find_ command on a particular directory the first time, which usually takes a while. Run it again and it will be much quicker.

**Active, Inactive**

A page cache optimizes access to files. These buffers can be recently used (=active), or not (=inactive).

**Active** is the total of _Active(anon)_ and _Active(file)_. Similarly, **Inactive** is the total of _Inactive(anon)_ + _Inactive(file)_.

**SwapTotal, SwapFree**

These provide insights in the configured swap memory and how much is left. Ideally, the SwapFree value is equal to SwapTotal, meaning no swap is in use at that time. Swapping is disk intensive.

**Dirty**

The Dirty field refers to data that is stored in memory and still needs to be written to the disk.

You can test this easily by writing to a temporary file and compare the value before and after.

`cat /proc/meminfo | grep Dirty && dd if=/dev/zero of=/tmp/testfile.txt bs=1M count=10 && cat /proc/meminfo | grep Dirty`

Note: if you repeat this command, you will see the effect of smart memory management. In that case, the value before and after will most likely be the same, as some data was cached and directly returned as a finished action. You can counter this by retrieving random data from [/dev/random](https://linux-audit.com/system-administration/files/dev-random/) .

**Slab, SReclaimable, SUnreclaim**

The kernel does a lot of repetition during the time it is running. Some objects, like asking for the specific inode of a file may be performed thousand times a day. In such case, it would be wise to store it in a quick reference list, or cache. **Slab** is the combination of caches for kernel objects, to optimize those activities that happen the most.

The **Slab** field is the total of _SReclaimable_ and _SUnreclaim_.

> Slab: 32272 kB
>
> SReclaimable: 18144 kB
>
> SUnreclaim: 14128 kB

**NFS\_Unstable**

For systems that use NFS this is a good measurement to see how much data is not committed to the storage yet. For systems without NFS, this value can be ignored and is usually just zero.

**More fields**

If you compared these fields with your own system, you will discover there are more fields. Depending on your workload, you will have to discover what fields make sense to monitor. What does generally work well during troubleshooting, is comparing similar systems and check for the differences in /proc/meminfo. It may give a good indication of where memory is used and what keeps the system busy.

#### Using vmstat utility

Another nice utility that is often available is [`vmstat`](https://linux-audit.com/system-administration/commands/vmstat/). With `-s` we can query memory statistics.

![Screenshot of vmstat output and details from /proc/meminfo](<.gitbook/assets/compare vmstat and proc meminfo output.png>)

We can also query the previous mentioned slabs.

![Details from vmstat about slabs](<.gitbook/assets/vmstat show slab information.png>)

### Monitoring memory usage in Linux

If you have a monitoring system in place, then two key attributes from /proc/meminfo should be monitored.

* MemFree
* SwapFree

By monitoring these two values you may discover memory leaks and badly optimized systems. You may also pick up on a misbehaving process now and then.

For environments that have many similar systems with a typical workload (e.g. lots of web servers doing the same), then it would make sense to monitor more of the keys in /proc/meminfo. Storing the data a few times per day may give you the ability to compare systems and find exceptional events.

### Frequently Asked Questions

#### How can I find out the total physical memory (RAM)?

Use the _free_ command to show the total amount of memory and how it is assigned.

What Linux tool can I use to see the details of the memory modules?

Use the `hwinfo` tool to gather details regarding the memory. If that is not available, then consider using the output from [`dmesg`](https://linux-audit.com/system-administration/commands/dmesg/).

`hwinfo --memory`

#### How can I see which processes consume the most memory?

Use the `ps` command to show memory usage and do a reverse sort.

`ps -e -orss=,args= | sort -nr | head`

#### Why are the buffer and cache use so much memory on Linux?

Linux considers unused memory to be wasted memory. So it will use as much memory as possible to speed up the performance on the system. The related caches and buffers contain typically data related to the file system. That is also why a second run of the _find_ command in the same directory runs much quicker. The kernel will reassign memory to processes when needed.

#### Where does the kernel store the details regarding virtual memory management?

Most of the related settings, like how to act during an Out-of-Memory event, will be stored in **/proc/sys/vm**.

### Conclusion

Linux memory management is an extensive subject and there is a lot to learn. Make sure to understand the basics, like how to obtain memory information, including that of RAM and swap. This is of great help during troubleshooting and to know what programs need to do their job.

Did you learn something from this article? Great! Share it on your favorite website or with others. If you have a nice tool for memory analysis or got a question, let it [know](https://linux-audit.com/contact/)!

### Relevant commands in this article

Like to learn more about the commands that were used in this article? Have a look, for some there is also a [cheat sheet](https://linux-audit.com/cheat-sheets/) available.

* cat
* [dmesg](https://linux-audit.com/system-administration/commands/dmesg/)
* [dmidecode](https://linux-audit.com/cheat-sheets/dmidecode/) cheat sheet
* free
* hwinfo
* ps
* [vmstat](https://linux-audit.com/system-administration/commands/vmstat/)

See the full list of [Linux commands](https://linux-audit.com/system-administration/commands/) for additional system administration tools.

### Feedback

![Small picture of Michael Boelen](https://linux-audit.com/authors/michael-boelen/images/michael-boelen-200x200.webp)

This article has been written by our Linux security expert Michael Boelen. With focus on creating high-quality articles and relevant examples, he wants to improve the field of Linux security. No more web full of copy-pasted blog posts.

Discovered outdated information or have a question? [Share your thoughts](https://linux-audit.com/contact/). Thanks for your contribution!

[![Mastodon icon](https://linux-audit.com/images/icons/mastodon.svg)](https://mastodon.social/@mboelen)

### Related articles

Like to learn more? Here is a list of articles within the same category or having similar tags.

* [smem](https://linux-audit.com/system-administration/commands/smem/)
* [Swap memory information](https://linux-audit.com/system-performance/memory/swap/)
* [Auditing Linux processes: The Deep Dive!](https://linux-audit.com/auditing-linux-processes/)
* [numactl: control NUMA policy for processes and shared memory](https://linux-audit.com/system-administration/commands/numactl/)
* [slabtop: showing memory slab usage for the Linux kernel](https://linux-audit.com/system-administration/commands/slabtop/)
