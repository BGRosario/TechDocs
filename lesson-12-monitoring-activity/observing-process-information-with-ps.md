# Observing Process Information with ps

#### Using ps&#x20;

* The **ps** command has two different dialects: BSD and System V&#x20;
  * In BSD, options do not have a leading **-**
  * In System V, options do have a leading **-**&#x20;
  * Therefore, **ps-L** and **ps L** are two completely different commands&#x20;
* **ps** shows an overview of current processes&#x20;
* Use **ps aux** for an overview of all processes

***

**ps -fax -** shows hierarchical relation between processes

```
You will see a bunch procs running, some with <?> which are kernel threats, you don't really manage them
```

* **ps -fU&#x20;**_**user**_ - shows all processes owned by a user&#x20;
* **ps -f --forest -C&#x20;**_**sshd** -_ shows a process tree for a specific process&#x20;
* **ps L** - shows format specifiers&#x20;

```
They can be use as a selecter in a command to expand the use of PS
```

* **ps -eo pid, ppid, user, cmd** - uses some of these specifiers to show a list of processes
