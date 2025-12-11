# Performing Administrator Task with sudo

Sudo is a more secure mechanism to perform administrative tasks

* Behind sudo is the /etc/sudoers configuration file&#x20;
* While editing /etc/sudoers through **visudo**, very detgailed administration privileges can be assigned
* To run an administration task using **sudo,** use **sudo** **command**
* This will prompt for the current user's password, and run the command if this is allowed through /etc/sudoers
* To open a root shell, **sudo** -i can be used&#x20;
