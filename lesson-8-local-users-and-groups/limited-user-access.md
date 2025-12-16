# Limited User Access

An essential task for a sys admin is to limit user access when necessary. It increases security and lets you be more in control

Here are some commands that would let you achieve that.&#x20;

* User account can be temporarily locked

```bash
usermod -L anna #will lock anna

root@bgrosario-darkrai:/home# usermod -L linda
root@bgrosario-darkrai:/home# passwd -S linda
    linda LK 2025-12-13 0 99999 7 -1 (Password locked.)
    
    
usermod -U anna #will unlock anna    
```

You can also check if the user has a ! at the start of the string in/etc/skel. It would mean the user account is locked. Double !! means that the user has never entered their password. In different ways, you can add a ! in front of the : to lock it

```bash
linda:! #Locked account 
linda: #Not locked
```

* User accounts can be set to expire

```bash
usermod -e 2027-01-01 bill #Expires user account bill on 01-01-2027
```

