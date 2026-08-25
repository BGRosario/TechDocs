# Managing Shells Jobs

Sometimes moving jobs to the background is useful if they take extremely long time&#x20;

To start a job in the background:&#x20;

```bash
command & ##to start a job in the background
```

To move a job to the background

```bash
Ctrl-Z ##To stop the job
bg ##To move it to the background
```

Use **jobs** for a complete overview of running jobs

```bash
fg [n] ##To move the last job back to the background
```

To kill the job:&#x20;

```
kill %[n] ##This will kill process ID specified
```
