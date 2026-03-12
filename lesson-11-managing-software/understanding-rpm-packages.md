# Understanding RPM Packages

Software on RHEL is installed using packages in Red Hat Package Manager (RPM) format. An RPM package contains a compressed archive and package metadata; in the metadata, package dependencies are listed. <br>

* To handle dependency management, RHEL uses repositories for package installation
* If a dependency was found, it is installed automatically from the repository
* Installed packages are registered in the RPM database

<pre><code><strong>rpm command can be used for some package management tasks
</strong>
Some commands query the RPM database
- rpm -qa shows all packages that are currently installed 
- rpm -qf filename shows from which package the filename was installed
- rpm -ql lists files installed from a package 
- rpm -q --scripts shows scripts executed while installing the package 

- rpm -q changelog shows the change log for a package
Querying package files is also possible
    - Add -p to any of the commands above
</code></pre>

***

### Extracting RPM packages

* Contents of an RPM package can be extracted to the current directory (without installing)

```
- rpm2cpio mypackage -1.0.rpm | cpio -tv - will show the contents of a package
- rpm2cpio mypackage -1.0.rpm | cpio -idmv - extracts the package contents to the curret directory
```
