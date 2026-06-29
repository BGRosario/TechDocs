# Using dnf Groups

dnf group is just a collection of packages; an environment group is used to install a specific usage pattern and may consist of packages and groups

```
dnf group list  ## to see a list of groups
dnf group list hidden ## list hidden groups
dnf group info <groupname> 
dnf group install --with-optional
```



```
dnf group list   #to see a list of groups
```

* Some groups are normally only installed through environment groups and not separately, and for that reason, don't show while using dnf group list



***

### Understanding Groups

```
dnf group info <groupname> #to see packages within a group
```

* Packages are marked as mandatory, default, or optional
* While using `dnf group install` Only mandatory and default packages are installed
* To install optional packages, use:

```
dnf group install --with-optional    
```

As group names often contain spaces, the entire group name must be referred to using double quotes
