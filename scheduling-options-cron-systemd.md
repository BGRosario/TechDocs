# Scheduling Options (Cron, Systemd)

In RHEL9:&#x20;

* **systemd** timers are the primary solution for recurring jobs
* **crond** is an older scheduling solution
* **at** is available to schedule non-recurring user tasks

***

### How to use Systemd timers&#x20;

* systemd provides unit.timer files that go together with unit.service file to schedule the service file
* When using **systemd** timers, the timer should be enabled/systayed, and NOT the service unit
* **systemd** timers are often installed from RPM packages&#x20;
* In the timer unit file, the **OnCalendar** option specifies when the service should be started&#x20;
* On RHEL9,&#x20;



***

### Cron - Old Scheduling Option



* It uses **crond,** a daemon that checks its configuration to run cron jobs periodically
* Still on RHEL 9, **crond** is enabled as a **systemd** service by default
* Most services that need scheduling are scheduled through **systemd** timers&#x20;



### Using Cron

* The cron service checks its configuration every minute

```
/etc/contab
```

* Is the main (managed) configuration file

```
/etc/cron.d/
```

* is used for drop-in files

```
/etc/cron.{hourly,daily,weekly,monthly}
```

* is used as a drop-in for scripts that need to be scheduled regularly
* User-specific cron jobs can be created using **crontab -e**



### Understanding Cron Time

* Cron time specifications are specified as: **minute, hour, day of the month, month, day of the week**
* 0 \* \* dec 1-5 will run a cron job every month through Friday at minute zero in December&#x20;
* The **/etc/crontab** file has a nice syntax example

{% hint style="info" %}
Do not edit /etc/crontab; put drop-in files in /etc/cron.d instead
{% endhint %}

