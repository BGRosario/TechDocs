# Exploring Jobs and Processes

All tasks are started as processes; processes have a PID.&#x20;

* Common Process Management tasks include scheduling priority and sending signals
* Some processes are starting multiple threads, and individual threads cannot be managed
* Tasks that are started from a shell can be managed as jobs
* Shell jobs can be started in the foreground or background

{% hint style="info" %}
The key difference is that a job is tied to the user because they are tied to a shell, so the user can manage their own jobs. A proc is tied to the system, so it requires sudo privileges to manage them
{% endhint %}
