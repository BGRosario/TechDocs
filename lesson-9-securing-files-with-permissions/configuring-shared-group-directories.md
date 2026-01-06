# Configuring Shared Group Directories

If members of the same group need to share files within a directory, some special permissions are required&#x20;

* The Set Group ID (SGID) permission ensures that all files created in the shared group directory are group-owned by the ugroup owner of the directory
* The sticky bit permission ensures that only the user who is the owner of the file, or the directory that contains the file, is allowed to delete the file

```
chmod g+s - will apply SGID to the directory 
chmod +t mydir - assigns the sticky bit to the directory 
    
    In absolute mode, a number of 4 digits is used, of which the first digit is for special permissions
    
chmod 3770 mydir assigns SGID and sticky it, as well as rwx for user and group    
```
