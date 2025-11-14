# Exploring History

* Bash registers recently used commands&#x20;
* Type **History** for an overview&#x20;
* Commands are kept in \~/.bash\_history to make them available beyond sessions&#x20;
* The **HISTSIZE** and **HISTFILEZIE** variables are used to define the number of entries kept in history

***

### Different ways to repeat commands

* _{Up arrow}_ key allows you to scroll backward through previous commands&#x20;
* **Ctrl-r (cmd-r if macOS)** performs a reverse search based on the pattern entered&#x20;
* **!**_**nn**_ repeats a command from the history based on its number value

```
E.g.

history 
 1169  w
 
 root@hostname:# !1169
 root@hostname:#  22:50:42 up 244 days,  7:07,  2 users,  load average: 0.00, 0.02, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     pts/0    10.0.0.1   07Nov25  0.00s  0.00s  0.00s w
```

### Managing History

* **history -w** synchronizes the current history from memory to the history file
* **history -c** clears current history, don't forget to also use **history -w** when you want to remove everything&#x20;
* **history -d&#x20;**_**nn**_ removes line _nn_ from current history
