# Input and Output

There are 3 redirects in Linux&#x20;

1. Standard input (**stdin)** has a file descriptor number as 0&#x20;
2. Standard output (**stdout**) has a file descriptor number of 1&#x20;
3. Standard error (stderr) it has a file descriptor number as 2&#x20;



Output (**stdout**) -1&#x20;

* By default, when running a comman,d its output goes to the terminal&#x20;
* The output of a command can be routed to a file using > symbol&#x20;
  * E.g. `ls -l > listings`
  * `pwd > findpath`
* If using the same file for additional output or to append to the same file, then use >>
  * E.g. `ls -la >> listings`
  *   `echo "Hello World" >> findpath`

