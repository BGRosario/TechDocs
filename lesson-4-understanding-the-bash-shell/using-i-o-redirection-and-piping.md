# Using I/O Redirection and Piping

There are 3 redirects in Linux&#x20;

1. Standard input (**stdin)** has a file descriptor number as 0&#x20;
2. Standard output (**stdout**) has a file descriptor number of 1&#x20;
3. Standard error (stderr) it has a file descriptor number as 2&#x20;

***

Input (**stdin**) - 0

* Input is used when feeding file contents to a file
  * E.g. cat < listings
  * mail -s "Office memo" allusers@abc.com < memoletter

Output (**stdout**) -1&#x20;

* By default, when running a command its output goes to the terminal&#x20;
* The output of a command can be routed to a file using > symbol&#x20;
  * E.g. `ls -l > listings`
  * `pwd > findpath`
* If using the same file for additional output or to append to the same file, then use >>
  * E.g. `ls -la >> listings`
  * `echo "Hello World" >> findpath`

Error (**stderr**) -2&#x20;

* When a command is executed we use a keyboard and that is also considered (stdin -0)
* That command output goes on the monitor, and that output is (stdout -1)
* If the command produced any error on the screen then it is considered (stderr -2)
  * We can use redirects to route errors from the screen
    * E.g `ls -l /root 2> errorfile`&#x20;
    * `telnet localhost 2> errorfile`

