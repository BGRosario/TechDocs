# Understanding Process States

When a new process is started (forked), it is scheduled, and after being scheduled, it enters a runnable state (R) as the CPU allocates resources to run it.&#x20;

* In this state, it is waiting in the queue to be scheduled
* Runnable processes will get a time slice, which allows them to get a running state, in either kernel space or user space
* Runnable processes can get preempted or rescheduled&#x20;
  * In that case, they will return to a runnable state and wait in the queue for a new time slice
* A runnable process can be stopped (ctrl-z) and will show as **TASK\_STOPPED (**&#x54;**)**, and after being stopped, it can receive another signal to resume and return to a runnable state&#x20;

***

#### DIFFERENT STATES

While running, the process may have to wait

* This is also referred to as "blocking" state, but "blocking" is not an official state in the Linux kernel
* Waiting processes can have different flags
  * **TASK\_INTERRUPTIBLE (S)**: the process is waiting for a hardware request, system resource access, or a signal
  * **TASK\_UNITERRUPTIBLE (D)**: the process is waiting but does not respond to signals
  * **TASK\_KILLABLE (K)**: the process is waiting but may be killed&#x20;
  * **TASK\_REPORT\_IDLE (I)**: Used for Kernel threads, this process will not count for the load average

***

#### EXIT STATE&#x20;

When a process exists, it will briefly enter the **EXIT\_ZOMBIE (Z)** state. This is where it signals the parent process that it exists, and all resources except for the PID are released.

In the next stage, the process will enter the **EXIT\_DEAD (X)** state. In this state, it will be reaped, and all remaining processes will be cleaned up&#x20;

***

#### ZOMBIES

* A process becomes a Zombie when it has completed its task, but the parent process hasn't collected its execution status
* Zombies are already dead, so they can't and don't have to be killed (dead process)
* The most important disadvantage is that Zombies occupy a PID&#x20;
* To get rid of Zombie, the parent process must collect the child's execution status
  * Send **SIGCHILD** to the parent to ask the parent to reap the Zombie&#x20;
  * Kill the parent process&#x20;
  * When the parent is killed, the Zombie becomes an orphan and will be adopted by the init process
