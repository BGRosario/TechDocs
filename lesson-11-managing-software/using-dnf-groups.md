# Using dnf Groups

A dnf group is just a collection of packages; an environment group is used to install a specific usage pattern and may consist of packages and groups

```
dnf group list  ## to see a list of groups
dnf group list hidden ## list hidden groups
dnf group info <groupname> 
dnf group install --with-optional
```

