# Managing Procs Priority

#### Managing nice

* To change the priorities of non-real-time processes, **nice** and **renice** can be used
* Nice values range from -20 to 19
  * Negative nice values indicate an increased priority; a positive nice value indicates decreased priority

Normal users can set nice values, but renice requires root&#x20;

Syntax:

```
nice -n [priority number] command
```

For testing purposes, you can try:&#x20;

```
nice -n 10 dd if=/dev/zero of=/dev/null
```
