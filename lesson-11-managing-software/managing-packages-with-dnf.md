# Managing Packages with dnf

**dnf** was created to be intuitive

* dnf list lists installed and available packages
  * dnf list 'selinux\*'&#x20;
* dnf search searches in name and summary. Use **dnf search all** to search in the description as well
  * dnf search all seinfo
* **dnf provides** searches in package file lists for the package that provides a specific file
  * dnf provides \*/Containerfie&#x20;
* dnf info shows information about the package

***

