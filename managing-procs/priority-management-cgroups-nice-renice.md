# Priority Management (Cgroups, nice, renice)

Running procs have their priority. Understanding priority management is very important

In modern Linux to work with priority and apply resource restrictions in Linux systems

* Linux [Cgroups](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/6/html/resource_management_guide/ch01) provide a framework to apply resource restrictions to Linux systems.&#x20;
* It can limit the amount of CPU cycles, available memory, and more
* If procs are equal from the perspective of Cgroups, the Linux **nice** and **renice** commands can be used to manage priority.&#x20;

***

In Cgroups, the linux system is divided into 3 slices

* System: all systemd procs
* User: all user procs
* Machine: Virtual Machines and containers

Each slice has an equal CPU weight; that means that if one or more procs within a slice request a max amount of CPU cycles, each slice will get an equal amount of CPU shares

* So 20 systemd procs together get as much as one user proc that claims full CPU usage

***

If no specific Cgroups are dfined, Linux&#x20;

* nice&#x20;
* renice&#x20;

can be used to define CPU priority. To change priorities of non-realtime processes, nice and renice can be used.&#x20;

* Priorities are relative to the current running procs.&#x20;
