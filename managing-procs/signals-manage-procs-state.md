# Signals - Manage Procs State

A signal allows the OS ot interrupt a proc from software and ask it to do something&#x20;

* Interrupts are comparable to signals, but are generated from hardware&#x20;
* A limited number of signals can be used and are documented in&#x20;

```
man 7 signals
```

* Not all signals work in all cases
* The **kill** command is used to send signals to PID's&#x20;
* You can also use **k** from top

***

### Zombie Demo&#x20;

[lesson-12-monitor-procs](../lesson-12-monitor-procs/ "mention")

```
git clone https://github.com/sandervanvugt/rchsa
```

* -SIGCHILD \[ID] is what you need to kill the zombie parent; as a result, this will be adopted by the systemd procs&#x20;
