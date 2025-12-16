# Managing Group Membership

Each user must be a member of at least one group.

* Primary group membership is managed through /etc/passwd
* The user's primary group is crucial because it becomes the group-owner if a user creates a file
* Additional (Secondary) groups can be defined as well
* Secondary Group Membership is managed through /etc/groups
* Temporarily set primary group membership using **newgrp**&#x20;

{% hint style="info" %}
It might be nice to use this command if the primary group was added, instead of having the user log in again or all the time to have this take effect, just run newgrp \[group]&#x20;
{% endhint %}
