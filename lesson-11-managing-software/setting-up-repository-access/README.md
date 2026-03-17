# Setting Up Repository Access

A repository is a collection of RPM package files with an index that contains the repo contents&#x20;

* Repos are often offered through websites, but local repos can also be created.
* The **dnf** command is used as the default command to install packages from the repo
* In RHEL 9, **dnf** is preferred over the **yum** command, which was used in previous versions of RHEL&#x20;
* **dnf** and **yum** are offering the same functionality&#x20;

***

### Accessing Repos

To access the repo, a RHEL system must be registered using **subscription-manager**&#x20;

* **subscription-manager** tries to access the online RH repo
* **subscription-manager** tries to access the online Red Hat Repo
* As an alternative to an online repo, repos can be offered through RH Satellite
* If no Internet connection or no RHS is available, no repo will be available by default.&#x20;
* In that case, you'll have to manually configure repo access&#x20;

***

### Manual Config Repo Access&#x20;

To access repo that are offered through the subs manager, use:&#x20;

```
dnf config-manager --enable name-of-the-repo to add a repository

```

* Third-party repo can be added using a repo file in:&#x20;

```
/etc/yum.repos.d 
or 
dnf config-manager
    - dnf config-manager --add-repo="file:///repo/AppStream"
    -cat >> /etc/yum.repos.d/AppStream.repo << EOF
            >[AppStream]
            >name=AppStream
            >baseurl=file:///repo/AppStream
            >gphcheck=0
            EOF
```
