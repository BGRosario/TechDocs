# Optional Demo: Configuring the Installation Disk as Repo

{% hint style="info" %}
<mark style="color:$info;">This is not part of the exam, only practice</mark>
{% endhint %}

Review how much space you have available in /&#x20;

* df -h # You need 10G free disk space on /
* dd if=/dev/sr0 of=/rhel9.iso bs=1M
* mkdir /repo
* cp /etc/fstab /etc/fstab.bak
* echo "/rhel9.iso /repo iso9660 defaults 0 0" >> /etc/fstab
* mount -a

If you don't have 10GB of free space in /&#x20;

* mkdir /repo
* echo "/dev/sr0 /repo iso9660 defaults 0 0" >> /etc/fstab

{% hint style="info" %}
sr0 is the name of the optical drive
{% endhint %}

***

Using GPG Keys&#x20;

* To ensure that packages have not been tampered with, GPG Keys can be used
* A repo GPG key is used to sign all packages, and before installing the package, its signature is checked
* To do this, you'll need a local GPG key to be present&#x20;
* To make accessing the trusted repo easier, use the **gpgcheck=0** option in the repo client file

