# Understanding Systemd

Will be diving a little bit into what systemd is and its importance. <br>

## What is Systemd?



* [Systemd is a system and service manager for Linux Operating systems](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/chap-managing_services_with_systemd)
* It is the first process started after the kernel is loaded
  * It starts and manages all types of services you can imagine.&#x20;

***

These are a handful of units available:&#x20;

## Service Units

* Service units are used to start daemon processes

## Socket Units

* Monitor activity on a port and start the corresponding service unit when needed

## Timer Units&#x20;

* Are used to start services periodically

## Path Units&#x20;

* Can start service units when activity is detected in the file system

## Mount Units&#x20;

* Are used to mount file systems

***

